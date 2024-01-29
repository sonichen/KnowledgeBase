---
title: 18-Confidence Interval
updated: 2024-01-29T12:13:03.0000000+08:00
created: 2021-05-04T11:50:13.0000000+08:00
---

背景：在156名18岁到22岁的受访者中，有48人说，他们至少每天都会更新自己的状态。报告的作者讨论了这一发现，就好像这156名受访者告诉了我们，这个年龄段的数百万Facebook用户的行为一样。当然，这比了解156个Facebook用户更有趣，不管他们的采样是多么仔细。像这样的研究能告诉我们关于18到22岁的Facebook用户的什么呢？

![image1](../../assets/742f2babe3624df496603fee3827c4e0.png)
## 18.1 A Confidence Interval
因为
![image2](../../assets/77893fb5896a49eea9bca4234c1ff716.png)

不知道p,但是为了标准差，所以
![image3](../../assets/cbc797e70e38475096294e698f2b4451.png)

得到sampling model for p尖
![image4](../../assets/f6d865eed1854732bb4b49dcb9f10b7a.png)

![image5](../../assets/84f4ca3a429444a88a2aa9f415a7c538.png)
请注意表述，“哔哩哔哩xx%confident哔哩哔哩”
![image6](../../assets/389d760e07034f0e90bb3ba618dbdd7f.png)

又名
![image7](../../assets/66e3116bb2844443b074b72247f9d419.png)

## 18.2 Interpreting Confidence Intervals: What Does 95% Confidence Really Mean?
“we are 95% confident that the true proportion lies in our interval.”

我们知道不同样本的比例也不同。如果其他研究人员选择自己每天更新状态的Facebook用户的样本，每个人的样本比例几乎肯定会有所不同。当他们都试图估计整个人群的真实状态更新率时，他们将把置信区间集中在在自己样本中观察到的比例上。我们每个人都会有一个不同的间隔。
![image8](../../assets/233bf56873fd4eb5b61874f3cdffe0af.png)
案例
![image9](../../assets/d0cefdd08c2d48d1997dbcce60c5f45a.png)

CLT中心极限定理告诉我们，95%的随机样本将产生捕获真实值的区间。这就是我们所说的95%的自信程度。

## 18.3 Margin of Error: Certainty vs. Precision
1，ME
![image10](../../assets/665f707e38ad4c88aa3ca2d4becb5681.png)
公式
![image11](../../assets/70ad1b330d8f47728d87d9e562c5bd94.png)

![image12](../../assets/423d1440fc2344dd9764b4c0ef8f84a0.png)
案例
![image13](../../assets/c31625c4b91449da99d4c44fd97758a5.png)

2，Critical Values
2.1 定义
![image14](../../assets/1128c04ba34e4857b401d3723754bdf1.png)

2.2 常用的z\*的值
![image15](../../assets/b57d8d955a2c4f758cac19b896794910.png)

注：**ME=z\*SE**
案例
![image16](../../assets/6ddde4538fdd401983bf2f10084f3a04.png)

## 18.4 Assumptions and Conditions
1，
Independence Assumption
- Randomization Condition:
- 10% Condition:

Sample Size Assumption:
- Success/Failure Condition 10胜10负

![image17](../../assets/4eaf1aed28c844ab86666515ca6e6218.png)

案例
![image18](../../assets/6a16b18516b947f0882e004caa1ee1d2.png)
2，Choosing Your Sample Size
假设一个候选人正在计划进行投票，并希望以95%的信心将选民的支持率估计在3%以内。她需要一个多大的样本？
![image19](../../assets/0bf9441a81e54aff8c1d0c830070c337.png)
案例
![image20](../../assets/5ee2f6ecf61744bdbea35f34f65dd9e6.png)
案例
![image21](../../assets/b006a3c6008b4c8a944ec42a6963474f.png)

总结
![image22](../../assets/1409eab7a3e9452bbb81d090da0b76b4.png)

![image23](../../assets/a4cb81b944604d9d99abb64d40147800.png)
