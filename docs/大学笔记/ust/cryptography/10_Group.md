## Group theory

### 定义

[简单来说，一个集合和一个二元运算，并且满足群论四大公理。](https://www.zhihu.com/tardis/bd/ans/127659716?source_id=1001)

数学运算中，有种特殊的**集合+运算**就是群。

什么是群？简单来说，就是描述对称。

对称就是：**“某种操作下的不变性”**，关键字是两个：**“操作”和“不变性”**

群只关心对称最本质、最抽象的性质。所以我们只关心操作，只需要把操作放到集合里。要放进去我们必须要把操作给数学化，也就是符号化，我们起码有两种符号化的选择，类比于加法或者乘法：

群的定义

![image-20240511112355153](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511112355153.png)

![image-20240511112453358](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511112453358.png)



![image-20240511104328471](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511104328471.png)



![image-20240511111340628](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511111340628.png)

### 计算





## Multiplicative Inverses

TODO



## 费马小定理Fermat's Little Theorem

![image-20240511111455890](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511111455890.png)

![image-20240511104505605](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511104505605.png)

≡ 同余符号

这个意思是，a的p次方和a mod p的结果同余 ，这里a不能是p的倍数

![image-20240511104559736](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511104559736.png)

![image-20240511104707983](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511104707983.png)

用法

![image-20240511104822854](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511104822854.png)

## **作业Repeated Squaring**

![image-20240511115109658](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511115109658.png)

![image-20240511115143972](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511115143972.png)

## Factoring

![image-20240511115211002](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511115211002.png)

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





## RSA

The factoring problem is not *directly* useful for cryptography, Instead, introduce a problem related to factoring: the *RSA problem*



![image-20240511115721571](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511115721571.png)



## RSA and factoring



## Cyclic groups

### 数学基础



### 算法和协议





## Diffie-Hellman



Group selection

## Reference

[1] https://www.zhihu.com/tardis/bd/ans/127659716?source_id=1001