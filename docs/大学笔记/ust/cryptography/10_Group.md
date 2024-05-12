## Group theory

### 什么是群

了解群之前，先了解代数结构和封闭性

#### 代数结构

把一个集合G和指定的一个或者多个运算组合到一起，表达为**(G, *,#....)**

- G是非空集合
- *, # ...是二元运算，类似加减乘除，需要两个运算数

关注的是，G里的元素用指定的二元运算会得到什么性质？

如果满足封闭性，就算一个代数结构。**代数结构必须满足封闭性，否则不是代数结构。**

#### 封闭性

什么是封闭性？**集合G中任意两个元素的运算结果还是存在集合G中。**

案例

(Z, +)，有封闭性，满足代数结构

(Z, ➗)，不封闭（结果不一定都是整数并且0不能做除数，运算不能适用所有的元素），不满足代数结构

#### 群group

在带有一个运算的**代数结构**中，有一个类型叫**群**

(G, *)是一个群，**要满足以下四个性质**

- 封闭性
- 结合律：元素的**运算顺序不影响最后结果**
- 单位元：集合里有一个元素e，它和任何元素的运算结果都还是那个元素（任何元素和0相加还是0，任何元素和1相乘还是1），就称e为单位元
- 逆元：如果集合里的每个元素，都有一个元素和他的运算结果等于单位元，这两个元素就称为互为逆元。单位元是以自身为逆元。

![image-20240511121438850](assets\image-20240511121438850.png)

案例

![image-20240511121613572](D:/Workplace/github/soni_notes/docs/大学笔记/ust/cryptography/assets/image-20240511121613572.png)

![image-20240511121654396](D:/Workplace/github/soni_notes/docs/大学笔记/ust/cryptography/assets/image-20240511121654396.png)

去掉0的有理数

![image-20240511121717042](D:/Workplace/github/soni_notes/docs/大学笔记/ust/cryptography/assets/image-20240511121717042.png)

![image-20240511121746883](D:/Workplace/github/soni_notes/docs/大学笔记/ust/cryptography/assets/image-20240511121746883.png)

![image-20240511135325305](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511135325305.png)

### 群的性质

性质



![image-20240511135357421](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511135357421.png)

阶数order：一个有限群G的阶数是G中的元素数

根据集合的元素数量，分为有限群和无限群

![image-20240511121935256](D:/Workplace/github/soni_notes/docs/大学笔记/ust/cryptography/assets/image-20240511121935256.png)

![image-20240511121951520](D:/Workplace/github/soni_notes/docs/大学笔记/ust/cryptography/assets/image-20240511121951520.png)

单位元&逆元

定理1：群里的单位元是唯一的

反证法证明：

![image-20240511122057358](D:/Workplace/github/soni_notes/docs/大学笔记/ust/cryptography/assets/image-20240511122057358.png)

![image-20240511122128322](D:/Workplace/github/soni_notes/docs/大学笔记/ust/cryptography/assets/image-20240511122128322.png)

![image-20240511122246063](D:/Workplace/github/soni_notes/docs/大学笔记/ust/cryptography/assets/image-20240511122246063.png)



![image-20240511122349500](D:/Workplace/github/soni_notes/docs/大学笔记/ust/cryptography/assets/image-20240511122349500.png)

![image-20240511122430018](D:/Workplace/github/soni_notes/docs/大学笔记/ust/cryptography/assets/image-20240511122430018.png)

![image-20240511122512012](D:/Workplace/github/soni_notes/docs/大学笔记/ust/cryptography/assets/image-20240511122512012.png)



### 什么是abelian group

如果一个群的任意两个元素运算满足**交换律**，就称为阿贝尔群

![image-20240511122618711](D:/Workplace/github/soni_notes/docs/大学笔记/ust/cryptography/assets/image-20240511122618711.png)

所以阿贝尔群要满足五个性质（和群相比，多满足一个交换律）

![image-20240511122639100](D:/Workplace/github/soni_notes/docs/大学笔记/ust/cryptography/assets/image-20240511122639100.png)



![image-20240511122700653](D:/Workplace/github/soni_notes/docs/大学笔记/ust/cryptography/assets/image-20240511122700653.png)

如果已经知道群G是一个群，如何证明是阿贝尔群？可以考虑证明它有交换律。

有一个更简单的定理：

![image-20240511123332778](D:/Workplace/github/soni_notes/docs/大学笔记/ust/cryptography/assets/image-20240511123332778.png)

![image-20240511123407243](D:/Workplace/github/soni_notes/docs/大学笔记/ust/cryptography/assets/image-20240511123407243.png)

![image-20240511123426717](D:/Workplace/github/soni_notes/docs/大学笔记/ust/cryptography/assets/image-20240511123426717.png)

![image-20240511123449574](D:/Workplace/github/soni_notes/docs/大学笔记/ust/cryptography/assets/image-20240511123449574.png)

![image-20240511123520129](D:/Workplace/github/soni_notes/docs/大学笔记/ust/cryptography/assets/image-20240511123520129.png)



![image-20240511123620450](D:/Workplace/github/soni_notes/docs/大学笔记/ust/cryptography/assets/image-20240511123620450.png)



### 群的计算

![image-20240511135641120](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511135641120.png)

![image-20240511135756252](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511135756252.png)

## Modular inverses

回顾倒数

![image-20240511140137600](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511140137600.png)

模运算下，乘法逆元是一个类似倒数的概念

可以理解为2 x 3 在mod 5下互为倒数，这里称为乘法逆元

![image-20240511140501816](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511140501816.png)

7 x 1/2 mod 5可以理解成 7 X **2的乘法逆元** mod 5

![image-20240511140638320](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511140638320.png)

案例

![image-20240511140657299](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511140657299.png)

思考：谁 x 2 mod 7 =1

可以想到4，（4 x 2） mod 7 =1，所以mod7时，2的乘法逆元是4

![image-20240511140810870](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511140810870.png)

![image-20240511140850297](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511140850297.png)

要注意是哪个模数下的乘法逆元

![image-20240511140927783](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511140927783.png)



有幂运算性质

先不看mod5进行计算，再加入mod计算

![image-20240511141028172](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511141028172.png)

![image-20240511141114564](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511141114564.png)

称呼为乘法逆元的两个整数通常只考虑比模数小的

![image-20240511141146901](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511141146901.png)

彼此唯一

![image-20240511141216526](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511141216526.png)

一个整数和模数互素，才存在乘法逆元





## Multiplicative Inverses

![image-20240511141427419](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511141427419.png)

是唯一

![image-20240511141444796](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511141444796.png)

## 费马小定理Fermat's Little Theorem

![image-20240511111455890](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511111455890.png)

![image-20240511104505605](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511104505605.png)

≡ 同余符号

这个意思是，a的p次方和a mod p的结果同余 ，这里a不能是p的倍数

![image-20240511104559736](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511104559736.png)

![image-20240511104707983](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511104707983.png)

用法

![image-20240511104822854](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511104822854.png)



## Corollary

TODO

![image-20240511141606602](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511141606602.png)

![image-20240511141636720](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511141636720.png)

![image-20240511141646870](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511141646870.png)

## **作业Repeated Squaring**

![image-20240511141735953](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511141735953.png)

![image-20240511115109658](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511115109658.png)

![image-20240511115143972](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511115143972.png)

## Factoring

乘法两个数字很容易；分解一个数字是很困难的

最难考虑的数字是两个等长的素数的乘积

**Generating primes**

生成（随机）n位素数

- Choose uniform n-bit integer p
- 如果p为素数，则输出它；否则，重复

但是这样效率低

为了提高效率，需要两件事：

- 质数应该足够密集：一个均匀的n位整数是素数的概率应该足够大
- 需要一种有效的方法来测试质数

**Distribution of primes**

我们知道质数是足够密集的

![image-20240511141916991](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511141916991.png)

所以需要生成素数的算法

有一些有效的（随机）算法来生成（随机）素数——这些算法可能会失败，但其概率可以忽略不计

## RSA

The factoring problem is not *directly* useful for cryptography, Instead, introduce a problem related to factoring: the *RSA problem*

N=pq with p和q是不同的素数

![image-20240511142057258](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511142057258.png)

![image-20240511115721571](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511115721571.png)

![image-20240511142140192](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511142140192.png)

![image-20240511142150321](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511142150321.png)

## RSA and factoring

![image-20240511142207320](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511142207320.png)

## Cyclic groups

设G是一个m阶的有限组（用乘法表示），设g是G的某个元素

![image-20240511142348508](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511142348508.png)

![image-20240511133924020](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511133924020.png)

循环群

群里的所有元素都可以由g生成

![image-20240511133956155](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511133956155.png)

![image-20240511134106302](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511134106302.png)

用2可以产生群里的所有元素

![image-20240511142439411](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511142439411.png)

![image-20240511142812628](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511142812628.png)

![image-20240511142821127](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511142821127.png)

**性质**

![image-20240511134134303](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511134134303.png)

一个循环群可能有很多生成元

循环群是特殊类型的阿贝尔群

![image-20240511134227808](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511134227808.png)

![image-20240511134256612](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511134256612.png)

![image-20240511134307207](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511134307207.png)

性质

![image-20240511142910491](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511142910491.png)

## Discrete-logarithm (dlog) problem

TODO

Fix cyclic group G of order q, and generator g

![image-20240511150014774](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511150014774.png)



![image-20240511150711971](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511150711971.png)

## Diffie-Hellman 密钥交换算法

DH算法是一个密钥交换算法，不像对称算法那样对数据加密

实际应用中，公钥密码和对称密码经常结合使用，加解密使用对称密码技术，密码管理使用公钥密码技术

使得通信的双方在安全的信道中安全地交换密钥，用于加密后续的通信消息



算法流程

![image-20240511151951650](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511151951650.png)

![image-20240511152418527](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511152418527.png)

先选取一个大素数P和a的本源根（生成元）

除此之外，用户a选择一个保密的随机数Xa，用户b选择一个保密的随机数Xb

分别计算Ya和Yb

然后互发给对方

然后AB分别计算K，得到的结果应该是一样的

这里如果有攻击者，可以到的消息有a, P, 可以截获Ya, Yb，但是难以求k，这就是离散对数的困难

为什么K计算相等

![image-20240511152223013](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511152223013.png)

例题

![image-20240511152341423](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511152341423.png)



**补充：**

本源根可以理解为生成元，什么是生成元？![image-20240511151340289](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511151340289.png)
如果某个元素 mod 1-N-1的结果没有重复，就是一个生成元

![image-20240511151517378](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511151517378.png)

## Group selection

离散对数问题在所有组中都不难

然而，有某些群的问题被认为是困难的——所有相同阶的循环群都是同构的，但是群的表示很重要







## Reference

[1] https://www.zhihu.com/tardis/bd/ans/127659716?source_id=1001