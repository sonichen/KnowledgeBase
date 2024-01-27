---
title: 15-Random Variables
updated: 2021-07-02T20:53:14.0000000+08:00
created: 2021-05-02T11:23:40.0000000+08:00
---

一种随机变量来建模结果的概率。使用随机变量可以帮助我们谈论和预测随机行为。

## 15.1 Center: The Expected Value

1，术语
<table>
<colgroup>
<col style="width: 38%" />
<col style="width: 61%" />
</colgroup>
<thead>
<tr class="header">
<th>random variable</th>
<th>随机变量，用X表示</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>a discrete random variable.</td>
<td><p>离散型随机变量</p>
<p>可以单独列出来，用x表示所有可能的值及其发生的概率的集合被称为离散随机变量的概率模型</p></td>
</tr>
<tr class="even">
<td><p>a continuous</p>
<p>random variable.</p></td>
<td>连续性随机变量</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
</tr>
</tbody>
</table>

案例，保险公司
例如，假设任何一年的死亡率是每1000人中就有1人，而1000人中又有2人患有某种残疾。然后我们可以在这样的表格中显示此保险单的概率模型：
![image1](../../assets/f31ce33bd26d4487bb1f355fc7dfe8d3.png)

我们无法预测任何一年会发生什么，但我们可以说我们期望发生的事情。为了做到这一点，我们（或者，更确切地说，保险公司）需要概率模型。
![image2](../../assets/245a612f6f9e44e4b73901c437cd91f5.png)

![image3](../../assets/c2b0e8cbbf2949bb85b92301ef9239a4.png)

![image4](../../assets/93897ffff7e84ab4a321db9150470126.png)
注意：请确保所有可能的结果都包含在总和中。并验证您有一个有效的概率模型开始—每个概率应该在0和1之间，并且应该为1。

案例
![image5](../../assets/5c6b6ec1aa3244bda9f7e1ff975ca2a8.png)

## 15.2 Spread: The Standard Deviation
![image6](../../assets/ffbdb28ac9dd45f68f2ea156ef244b5d.png)

案例
![image7](../../assets/87f3b2403ae94c018338409d6420b866.png)

案例：离散随机变量的期望值和标准偏差

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th>作为诺威电脑公司的库存负责人，您很高兴您能够在订单到达当天成功地将两台电脑运送给您最大的客户。然而，当你发现有人在你的储藏室里重新安装了翻新过的电脑时，你会被吓坏了。运送的电脑是从15台库存的电脑中随机挑选出来的，但其中4台实际上是翻新的。如果你的客户有了两台新电脑，事情就会很好。如果客户端得到一台翻新的计算机，它将自费发送回$100，您可以更换它。但是，如果两台计算机都已翻新，客户将在本月取消订单，您将总共丢失$1000。</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>![image8](../../assets/e18767be33f74ee5a62fd591bbafec19.png)</p>
<p></p></td>
</tr>
</tbody>
</table>

## 15.3 Shifting and Combining Random Variables
1，那么这个标准偏差呢？我们知道，从数据中添加或减去一个常数会改变平均值，但不会改变方差或标准偏差。随机变量也是如此
<table>
<colgroup>
<col style="width: 80%" />
<col style="width: 19%" />
</colgroup>
<thead>
<tr class="header">
<th>![image9](../../assets/148598c5402247539caf64b26dd79def.png)</th>
<th></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>![image10](../../assets/f57e4603017b4096801a0d06c443bf7b.png)</td>
<td></td>
</tr>
<tr class="even">
<td><p>![image11](../../assets/ccfb1a05b63845d79b51e3944bd39a8e.png)</p>
<p></p>
<p>![image12](../../assets/a5373d02d0a54adda4966d6bf8c0a746.png)</p>
<p></p></td>
<td><p>![image13](../../assets/3c753c50f05d48ad9b3814a45da80021.png)</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p>![image14](../../assets/866f938000654a59beecb031e072729d.png)</p>
<p></p></td>
<td><p>■两个随机变量之和的平均值是平均值的和。</p>
<p>■两个随机变量差的平均值是平均值的差。</p>
<p>■如果随机变量是独立的，它们的和或差总是方差的和。</p></td>
</tr>
</tbody>
</table>

案例
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>我们已经确定，在安静的角落用餐的情侣可以期待幸运情人的平均折扣为$5.83，标准偏差为$8.62。假设几周来，餐厅一直在分发任何一餐价值$5的优惠券（每一张折扣）</p>
<p>![image15](../../assets/4d54a1a0cc5f43dd8eab68130194df36.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>![image16](../../assets/7eb309269df0448cb1aff1f1fdf893e7.png)</td>
</tr>
<tr class="even">
<td><p>![image17](../../assets/763076089db248b4b61d0614c8a21745.png)</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p>![image18](../../assets/8fff3f06877146d5bc44233b03b88539.png)</p>
<p></p></td>
</tr>
<tr class="even">
<td><table>
<colgroup>
<col style="width: 51%" />
<col style="width: 48%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image19](../../assets/8c138c07de4d4553b087a5cc249e3da1.png)</p>
<p></p></th>
<th><p>![image20](../../assets/a199fbd95d064628bf4d6b32e110eb39.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table></td>
</tr>
<tr class="odd">
<td><table>
<colgroup>
<col style="width: 44%" />
<col style="width: 55%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image21](../../assets/4c308a1b9f6641c8a0c3421336b50f87.png)</p>
<p></p></th>
<th><p>![image22](../../assets/c894bac823e64773a15eb4308716c483.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table></td>
</tr>
</tbody>
</table>

\*Correlation and Covariance

## 15.4 Continuous Random Variables

案例
![image23](../../assets/3f5d140c9d534726aa8e8bb3c4a1f20f.png)
1
![image24](../../assets/a4a395d9e4cb420ea46266f4c2c2fd78.png)
2
![image25](../../assets/7993ea09ebf24dc288e9de5313cdb147.png)

注意点
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>注意不独立的变量</p>
<p>别忘了：独立随机变量的差异会增加。标准偏差不会发生</p>
<p>不要忘记：独立随机变量的差异会增加，即使你在观察它们之间的差异</p>
<p>不要编写具有具有相同变量符号的随机变量的独立实例。</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

总结
![image26](../../assets/1b52e829f9c84c759b7d127cd02cdfe9.png)

