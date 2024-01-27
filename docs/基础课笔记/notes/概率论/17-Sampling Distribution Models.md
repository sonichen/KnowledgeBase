---
title: 17-Sampling Distribution Models
updated: 2021-05-06T20:39:09.0000000+08:00
created: 2021-05-03T23:03:18.0000000+08:00
---

同一个调查，不同时期进行得出的概率不一样

## 17.1 Sampling Distribution of aProportion
背景：对一同一个实验，多次得出的概率分布如下
![image1](../../assets/bbe4b3543cf744809a186a2ecf40da0a.png)

1，It is called the sampling distribution of the proportions

The histogram is unimodal, symmetric, and centered at p.
样本统计量随样本变化的抽样分布模型使我们能够量化这种变化，并说明我们认为相应的种群参数在哪里
注意：
![image2](../../assets/a52e8569807b4920939427d954402241.png)
案例

2，Which Normal?
To use a Normal model, we need to specify two parameters: its mean and standard deviation.
The center of the histogram is naturally at p, so that’s what we’ll use for the mean of
the Normal model.
<table>
<colgroup>
<col style="width: 49%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image3](../../assets/9c278fd66339423ba544f6a7e92cc6c7.png)</p>
<p>![image4](../../assets/93b3099dc09b4987869c6ffca1fac01e.png)</p>
<p></p></th>
<th><p>![image5](../../assets/de07171360644e8d9d8104015889ee2f.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

因为我们有一个正态模型，所以我们可以使用68-95-99.7规则，或使用表或技术查找精确的概率。例如，我们知道95%的正态分布值大约在平均值的两个标准差范围内，因此，如果各种可能问同一问题的民调报告了不同的结果，我们不应该感到惊讶。

Such sample-to-sample variation is sometimes called **sampling error**. It’s **not really an error at al**l, but just variability you’d expect to see from one sample to another.
Abetter term would be **sampling variability**.

## 17.2 When Does the Normal Model Work? Assumptions and Conditions

![image6](../../assets/557fd1e7703d425eaaed0f57ef451b92.png)

满足一下条件
**The Independence Assumption**：
样本中的个体（我们发现的比例）必须相互独立；

如果你的数据来自一个实验，其中受试者被随机分配到治疗中，或来自基于一个简单的随机样本的调查，那么这些数据就满足随机化条件Randomization Condition.
**10% Condition:**
抽样过多的人口也可能是一个问题。一旦你抽样了超过10%的人口，剩下的个体就不再真正独立。

**Success/Failure Condition:**
You should have at least 10 successes and 10 failures in your data。np和nq都必须\>=10

![image7](../../assets/f41c4632ee66417b981489cec9abf559.png)

案例
<table>
<colgroup>
<col style="width: 13%" />
<col style="width: 86%" />
</colgroup>
<thead>
<tr class="header">
<th>美国疾病控制和预防中心报告说，美国22%的18岁女性的体重指数(BMI)为30岁或以上——国家心肺和血液研究所认为这一值与健康风险的增加有关。作为一所大型大学例行健康检查的一部分，体育系通常要求学生进来进行测量和称重。今年，该部决定尝试一个自我报告系统。它要求<u>200名</u>随机挑选的女性学生报告她们的身高和体重(可以从中计算出她们的BMIs)。这些学生中只有31名的英中率大于30分。</th>
<th><p>![image8](../../assets/6d6f86e9d84b486e8ae6f1f6fb073ab3.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 49%" />
</colgroup>
<thead>
<tr class="header">
<th>假设大约13%的人口是左撇子。有200个座位的学校礼堂有15个“左撇子”座位，座位的内置桌子在左边而不是右臂。在一个90名学生的班级上，左手学生没有足够座位的可能性有多大？</th>
<th><p></p>
<p></p>
<p></p>
<p></p>
<p></p>
<p></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>![image9](../../assets/6e2ccbb2dd8647f0b2a3490e4ec566f9.png)</p>
<p></p></td>
<td><p>![image10](../../assets/913df7f6f4b24b2c92878e9c17e5550c.png)</p>
<p></p></td>
</tr>
</tbody>
</table>

## 17.3 The Sampling Distribution of Other Statistics

术语：skewed to the right，

Simulating the Sampling Distribution of a Mean

## 17.4 The Central Limit Theorem: The Fundamental Theorem ofStatistics
中心极限定理告诉我们，当样本量足够大时，样本均值的分布慢慢变成正态分布，就像这个图：
![image11](../../assets/10567b6f439e4be3a9982f91cefe73ee.png)
1，Laplace’s result is called the Central Limit Theorem13 (CLT).

随着样本量的增长，重复随机样本的均值分布不仅越来越接近正态模型，而且无论种群分布的形状如何，这都是如此！即使我们从偏态或双峰种群中提取样本，
中心极限定理也告诉我们，随着样本量的增长，重复随机样本的方法将倾向于遵循正态模型

![image12](../../assets/44e129fd3dac4cfe8313d182d2259b62.png)

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
![image13](../../assets/1cfc0f4c8d244a699e60e286f5a94dd9.png)

![image14](../../assets/d8bd453314be45bba5577ecd2541d5b2.png)
区别：重点
![image15](../../assets/afbe95be89404ac9be77e69a7644b468.png)

![image16](../../assets/1b79794590394ff6a3b1a71c8be2e5d5.png)

![image17](../../assets/dfe3c4e819f24a4b8b867669fc080f15.png)

## 17.5 Sampling Distributions: A Summary
![image18](../../assets/bcc07fa765714244bedc0945c3077e5d.png)

![image19](../../assets/daf75b0ab5a64ae68bcacaade6f4bd8b.png)

