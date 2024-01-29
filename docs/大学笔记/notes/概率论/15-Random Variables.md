---
title: 15-Random Variables
updated: 2024-01-29T12:10:53.0000000+08:00
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
</tbody>
</table>

案例，保险公司
例如，假设任何一年的死亡率是每1000人中就有1人，而1000人中又有2人患有某种残疾。然后我们可以在这样的表格中显示此保险单的概率模型：
![image1](../../assets/8a93bf2cce534f57914398da8e8f5be5.png)

我们无法预测任何一年会发生什么，但我们可以说我们期望发生的事情。为了做到这一点，我们（或者，更确切地说，保险公司）需要概率模型。
![image2](../../assets/4f41002dc819469ba34f22b0e3ff7d41.png)

![image3](../../assets/3d4c81852e2641958b76f7262ccb8d2e.png)

![image4](../../assets/e0dbbd92ba134f90bbabf14d8eb7b5e7.png)
注意：请确保所有可能的结果都包含在总和中。并验证您有一个有效的概率模型开始—每个概率应该在0和1之间，并且应该为1。

案例
![image5](../../assets/ec9fcdb27fc246f0bdf5bda4cec47246.png)

## 15.2 Spread: The Standard Deviation
![image6](../../assets/913ef62acd7c4c849a8eb310c32da11c.png)

案例
![image7](../../assets/772ddfbf7e7447fa931e189df0a99431.png)

案例：离散随机变量的期望值和标准偏差

作为诺威电脑公司的库存负责人，您很高兴您能够在订单到达当天成功地将两台电脑运送给您最大的客户。然而，当你发现有人在你的储藏室里重新安装了翻新过的电脑时，你会被吓坏了。运送的电脑是从15台库存的电脑中随机挑选出来的，但其中4台实际上是翻新的。如果你的客户有了两台新电脑，事情就会很好。如果客户端得到一台翻新的计算机，它将自费发送回\$100，您可以更换它。但是，如果两台计算机都已翻新，客户将在本月取消订单，您将总共丢失\$1000。
![image8](../../assets/40ed7916fb084f6ca2a6c8cbee7273db.png)

## 15.3 Shifting and Combining Random Variables
1，那么这个标准偏差呢？我们知道，从数据中添加或减去一个常数会改变平均值，但不会改变方差或标准偏差。随机变量也是如此
![image9](../../assets/1e195685abfe4a43961a8d78bf41472f.png)
案例
![image10](../../assets/4d8dd97abcb74f2bb2a5cd4ae4eed3e3.png)
\*Correlation and Covariance

## 15.4 Continuous Random Variables

案例
![image11](../../assets/2fb5fed6656b40a1981f639958cb52c5.png)
1
![image12](../../assets/6cb6b06cd5334a4fa35f773a745b4922.png)
2
![image13](../../assets/c5f62226d7804f1b9138fe5bca2ed889.png)

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
![image14](../../assets/8218dd6d4afe4bf5b3f12eb98cbe9453.png)

