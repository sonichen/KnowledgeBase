---
title: 17-Sampling Distribution Models
updated: 2024-01-29T12:12:24.0000000+08:00
created: 2021-05-03T23:03:18.0000000+08:00
---

同一个调查，不同时期进行得出的概率不一样

## 17.1 Sampling Distribution of aProportion
背景：对一同一个实验，多次得出的概率分布如下
![image1](../../assets/06b75722d476441aa948f44a391ea0a2.png)

1，It is called the sampling distribution of the proportions

The histogram is unimodal, symmetric, and centered at p.
样本统计量随样本变化的抽样分布模型使我们能够量化这种变化，并说明我们认为相应的种群参数在哪里
注意：
![image2](../../assets/3a368088bb764199820ddf294b01b562.png)
案例

2，Which Normal?
To use a Normal model, we need to specify two parameters: its mean and standard deviation.
The center of the histogram is naturally at p, so that’s what we’ll use for the mean of
the Normal model.

![image3](../../assets/2948f094b1744d6297ba76c4cdb0b4e4.png)
因为我们有一个正态模型，所以我们可以使用68-95-99.7规则，或使用表或技术查找精确的概率。例如，我们知道95%的正态分布值大约在平均值的两个标准差范围内，因此，如果各种可能问同一问题的民调报告了不同的结果，我们不应该感到惊讶。

Such sample-to-sample variation is sometimes called **sampling error**. It’s **not really an error at al**l, but just variability you’d expect to see from one sample to another.
Abetter term would be **sampling variability**.

## 17.2 When Does the Normal Model Work? Assumptions and Conditions

![image4](../../assets/9e30c09c204b44f59aa9dc4fa689a2e5.png)

满足一下条件
**The Independence Assumption**：
样本中的个体（我们发现的比例）必须相互独立；

如果你的数据来自一个实验，其中受试者被随机分配到治疗中，或来自基于一个简单的随机样本的调查，那么这些数据就满足随机化条件Randomization Condition.
**10% Condition:**
抽样过多的人口也可能是一个问题。一旦你抽样了超过10%的人口，剩下的个体就不再真正独立。

**Success/Failure Condition:**
You should have at least 10 successes and 10 failures in your data。np和nq都必须\>=10

![image5](../../assets/3bb4c4875bea405686f363d8c2e08ec2.png)

案例
![image6](../../assets/cdd46ea73e7e498aa0c48ae8d9f9dea9.png)

![image7](../../assets/1415158ae96c4b6b97f84ec095001c5c.png)

## 17.3 The Sampling Distribution of Other Statistics

术语：skewed to the right，

Simulating the Sampling Distribution of a Mean

## 17.4 The Central Limit Theorem: The Fundamental Theorem ofStatistics
中心极限定理告诉我们，当样本量足够大时，样本均值的分布慢慢变成正态分布，就像这个图：
![image8](../../assets/df65ccc2f78c4fd58133f00eecd28487.png)
1，Laplace’s result is called the Central Limit Theorem13 (CLT).

随着样本量的增长，重复随机样本的均值分布不仅越来越接近正态模型，而且无论种群分布的形状如何，这都是如此！即使我们从偏态或双峰种群中提取样本，
中心极限定理也告诉我们，随着样本量的增长，重复随机样本的方法将倾向于遵循正态模型

![image9](../../assets/5c0766873ca240ac87bb79a3153eca1b.png)

中心极限定理(CLT)随机样本的均值是一个抽样分布可以近似的随机变量,

2，Assumptions and Conditions
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Independence Assumption:</p>
<blockquote>
<p>样本量n不应超过总人口的10%。</p>
</blockquote>
<p>Sample Size Condition:</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

3，Which normal
![image10](../../assets/310e0f17f7744a859182d26ff2b16869.png)

![image11](../../assets/494f0a31d5e34fb896724e609ce8d548.png)
区别：重点
![image12](../../assets/fb0c702e6d064b119a8fce9f6f75355d.png)

![image13](../../assets/1e969d3faaff46c580921ed74efbd1bf.png)

![image14](../../assets/e6693ff6001e43929651524bf1712c60.png)

## 17.5 Sampling Distributions: A Summary
![image15](../../assets/9316b0b2de0c4d508f38d130603a7b33.png)

![image16](../../assets/2d927f22fc5f4fd08906f4a4eb1f5b0f.png)

