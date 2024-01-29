---
title: 16-Probability Models
updated: 2024-01-29T12:12:01.0000000+08:00
created: 2021-05-03T10:24:36.0000000+08:00
---

你要抽小卡，已知20%的盒子里有一张希望独奏的照片，30%的盒子是丹尼卡·帕特里克的照片，其余的是布莱克·格里芬的照片。

## 16.1 Bernoulli Trials
假设你是唯粉，你只关系抽到本命，抽到本命的卡的概率0.2
每一次开卡的行为称为一次trail
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>■ There are only two possible outcomes (called success and failure) on each trial. Either</p>
<p>you get Hope’s picture (success), or you don’t (failure).</p>
<p>■ The probability of success, denoted p, is the same on every trial. Here p = 0.20.</p>
<p>■ The trials are independent.</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
Situations like this occur often and are called Bernoulli trials.
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>伯努利试验（Bernoulli experiment）是在<strong>同样的条件</strong>下<strong>重复地</strong>、<strong>相互独立</strong>地进行的一种随机试验，</p>
<p>其特点是该随机试验<strong>只有两种可能结果：发生或者不发生</strong>。</p>
<p>我们假设该项试验独立重复地进行了n次，那么就称这一系列重复独立的随机试验为n重伯努利试验，或称为伯努利概型。</p>
<p>单个伯努利试验是没有多大意义的，然而，当我们反复进行伯努利试验，去观察这些试验有多少是成功的，多少是失败的，事情就变得有意义了，这些累计记录包含了很多潜在的非常有用的信息</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

Let’s call this random variable Y = \# boxes and build a probability model for it
<table>
<colgroup>
<col style="width: 57%" />
<col style="width: 42%" />
</colgroup>
<thead>
<tr class="header">
<th>抽一次中，抽两次中，抽第五次才中的概率：</th>
<th><p>![image1](../../assets/44fc675bfc0c4352b30c6dd96f94deee.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

![image2](../../assets/4be862a6e90642939a6a1ba468c64f7a.png)

## 16.2 The Geometric Model
作用：模拟在一系列伯努利试验中取得**第一次成功的概率**
1，几何模型完全由一个==参数p、成功的概率==指定，并表示GEOM(p)。由于在试验编号x上取得第一次成功需要第一次经历x-1失败，所以概率很容易用一个公式来表示。
![image3](../../assets/209ba942041a46788943386ec2ddf086.png)

案例
![image4](../../assets/baad92130bd74199903b871bf8fcbe86.png)
2，Independence
伯努利试验的一个重要要求是这些试验是独立的。
10%的条件：伯努利试验必须独立的。如果违反了这个假设，只要样本小于10人口的%，仍然可以继续进行

案例
![image5](../../assets/89519bb97d424726b8f19bc3666071dd.png)

## 16.3 The Binomial Model
1，作用：求在n实验中几次成功的概率
![image6](../../assets/bfb20feecc0340d9bf396a2928d2672a.png)

![image7](../../assets/5207d79e76164b0292589e2b5c046e95.png)
案例
![image8](../../assets/b15d6907b0694dbe8af7dcbd47fc51aa.png)

案例
![image9](../../assets/a302deae731a4aa6a6063a422a37351f.png)
## 16.4 Approximating the Binomial with a Normal Model
1，Binom(50, 0.2),
![image10](../../assets/f7b90866ce744361882c69ef897b733c.png)

案例
![image11](../../assets/e4595dd24cd944fc870f481e3f60347d.png)
## \*16.5 The Continuity Correction
![image12](../../assets/c052e656657a4d0b9e1bf06ef924c3f9.png)

## 16.6 The Poisson Model
1，泊松分布适合于描述单位时间内随机事件发生的次数。
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>泊松分布：计算一段时间内发生x次的概率</p>
<p>指数分布：是描述泊松过程中的事件之间的时间的概率分布【下一次发生的概率】</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

![image13](../../assets/0142464b1b10471080bfdd9ebf0acfd5.png)

![image14](../../assets/2b22c7845eb9456db9a70296355f753b.png)

![image15](../../assets/b132f1ce05b34f51bf74a602832c14c1.png)

![image16](../../assets/6e0572c13ecc4d46a526c5c5b38479a2.png)
2，什么时候用合适呢
![image17](../../assets/e0d25adc01d941399ce6a0255dd41456.png)

## 16.7 Other Continuous Random Variables: The Uniform and the Exponential
### 一、The Uniform Distribution
![image18](../../assets/d3704ab827b34065b2cd868dc9a1a9da.png)
1，对于连续均匀性，我们希望所有相同长度的时间间隔都具有相同的概率
![image19](../../assets/8e55dfd4e3b0435bb7aad06040400edd.png)

![image20](../../assets/0e87a8c8b13f423da1a9bf4d9b9c70ee.png)
2，案例
例如，假设您到达一个公交车站，并想要模拟您等待下一辆公交车的时间。标志上写着公交车大约每20分钟就到一次，但没有提供其他信息。你可能会假设到达同样可能是在未来20分钟内的任何地方，所以概率模型将是
![image21](../../assets/806cbe6c48f2405a912576f91cf36570.png)

### 二、The Exponential Model
指数模型用于泊松模型计算时间段的时候
![image22](../../assets/8612c2a9b1954c1287fe40ed5cd58759.png)

1，我们已经看到，泊松模型是事件的到达或发生的一个很好的模型。例如，假设我们使用泊松来建模x在下一分钟内访问我们的网站的概率。然后，可以使用参数为l的指数模型来模拟这些事件之间的时间。因为时间是一个连续的量，所以它有一个连续的模型，它的形式为：
![image23](../../assets/3a0808444810421c8af75f3cf2b2d6ee.png)

![image24](../../assets/baf414dcb1894c558230ebf3a826f65b.png)

总结
![image25](../../assets/6c569808037f4d6e891e4fa05fe38a84.png)
![image26](../../assets/9bf1fa293e9843c191acbee512cce5d3.png)

![image27](../../assets/0e2526218c6a4c44a66a1179e17f3acb.png)

补充
Continuous random variable
![image28](../../assets/0aa9aa8df6974345b9087d9156b4ad0d.png)

