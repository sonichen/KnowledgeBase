---
title: '7-Statement Coverage '
updated: 2020-11-08T14:26:09.0000000+08:00
created: 2020-10-27T20:18:22.0000000+08:00
---

一，介绍
1，Structural testing 结构测试，通常在functional testing后使用
1，Structural testing 【又名 white-box testing】：基于实现的测试或**基于代码的测试。**
3，测试被设计用来评估程序代码的特定方面，如语句或决策。
4，提供实现的覆盖范围，但不提供规范的覆盖范围。

二
1，Structured Programming Constructs

在图中标出Branch ID，Line numbers， T（只要正确的标出就好啦）， Node numbers

<table>
<colgroup>
<col style="width: 3%" />
<col style="width: 25%" />
<col style="width: 37%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p></p>
<p>If-Then-Else</p></th>
<th><p>![image1](../../assets/a6b47b14ae9f41b6905d9a1679cd42ba.png)</p>
<p></p></th>
<th><p>![image2](../../assets/7ff18f7093e84e9f98f6da9835da25b7.png)</p>
<p></p></th>
<th></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Case/Switch</td>
<td><p>![image3](../../assets/c6fdffd506af4faba0f26c19e58e619a.png)</p>
<p></p></td>
<td><p>![image4](../../assets/7f4b7b0001d14604b175fdb2dea29f94.png)</p>
<p></p></td>
<td><p>![image5](../../assets/c6486bb17a9a4930ab51b862a1373fe3.png)</p>
<p></p></td>
</tr>
<tr class="even">
<td><p>Pre-test Loop</p>
<p></p></td>
<td><p>![image6](../../assets/4cc023c046de4ebfa366f73e5e4ffc7b.png)</p>
<p></p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td><p><strong>While·</strong></p>
<p><strong>注</strong></p>
<p><strong>1,while的单独一行，不包括到其他</strong></p>
<p><strong>2,记得循环结束后回去，再次循环</strong></p></td>
<td><p>![image7](../../assets/4934ff36733a458daa68fb643a5b03cf.png)</p>
<p></p></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td><p>For</p>
<p>1,分为三部分abc</p></td>
<td><p>![image8](../../assets/f27ba7fd239e413f835ae10a06af369a.png)</p>
<p></p></td>
<td></td>
</tr>
<tr class="odd">
<td>Post-test Loop</td>
<td><p>![image9](../../assets/b5d94bdeb4c74765a1e9d4766f49ae8e.png)</p>
<p></p></td>
<td><p>![image10](../../assets/8895ae50616f48578e336d1a7bf2bbc1.png)</p>
<p></p></td>
<td></td>
</tr>
</tbody>
</table>

2，Decision vs. Condition
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Condition :单个判断，组成了decision</p>
<p>Decision ：if()里的一行</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
![image11](../../assets/3a2fadcb5cc64036b75ee91d8666c014.png)

3，Each statement in the source code is a test case.
Each node in the control flow graph is a test case.

三，实现步骤
1，根据代码，画出节点图
2，确定test cases，每个node为一个节点
3，find paths，出现的node都要被path覆盖，path数量要最小的，
4，列出test data
5，测试，找出错误，修正

案例
1，根据代码，画出节点图
![image12](../../assets/5842df8a57ea422fa20212ef6e67dd89.png)

2，确定test cases，每个node为一个节点
![image13](../../assets/49a5fae90a3a45b4aa2a651bb2697d33.png)

3，find paths，path数量要最小的，**所有的node都要被path覆盖**
Find minimum numbers of path that cover all nodes in the graph.
每一条path是一个test
![image14](../../assets/c067b4d1c3014a18a86ef3e2b01d3096.png)

4，列出test data
![image15](../../assets/5493369165084cdcb5a76f8e338f5135.png)
5，测试，找出错误，修正

测试方法不唯一

四，Coverage Criteria
指已通过测试的组件的百分比。
例如，100%的语句覆盖率意味着程序中的所有源代码行在测试期间至少执行了一次
![image16](../../assets/f5f9aa0bc3d34cdd8c7d0801fde18a70.png)

五，总结
1， There is no differentiation between error and non-error cases for structural testing.
**2，语句覆盖通常在function testing后使用。**
•在实践中，应消除重复的测试用例。
5，必须执行每一行源代码；通过在测试期间执行源代码中的所有语句，它提供了最低级别的覆盖率。
6，语句覆盖率通常用于少量的测试。

·
