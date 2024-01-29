---
title: 24-Comparing Counts
updated: 2024-01-29T12:17:59.0000000+08:00
created: 2021-06-08T19:45:16.0000000+08:00
---

背景：你最喜欢的颜色和你接受过的多少教育有关吗？一项调查发现，与受过高等教育的成年人相比，只有受过高中教育的成年人中说红色的比例也较低。这可能只是随机波动，还是不同教育水平的颜色偏好分布不同？我们在第二章中看到了计数和百分比表。在本章中，我们将了解如何测试我们在这些表中看到的模式的强度。
![image1](../../assets/090e49dc146b4ea8bf6adcb75b37fee5.png)

## 24.1 Goodness-of-Fit Tests
准备工作
**1，本章只有假设**
![image2](../../assets/bdbb9493d79b43ad86b6fa96f9e622f0.png)

A hypothesis test to address this question is called a test of “**goodness-of-fit.**”
没有单一的参数可以估计，所以置信区间没有多大意义。

**2，Assumptions and Conditions**
| Counted Data Condition  | check to be sure the values in each cell really are counts. |
|-------------------------|-------------------------------------------------------------|
| Independence Assumption | a random sample from the population ofinterest.            |
| Sample Size Assumption  | At least 5 individuals in each cell.                        |

案例
![image3](../../assets/b53f01c7daca43f095aeea7a224cba2e.png)

**3，Calculations**
这些观察到的和预期计数之间的差异，表示（Obs-Exp）。
![image4](../../assets/d8a466eee8e540d8b0e3af7b7825689b.png)

**4，Chi-Square P-Values**
计数表的卡方统计量**仅用于测试假设，而不适用于构造置信区间**。如果观察到的计数与预期的不匹配，则统计数据将会很大。它不能“太小”。“这就意味着我们的模型真的非常适合数据。所以卡方测试总是是片面的。如果计算出的统计值足够大，我们将拒绝零假设。
![image5](../../assets/0d21aebfe6a8436f805a39c3d3f7915e.png)

第一类
## The Chi-Square Calculation
![image6](../../assets/1f1992c68fd5420f9e17442a222f5b37.png)
解题步骤
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>1，做假设：一个相同，一个不相同</p>
<p>2，检查条件</p>
<p>3，求df=n-1</p>
<p>4，求X2</p>
<p>![image7](../../assets/ba1d2a2221884733b16c3e5c9ead3a50.png)</p>
<p>5，查表得P值</p>
<p>6，得出结论</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

补充：计算过程
![image8](../../assets/28bd17d0899a46c4a205d67c63e18771.png)
案例
![image9](../../assets/2a71b02c324b4365b856fbb766f8eb2d.png)

案例
我们有12生肖中的256名高管。自然的零假设是，高管的出生日期在所有十二宫中平均分配。测试统计量观察观测数据与这种理想化情况的匹配程度
![image10](../../assets/32f12fbc2cb543aea94711f94614e012.png)

The Trouble with Goodness-of-Fit Tests: What’s the Alternative?

拟合优度检验的唯一零假设是该理论是正确的。

## 24.2 Chi-Square Test of Homogeneity
**查看是否均匀分布**
背景：许多大学对毕业班进行调查，以确定毕业生的计划。我们可能会想知道，大学里不同学院的学生的计划是否一样。
这是一张针对来自一所大学几所学院的2011届毕业生的双向表格。表格中的每个单元格都显示了有多少来自特定大学的学生做出了某种选择。
![image11](../../assets/5bf6637a84954486a00d7d54823d19bf.png)
预期
![image12](../../assets/14b7991418df40aa9bfbeb4587b82142.png)

我们已经知道如何测试两个比例是否相同。例如，我们可以使用两比例的z测试来看看学生选择研究生院的比例对农业专业的学生和工程专业的学生是否相同。但现在我们有**两个多组**。我们想测试所有四所学院的学生的选择是否相同。
The z-test for two proportions generalizes to a chi-square test of
homogeneity

检查条件
![image13](../../assets/6a33e807344247cab425865785f91cf9.png)
计算
注：自由度
![image14](../../assets/fe9cfd001b174ed5bc7dd4dd1e2e09dc.png)
自由度的作用是？
步骤
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>1，做假设</p>
<p>2，检查条件</p>
<p>3，计算df: (R - 1)(C - 1)</p>
<p>4，列出table【预期与实际的对比】</p>
<p>5，计算X2（根据表格）</p>
<p>![image15](../../assets/46008c129e0647528e13abf6ad1ef605.png)</p>
<p>6，计算P值</p>
<p>7，结论</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

案例

![image16](../../assets/b9a405bb59a2458e85a082065351ed19.png)

24.3 Examining the Residuals【没认真看】
To standardize a cell’s residual, we just divide by the square root of its expected value:
![image17](../../assets/b6ff91b6aeab42368e1de509f2d51845.png)

![image18](../../assets/b6fb2a9154204bd4be6a8d783e12cace.png)

## 24.4 Chi-Square Test of Independence
**查看是否独立**
背景：德克萨斯大学西南医学中心的一项研究检查了626名接受非血液相关疾病治疗的人，
以确定丙型肝炎的风险是否与人们是否有纹身以及纹身有关。在美国，丙型肝炎每年约1万人死亡，但感染后多年未被发现
![image19](../../assets/95354b3d01e34b5c893f6ab31bd96fa4.png)

这些数据不同于本章之前考虑的数据类型，因为它们将单个组的对象分类为两个分类变量，而不是只有一个变量。

这里的分类变量是丙型肝炎状态（“丙型肝炎”或“无丙型肝炎”）和纹身状态（“客厅”、“其他地方”、“无”）。我们在第2章中看到了由两个分类变量分类的计数，所以我们知道这样的表被称为contingency tables

Contingency tables对两个（或多个）变量上的计数进行分类，以便我们可以查看一个变量上的计数分布是否取决于另一个变量。

询问这些数据的自然问题是，患丙型肝炎的几率是否与纹身状况无关。记住，如果事件A和B为独立事件，P(A)必须等于P(AB)。在这里，这意味着一个随机选择的患者患有丙型肝炎的概率应该是一样的，无论患者的纹身状态如何。

When we ask whether two variables measured on the same population are independent we’re performing a
chi-square test of independence.

检查条件
![image20](../../assets/d550b7305f6340909b67cd9232a94a35.png)

计算
步骤
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>1,做假设</p>
<p>2，检查条件</p>
<p>3，得df=（R-1）（C-1）</p>
<p>4，列出表格（分类）</p>
<p>5，计算X2</p>
<p>6，计算P值</p>
<p>7，结论</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

案例

![image21](../../assets/1400376eb3aa48cdb9665798b8a1133a.png)

![image22](../../assets/6391679e253e4f2cb7a4222804866b3d.png)
案例

![image23](../../assets/eaee8a903aaf4779895343325e8716cb.png)

Examine the Residuals【还没看】

Chi-Square and Causation【还没看】

总结
![image24](../../assets/ad37707bd27c4144b14c9b623f6aa1eb.png)
![image25](../../assets/245607af639641fba0e3ee0dc726c06b.png)
