---
title: 18-Confidence Interval
updated: 2021-05-13T09:32:26.0000000+08:00
created: 2021-05-04T11:50:13.0000000+08:00
---

背景：在156名18岁到22岁的受访者中，有48人说，他们至少每天都会更新自己的状态。报告的作者讨论了这一发现，就好像这156名受访者告诉了我们，这个年龄段的数百万Facebook用户的行为一样。当然，这比了解156个Facebook用户更有趣，不管他们的采样是多么仔细。像这样的研究能告诉我们关于18到22岁的Facebook用户的什么呢？

![image1](../../assets/3b9d37aa675d4ccd855ed6fa36a10ec8.png)
## 18.1 A Confidence Interval
因为
![image2](../../assets/a3b05977c45045d9b5754e57fbdc690b.png)

不知道p,但是为了标准差，所以
![image3](../../assets/5bf5d1f68cca4a168c1f99e391b2e94c.png)

得到sampling model for p尖
![image4](../../assets/4481cb548b6646e4969125fdf6391be7.png)

<table>
<colgroup>
<col style="width: 57%" />
<col style="width: 42%" />
</colgroup>
<thead>
<tr class="header">
<th>![image5](../../assets/32b9d334c16440d8823c02a4179b88db.png)</th>
<th><p>![image6](../../assets/d0e97ec99e1143c5ac0be10ede51242a.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

请注意表述，“哔哩哔哩xx%confident哔哩哔哩”
![image7](../../assets/33f3d38855c1499a847fc1ead072c07a.png)

又名
![image8](../../assets/f4b39812a6fc4f71a87772ebd93118a7.png)

## 18.2 Interpreting Confidence Intervals: What Does 95% Confidence Really Mean?
“we are 95% confident that the true proportion lies in our interval.”

我们知道不同样本的比例也不同。如果其他研究人员选择自己每天更新状态的Facebook用户的样本，每个人的样本比例几乎肯定会有所不同。当他们都试图估计整个人群的真实状态更新率时，他们将把置信区间集中在在自己样本中观察到的比例上。我们每个人都会有一个不同的间隔。
![image9](../../assets/04265069373b42eebabc87ab499ba36c.png)
案例
![image10](../../assets/65938e07c314422eb784b9551b14036a.png)

CLT中心极限定理告诉我们，95%的随机样本将产生捕获真实值的区间。这就是我们所说的95%的自信程度。

## 18.3 Margin of Error: Certainty vs. Precision
1，ME
![image11](../../assets/f65c25d53de14b27936295726e9ed123.png)
公式
| ![image12](../../assets/7a95d36e47ee409d8dd9963cf1402e04.png)  |    |
|-------------------------------------------------------------------------------------------------------------------------|-----|
| ![image13](../../assets/bc33c0fdabae46be85f6bc178085753b.png) |    |

![image14](../../assets/9e1540e239544e9bba221585b7638b30.png)
案例
![image15](../../assets/e69e8a30c0734194a3d06af74f4d3a4d.png)

2，Critical Values
2.1 定义
![image16](../../assets/007b02889b824145a0ddcb1ac6fc1a05.png)

2.2 常用的z\*的值
![image17](../../assets/fee7250664de46ce921cb284d638b027.png)

注：**ME=z\*SE**
案例
![image18](../../assets/d6c983be75e24593b526ba1e8889b65b.png)

## 18.4 Assumptions and Conditions
1，
Independence Assumption
- Randomization Condition:
- 10% Condition:

Sample Size Assumption:
- Success/Failure Condition 10胜10负

![image19](../../assets/9da611e428a14c4b8c457ea4dff8091d.png)

案例
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>2010年10月，盖洛普民意调查7问了510名随机抽样的成年人一个问题：“一般来说，你认为今天死刑在这个国家是公平还是不公平？”其中58%的人回答“公平”，36%的人说“不公平”，7%的人说他们不知道（由于四舍五入，百分比高达101%）。</p>
<p>从这个调查中，我们可以对所有成年人的意见得出什么结论呢？为了回答这个问题，我们将为所有相信死刑被公平适用的美国成年人的比例建立一个信任区间。建立一个针对比例的置信区间有四个步骤：计划、模型、力学和结论。</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><table>
<colgroup>
<col style="width: 48%" />
<col style="width: 51%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Check condition</p>
<p>![image20](../../assets/53caa025c576451c8f48989f3dc8eb26.png)</p>
<p></p></th>
<th><p>![image21](../../assets/bd41ef48c85a4994bc597c257091f9af.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table></td>
</tr>
</tbody>
</table>

2，Choosing Your Sample Size
假设一个候选人正在计划进行投票，并希望以95%的信心将选民的支持率估计在3%以内。她需要一个多大的样本？
![image22](../../assets/a5e99cdcc4a64b39a7b219fe8e763d40.png)
案例
![image23](../../assets/5eb4acf885e8423fa11a9c9a90a82d8d.png)
案例
![image24](../../assets/400b3614001240e6bc3d376ca5c8de14.png)

总结
![image25](../../assets/55f79af8f5b1493a8e4e58cd59e12ef6.png)

![image26](../../assets/0c85fdfd745f4cf9966ba89c994d36f1.png)
