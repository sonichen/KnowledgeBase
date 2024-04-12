# MapReduce 算法设计

## MapReduce是什么

- 一种编程模式
- 主要思想：分而治之
  - map: 拆解，将大问题分为很多小问题，在各个worker执行
  - reduce：组合，汇总所有的结果，所有的Map阶段产出的结果进行汇

> 使用它编程解决实际问题时，他只要编写一个Mapper 函数和一个Reduce 函数，或许在复杂一点加上一个Combiner 函数和Partitioner 函数，其余的就直接交给MapReduce框架执行。这样程序员就只要关注数据业务，而不用关注具体的执行过程。



MapReduce在具体执行过程中，同步化是一个非常棘手的问题。在MapReduce的并行执行过程唯一发生集群级同步化是在 Shuffle 和Sort阶段，即在Mapper阶段完成后，将各个节点上的中间结果Key/Value 依据Key的值聚集后复制到Reducer节点上。除此之外的过程，各个节点都是独立运行的而且没有直接的通信。这就意味着程序员对MapReduce的执行过程的很多方面都没有控制能力，比如：

1. 集群中哪个节点来执行Mapper 和Reducer 。
2. 什么时候开始和结束Mapper 和Reducer。
3. 输入的key/value 由哪个Mapper 来处理。
4. 中间结果产生的key/value 由哪个Reucer来处理。

从另一个角度来说，程序员可以控制以下的几个方面：

1. 数据结构的自定义，即key/value的具体的结构可以是程序员自定义的。
2. MapReude 每个Mapper 和Reducer 的执行过程在开始和结束都可以有一段程序自定义代码，来确定每个Mapper 和Reducer 在执行之前和结束后的动作。比如Hadoop在实现MapReude框架时，每个Mapper 和Reducer 都有一个setup 和cleanup 函数，既是定义开始和结束的动作。在一些MapReduce优化算法中会充分利用这两个函数。
3. 对MapRuduce的Mapper 的输入Key 和Reducer 的中间结果Key 状态的控制。
4. 对中间结果Key 排序的控制，这样程序员就有能力控制Reducer 处理Key的顺序。
5. 对中间结果Key 分区的控制，这样程序员就有能力控制Reducer 处理Key的集合。

## 1.local aggregation

可以减少中间结果的产生，从而能提高MapReduce 的效率(特别是对于一个Mapper 可能产生多个相同的Key)。

### 1.1 Combiner 和 in-Mapper Combining

Combiner: MapReduce 实现中都会提供的

作用：对每个Mapper产生的结果进行本地聚集

我们知道在MapReducer 的输入实现过程是大致这样的：一个大的作业文件会通过MapReduce提供的Splitter 来进行切割成多个小的文件，每个文件会被一个Mapper处理，而每个小文件又会被MapReduce提供的RecordReader进行分割形成很多的key/value 形式的记录，每个Mapper对象中的map 方法会对每条key/value 的记录进行处理。处理后会形成一个新的Key/value 的中间结果，会序列化写到本地磁盘。

举个常见的例子来说：数单词。假设现在有100 篇的文集，要数出每个单词出现的次数。MapRudce 接到这个任务后，首先检测文集数据的正确性。然后进行分割(这里我们采用逻辑上的分割)。比如集群有10 个TaskTracker可用。MapReduce 将100文档进行平均分割，每个TaskTracker会得到10篇文集。若每个TaskTracker运行一个Mapper的话，这10篇文集会一次被Mapper 处理。10篇文集又会被分切成10个RecordReader形式的Key/Value(key=docId,value=docContent)。这样一个Mapper 一次就会处理一片文档。具体算法伪码如下：

![image-20240411110226515](assets\image-20240411110226515.png)

首先，我们来讨论Combiner的使用。上述算法只使用了Mapper 和Reducer ，并没有使用Combiner ，这个算法的中间结果都是(term t; count 1) 的形式。即每个单词记录一次，这样的中间结果会很多。我们在下面改进的算法中使用Combiner 。

![image-20240411110403152](assets\image-20240411110403152.png)

从改进算法的伪码中我们可以看出，我们只是在Mapper中的map方法中添加一个关联数组(即JAVA中的Map)。每次map 处理一个文档时，并不是遇到一个单词就写到本地磁盘，而是将其添加到关联数组中，并且关联数组的值加1。在所有单词处理完后，在使用一个for循环将所有的单词及其出现在该文档中的次数写回本地磁盘。这样每个Mapper 的输出就是一个Map方法处理一篇文集中的单词及其出现在该文档中的次数。比如在处理docId =“16”的时候，单词“link”在这个文集中出现了5次。在没有使用Combiner的情况下，会有5个中间结果写回磁盘即(link;1), (link;1), (link;1), (link;1), (link;1)。而在使用Combiner 的情况下对于单词“link”只会有一个中间结果(link;5)写回磁盘。从中可以看出Combiner可以减少中间结果的数量。

这个的Combiner只是对本地Map方法产生的结果进行汇总。其作用相当于一个“mini-Reducer”。而事实上在Hadoop的MapReduce的实现中，其Combiner就是实现一个Reducer。

上述的算法相比没有Combiner 的算法有了很大的提高，实际上该算法还有提升的空间。这就是接下来要讲的“In-Mapper Combining”。

Combiner 的使用可以使得每个Mapper 的map 方法产生的结果本地聚集。实际上更为有效是，我们可以让每个Mapper 的结果本地聚集。上面数单词的例子中，每个Mapper 会处理10 文档，而Mapper中的map方法会每次处理1个文档，map会循环10遍。我们可以直接将 10个文档的单词进行本地聚集。

下面是使用 “In-Mapper Combining”的算法伪码实现：

![image-20240411110447766](assets\image-20240411110447766.png)

从上面使用“In-Mapper Combining”的伪码中可以看出，Mapper中的不只是有map 一个方法，而是增加了Initialize 和Close 方法。即我们之前说的每个Mapper执行过程中在开始和结束都可以有一段程序自定义代码，来确定每个Mapper 和Reducer 在执行之前和结束后的动作。这里对应Hadoop 中的方法是：setup 和 cleanup 方法。

下面对该算法分析：在每个Mapper 启动的时候会有一个关联数组的产生。在执行每个Map方法执行完时，并不直接写回磁盘，而是将单词加入到关联数组中，在整个Mapper执行完后才将所有单词写回磁盘(Close方法完成)。对应数单词的例子来说，每个Mapper不是在每篇文档处理完后写回磁盘的，而是每个Spiltter 的10篇文档处理完后，才一次性写回磁盘。这样中间结果相比直接使用Combiner就更少。

### 1.2 Combiner 和 in-Mapper Combining的优缺点

In-Mapper Combining 虽然比Combiner 有更少的中间结果。但是它有几个缺点。

- 破坏了MapReduce 编程模式的基础，因为保存中间结果跨越了多个Key/Value。如果说为了效率，我们不刻意的去追求模式。但是对于一些特定的算法它是不合适使用
- In-Mapper Combining 对拓展性提出了挑战。以数单词为例，假设Mapper处理的10篇文档很大设计到很多的单词，这样关联数组势必会非常大，又可能大到一个JVM不能完全存储这个关联数组。这样拓展性会遇到挑战。





##  Pairs 和 Stripes

这两种设计模式并没有利用MapReduce 的框架机制，而是巧妙的利用数据结构来实现的。但是依然可以利用我们之前提到的Combiner 和In-Mapper Combining 来进行效率优化。



 在日常应用中，我们通常想要从大数据集中挖掘出一些有用的关联模式。比如大型零售机构想要从他们的销售记录中挖掘出一些关联销售(比如用户购买了A产品，很大可能性上会买B产品)。这样的挖掘是非常有用的，比如在货物架上摆放时可以将A和B放在一起或者将A和B进行捆绑销售。而接下来要讨论的Pairs 和Stripes 对这种关联模式的挖掘是非常有效的。

为了更加简单的描述算法，我们这里用单词共现矩阵作为例子来讲述。很显然单词共现算法的空间复杂度为O(n2)。这里的n即为所有文集中单词出现的个数。对于大文集或者是互联网规模的数据来说，这个n无疑是非常大的。以至于大到无法在单机上运行，使用MapReduce 并行处理无疑是在恰当不过了。

首先我们来看下单词共现的Pair 的算法伪码：

![image-20240411110754413](assets\image-20240411110754413.png)

从上面的算法可以看出，这里求文集中的单词共现并没有利用MapReduce 本身的机制，而是通过设计良好的数据结构来完成的。

我们在来看下单词共现的Pair 的算法伪码

![image-20240411110821721](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cloud_compute\assets\image-20240411110821721.png)

### 2.1 Pairs 和 Stripes 分析比较

从上面Pairs 和 Stripes 的伪码可以看出，它们都实现了单词共现的需求，但是实现方法有所不同。

举个例子：假设现在篇文档的Id =“001”文档的内容为Content=“big data analytics is important”。(这里我们不考虑单词共现的先后关系)。

Pairs 的Mapper阶段产生的数据如下：![image-20240411110850024](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cloud_compute\assets\image-20240411110850024.png)

而Stripes的Mapper阶段产生的数据如下：

![image-20240411110903228](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cloud_compute\assets\image-20240411110903228.png)

从上面两个算法产生的中间数据来看：Pairs 和 Stripes 各有优缺点：

(1) Pairs 和Stripes 相比会有更多的中间结果产生，就上面的例子来说Pairs 的Mapper阶段产生的中间Key/Value 就有10个，而Stripes 的中间结果只有4个。若有之前讲的[Combiner 和In-Mapper Combining ](http://www.cnblogs.com/koalaer/archive/2012/04/16/MapReduce_Combiner.html)来优化中间结果，Stripes的优化效率比Paris会高很多的。因为Paris 的Key更加复杂。优化的效率会更低。

(2) 但是从可拓展性上来说，Pairs 比Stripes 有更高的拓展性，因为Paris 产生的Key/Value 的大小总是很小的，所以Paris几乎不存在拓展性问题。但是对于Stripes就不同了。Stripes 产生的Key/Value 的大小依据整个文集的大小。当文集很大时，一个Key/Value 的Value就会非常的大，有可能一个Mapper无法处理。这样拓展性能问题就显而易见了。