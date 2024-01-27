---
title: '8-Branch Coverage '
updated: 2020-11-08T14:35:51.0000000+08:00
created: 2020-11-08T14:22:52.0000000+08:00
---

一，基础知识
1，与statement coverage类似，statement coverage是要覆盖所有nodes，branch coverage是要覆盖所有分支（a,b,c,d…）
• Branch coverage is **a stronger form** of testing than Statement Coverage

2,The goal of Branch Coverage is to **make sure that all branches** in the
source code have been **checked** during testing,
**100% branch coverage guarantees 100% statement coverage**.

**3,基于节点图【**control flow graph.**】**

4，Test Cases and Test Data
在控制流图中，源代码中的每个分支都是一个测试
用例，即图中的每条边都是一个测试用例。

二、步骤
1，根据代码，画出节点图
2，确定test cases，每条分支为一个case
3，find paths，所有的**分支**都要被覆盖，path数量要最小的，
4，列出test data
5，测试，找出错误，修正

案例
![image1](../../assets/ba4b8434b451430792d739350db2ce77.png)
1，根据代码，画出节点图
2，确定test cases，每条分支为一个case

![image2](../../assets/1be9220f417549e08bd53b4d9a04901e.png)
3，find paths，所有的**分支**都要被覆盖，path数量要最小的，

![image3](../../assets/2294fdc2e82a4d0586470f4d74c5bb0c.png)
4，列出test data

![image4](../../assets/316f5c8b5616403cb8562e72dc22b61e.png)

![image5](../../assets/6ae717ebea0842818d6331113946c80e.png)

