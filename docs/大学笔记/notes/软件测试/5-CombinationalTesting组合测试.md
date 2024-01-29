---
title: 5-Combinational Testing组合测试
updated: 2020-11-08T11:40:12.0000000+08:00
created: 2020-10-22T17:41:14.0000000+08:00
---

真值表
1,
• Identify all the combinations of input to the software and associated output.

• The **inputs** to the software is called the **Causes**; the associated **output** is called the **Effects**.
| ![image1](../../assets/1ecc5058644242f88f067313f98fc438.png) |
|------------------------------------------------------------------------------------------------------------------------|
| ![image2](../../assets/28126378ca254c0b801b253f6e198753.png) |

• These Causesand Effectsare combined in **a truth table** that describes their relationship.

2,目的：To identify **a minimum subset of the possible combinations** that will test all the different behaviors of the program.

![image3](../../assets/087c352b365746aca19d2c61ced116c2.png)

• **Causes and Effects** must be expressed as **Boolean expressions**.

3，步骤：
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>1，根据题目，列出causes【input】和effects【output】</p>
<p></p>
<p>2，对于causes：</p>
<blockquote>
<p>1）先分裂开单个形式</p>
<p>2）根据符号组合</p>
<p>3）根据大小排序</p>
<p>4）消除多余的causes（消除相反的causes，不要冗余）</p>
<p>（为什么要组合和排序的过程呢？）</p>
<p></p>
</blockquote>
<p>3，画真值表</p>
<blockquote>
<p>1）<strong>表内不包含非法的情况【为了控制真值表的大小】</strong></p>
<p>![image4](../../assets/e9e04dcc52164c4bb54db98bb8f2dc96.png)</p>
<p>3）effects完全相同，causes只有一个不相等的不同列，该不相等的cause可以视为 don't care condition,(对结果没有影响)，用<strong>*</strong>来表示，合并不同列</p>
<p>4）剩余的情况作为rules</p>
<p></p>
</blockquote>
<p>4，画出test case，test data</p>
<p></p>
<p>5，进行测试，找出错误</p>
<p></p>
<p>6，修改原码</p>
<p></p>
<p><strong>7，如果输入的组合可能导致错误，那么可以使用单独的表，只包含错误输出</strong></p>
<p><strong>If combinations of inputs can cause errors, a separate table may be used, covering just the error outputs</strong></p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

案例
![image5](../../assets/86fcccb0b3d34a2eb75346bb4159b60a.png)

1，根据题目，列出causes和effects
![image6](../../assets/3244168e750f42889fd78811e06a1f02.png)

2，对于causes：
1）先分裂开单个形式

2）根据符号组合

3）根据大小排序

4）消除多余的causes**（消除相反的causes，不要冗余）**

![image7](../../assets/1ed7221c058c478fb0d1b4f4a967ae60.png)

![image8](../../assets/61f008d17f2c48d0a2030894d620bcc9.png)

![image9](../../assets/b779582878d248a3b81da40f66974e9c.png)
3，画真值表
1）表内不包含非法的情况：为了控制真值表的大小

![image10](../../assets/40b01959b061472eafa97b70b95dde68.png)

![image11](../../assets/4b06519171074a5a955f1bbe72cb5007.png)

![image12](../../assets/3b50f99497b54fdebe4917cc2b849d73.png)

3）effects完全相同，causes只有一个不相等的不同列，该不相等的cause可以视为 don't care condition,(对结果没有影响),用\*来表示，合并不同列

![image13](../../assets/993574e8e9354f60b31fdf11183b89c5.png)

4）剩余的情况作为rules

![image14](../../assets/1b264caebb69465094d21a83284cd9e0.png)
4，画出test case，test data

![image15](../../assets/fe5f53d0e279407489dc9587c76d242f.png)
5，进行测试，找出错误

![image16](../../assets/fe235f67b2ce426e84972b909183ef9d.png)

6，修改原码

![image17](../../assets/7dfdd052e698475984ffb93842f83a2d.png)

