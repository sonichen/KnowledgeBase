---
title: 16-Probability Models
updated: 2021-07-03T09:15:09.0000000+08:00
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
<th><p>![image1](../../assets/1a13e4e6934442ac908638017fd6db46.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

![image2](../../assets/bf040119201d409985c3bc632c277454.png)

## 16.2 The Geometric Model
作用：模拟在一系列伯努利试验中取得**第一次成功的概率**
1，几何模型完全由一个==参数p、成功的概率==指定，并表示GEOM(p)。由于在试验编号x上取得第一次成功需要第一次经历x-1失败，所以概率很容易用一个公式来表示。
![image3](../../assets/5ccd1e3d3a9e41f68d5d8b3516f7195f.png)

案例
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th>假设您的电子邮件，其中91%是垃圾邮件。我们还假设您没有使用垃圾邮件过滤器，因此每条邮件都会转储到收件箱中。而且，由于垃圾邮件来自许多不同的来源，我们将认为您的邮件是独立的</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>一夜之间，你的收件箱就会收集电子邮件。当你在早上第一次检查你的电子邮件时，你在找到真正的邮件之前应该需要丢弃多少垃圾邮件？</p>
<p>收件箱中的第四条邮件是第一个不是垃圾邮件的可能性是多少？</p></td>
</tr>
<tr class="even">
<td><p>![image4](../../assets/b6689379aa5e4b6fb4df686616338a9e.png)</p>
<p></p></td>
</tr>
</tbody>
</table>

2，Independence
伯努利试验的一个重要要求是这些试验是独立的。
10%的条件：伯努利试验必须独立的。如果违反了这个假设，只要样本小于10人口的%，仍然可以继续进行

案例
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th>O阴性血的人被称为“普遍捐赠者”，因为O阴性血可以提供给任何人，不管受试者的血型如何。只有大约6%的人有o-阴性的血。</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1.ᾏ如果献血者随机排队献血，在你发现有人有o阴性血液之前，你需要检查多少人？</p>
<p>2.ᾏ第一个o阴性供体是前四人之一的可能性是多少？</p></td>
</tr>
<tr class="even">
<td><p>![image5](../../assets/836711a508334ade9008a1b7fb282c47.png)</p>
<p></p></td>
</tr>
</tbody>
</table>

## 16.3 The Binomial Model
1，作用：求在n实验中几次成功的概率
<table>
<colgroup>
<col style="width: 55%" />
<col style="width: 44%" />
</colgroup>
<thead>
<tr class="header">
<th>![image6](../../assets/c09f3c7676144b75bc9d76f227c6d7bf.png)</th>
<th><p>![image7](../../assets/0f09b02dbde247e684223fbb494df5ee.png)</p>
<p></p>
<p>![image8](../../assets/5cd635d9790549dbb45cc2ce223d96c5.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

![image9](../../assets/afc2c8767a914286b7e5b1e2c32ddc3e.png)
案例
![image10](../../assets/eeafdd1662504162a05e49b405894208.png)

案例
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>假设有20个捐赠者来这里献血。回想一下，6%的人是“普遍的捐赠者”。“</p>
<p>问题：</p>
<p>1。其中普遍捐助者数量的平均值和标准偏差是多少？</p>
<p>2.有2个或3个普遍捐赠者的可能性是多少？</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>![image11](../../assets/87f480366f4947ceb72c9f09b709e2bd.png)</p>
<p></p></td>
</tr>
</tbody>
</table>

## 16.4 Approximating the Binomial with a Normal Model
1，Binom(50, 0.2),
![image12](../../assets/a3804ecb248f4161a2df26a3672e8de9.png)

案例
![image13](../../assets/66c4f61591974fe58b02c6b52f4aae2a.png)
## \*16.5 The Continuity Correction
![image14](../../assets/2d7222d977374acea74696dcb34a82ec.png)

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

![image15](../../assets/4804ccd2683b4dbca8d2fa9f3cb8e93b.png)

![image16](../../assets/4dba6c2de80f49a687ff6f5eea582e99.png)

![image17](../../assets/afb33a158d754831af2df0dcd4b67e08.png)

![image18](../../assets/e6081ecc91c04aa793df9bf86a3fa114.png)
2，什么时候用合适呢
![image19](../../assets/83f9db7bc97a4480b46005b3c8f712d0.png)

## 16.7 Other Continuous Random Variables: The Uniform and the Exponential
### 一、The Uniform Distribution,
<table>
<colgroup>
<col style="width: 65%" />
<col style="width: 34%" />
</colgroup>
<thead>
<tr class="header">
<th>在概率论和统计学中，均匀分布也叫矩形分布，它是对称概率分布，在相同长度间隔的分布概率是等可能的。 均匀分布由两个参数a和b定义，它们是数轴上的最小值和最大值，通常缩写为U（a，b）。</th>
<th><p>![image20](../../assets/eaa8fa5752d6493083d79601eafd0ef5.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>![image21](../../assets/9a39ab18c0674c078cdf3b66a513841a.png)</p>
<h3 id="section"></h3></td>
<td><h3 id="section-1"></h3></td>
</tr>
<tr class="even">
<td><p>![image22](../../assets/7e0b489d0280425c92c9d73f01f11810.png)</p>
<h3 id="section-2"></h3></td>
<td><h3 id="section-3"></h3></td>
</tr>
<tr class="odd">
<td><p>![image23](../../assets/d4faef7e10a9457da2560affd1a17e4f.png)</p>
<p></p></td>
<td></td>
</tr>
</tbody>
</table>
1，对于连续均匀性，我们希望所有相同长度的时间间隔都具有相同的概率
![image24](../../assets/8b69e33606f148d98a4cfc5540a4fa1e.png)

![image25](../../assets/0a5d2985a45a4aeebbc54bcff302b677.png)
2，案例
例如，假设您到达一个公交车站，并想要模拟您等待下一辆公交车的时间。标志上写着公交车大约每20分钟就到一次，但没有提供其他信息。你可能会假设到达同样可能是在未来20分钟内的任何地方，所以概率模型将是
![image26](../../assets/a81fc0157fbb45b7a533ce6f24419834.png)

### 二、The Exponential Model
指数模型用于泊松模型计算时间段的时候
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th>在概率理论和统计学中，<a href="https://baike.baidu.com/item/%E6%8C%87%E6%95%B0%E5%88%86%E5%B8%83/776702?fr=aladdin">指数分布</a>（也称为负指数分布）是描述泊松过程中的事件之间的时间的概率分布，即事件以<strong>恒定平均速率连续且独立地发生的过程</strong>。 这是伽马分布的一个特殊情况。 它是几何分布的<strong>连续模拟</strong>，它具有无记忆的关键性质。</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>![image27](../../assets/b2b258c4344f483c81c2e9bf5cc3dffb.png)</p>
<p></p></td>
</tr>
<tr class="even">
<td>![image28](../../assets/05036e7ea2ff49f4a1f0c0c713719473.png)</td>
</tr>
<tr class="odd">
<td><p>![image29](../../assets/a7b706723b1d4814a12bd90f9ffde670.png)</p>
<p></p></td>
</tr>
<tr class="even">
<td></td>
</tr>
</tbody>
</table>

1，我们已经看到，泊松模型是事件的到达或发生的一个很好的模型。例如，假设我们使用泊松来建模x在下一分钟内访问我们的网站的概率。然后，可以使用参数为l的指数模型来模拟这些事件之间的时间。因为时间是一个连续的量，所以它有一个连续的模型，它的形式为：
![image30](../../assets/09deea1a6d664beb9b9fd465afafb6cc.png)

![image31](../../assets/fb53c0a2660b4da19f6cba6f889bb7d8.png)

总结
![image32](../../assets/9a8f6b7423314ba1a9fad3955cf40e2c.png)
![image33](../../assets/c5a8b62901ff4061ba8db4b143a252ef.png)

![image34](../../assets/db7bd025d63746eab358e32befd5de0d.png)

补充
Continuous random variable
![image35](../../assets/2f9d80d278b843c7a938d219d296528c.png)

