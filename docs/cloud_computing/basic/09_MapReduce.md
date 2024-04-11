## MapReduce是什么

核心思想：分而治之

![image-20240411152809548](assets\image-20240411152809548.png)

![image-20240411152902318](assets\image-20240411152902318.png)

## 工作原理

MapReduce的编程模型借鉴了函数式编程

来自数据源的记录作为键值对输入，例如，[<文件名，行>]

‣ **map** (k, v) → [<k2, v2>] 

‣ **reduce** (k2, [v2]) → [<k3, v3>] 

所有具有相同key的值都被发送到相同的reduce，执行框架处理其他任务

其他任务：

Handles scheduling 

- assigns workers to map and reduce tasks 

- load balancing 

Handles “data distribution” 

- move processes to data 

- automatic parallelization

Handles synchronization 

- gathers, sorts, and shuffles intermediate data 

- network and disk transfer optimization 

Handles errors and faults 

- detects worker failures and restarts 

Everything happens on top of a distributed filesystem

![image-20240411153041036](assets\image-20240411153041036.png)

## 案例-WordCount

![image-20240411153123567](assets\image-20240411153123567.png)

### 伪代码

![image-20240411153145234](assets\image-20240411153145234.png)

## 工作步骤

1. 读取很多data
2. Map: (k1, v1) **→** [<k2, v2>]， 提取要处理的数据
3. shuffle and sort
4. Reduce：（k2，[v2]）→[<k3，v3>]聚合、汇总、过滤或转换
5. 输出结果

## 案例-Google Map

![image-20240411153359656](assets\image-20240411153359656.png)

![image-20240411153419085](assets\image-20240411153419085.png)

![image-20240411153436670](assets\image-20240411153436670.png)

![image-20240411153452285](assets\image-20240411153452285.png)

## Combiner&Partitioner

程序员也会指定combiner and partitioner

![image-20240411153718984](assets\image-20240411153718984.png)



Combiner and partitione

**combine** (k, [v]) → <k, v> 【对每个mapper产生的结果进行本地聚集】

- 在映射阶段之后在内存中运行的迷你reducer

- 用于减少网络流量的优化

**partition** (k, # of partitions) → partition for k 

- 划分键空间用于并行化简操作
- 通常是键的简单哈希，例如，hash(k) mod n

![image-20240411155534209](assets\image-20240411155534209.png)

![image-20240411155549622](assets\image-20240411155549622.png)



### Combine

> **Combiner作用**
>
> 1）每一个map可能会产生大量的输出，Combiner的作用就是**在map端对输出先做一次合并，以减少传输到reducer的数据量。**
>
> 2）Combiner最基本是实现本地key的归并，Combiner具有类似本地的reduce功能。
>
> 如果不用Combiner，那么，所有的结果都是reduce完成，效率会相对低下。
>
> 使用Combiner，先完成的map会在本地聚合，提升速度。
>
> 注意：Combiner的输出是Reducer的输入，如果Combiner是可插拔的，添加Combiner绝不能改变最终的计算结果。所以Combiner只应该用于那种Reduce的输入key/value与输出key/value类型完全一致，且不影响最终结果的场景。比如累加，最大值等。
>
> 注意:
>
> 不是每种作业都可以做combiner操作的，只有满足以下条件才可以：
>
> 1）combiner只应该用于那种Reduce的输入key/value与输出key/value类型完全一致，因为combine本质上就是reduce操作。
>
> 2）计算逻辑上，combine操作后不能影响计算结果，像求和，最大值就不会影响，求平均值就影响了。

### Partition

> **Partition作用**
>
> partition意思为分开，划分。**它分割map每个节点的结果，按照key分别映射给不同的reduce，也是可以自定义的。其实可以理解归类。**也可以理解为根据key或value及reduce的数量来决定当前的这对输出数据最终应该交由哪个reduce task处理。
>
> partition的作用就是把这些数据归类，将map的结果发送到相应的reduce。
>
> 每个map任务会针对输出进行分区，及对每一个reduce任务建立一个分区。划分分区由用户定义的partition函数控制，默认使用哈希函数来划分分区。
>
> partition过程如下：
>
> 1）计算(key，value)所属与的分区。
>
> 当map输出的时候，写入缓存之前，会调用partition函数，计算出数据所属的分区，并且把这个元数据存储起来。
>
> 2）把属与同一分区的数据合并在一起。
>
> 当数据达到溢出的条件时（即达到溢出比例，启动线程准备写入文件前），读取缓存中的数据和分区元数据，然后把属与同一分区的数据合并到一起。



Programmers specify: 

‣ **map** (k1, v1) → [<k2, v2>] 

‣ **combine** (k2, [v2]) → <k2, v2> 

‣ **partition** (k2, # of partitions) → partition for k2

‣ **reduce** (k2, [v2]) → [<k3, v3>] 

All values with the same key are reduced together 