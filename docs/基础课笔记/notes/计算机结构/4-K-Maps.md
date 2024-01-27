---
title: 4-K-Maps
updated: 2021-01-07T19:10:24.0000000+08:00
created: 2020-11-12T16:30:03.0000000+08:00
---

一、K-Maps
1，一种化简布尔代数式的方法，要Minimized Expressions
| ![image1](../../assets/a9cce9d60fde4cec8428bdb1e687775e.png)                                                           |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ![image2](../../assets/507153a2cec247dfba9e8df1d5a13d56.png) |
indices are labelled using a reflected **binary Gray code**

**2，格雷码**
<table>
<colgroup>
<col style="width: 86%" />
<col style="width: 13%" />
</colgroup>
<thead>
<tr class="header">
<th><p>格雷码：格雷码属于可靠性编码，是一种错误最小化的编码方式</p>
<p></p>
<p>格雷码的构造方法为：</p>
<p>直接排列以二进制为0值的格雷码为第零项，</p>
<p><strong>第一项改变最右边的位元，</strong></p>
<p><strong>第二项改变右起第一个为1的位元的左边位元，</strong></p>
<p>第三、四项方法同第一、二项，如此反覆，即可排列出n个位元的格雷码。</p></th>
<th><p>![image3](../../assets/21935fbcf64c42ff8cb233ec84dbf11e.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

3,Implicant一类
![image4](../../assets/631576632d8246ebae3755098da6c583.png)

![image5](../../assets/a81b0c1f263346f1a7149ab919728ea0.jpeg)
![image6](../../assets/376282c7585b429ea0b8ec901522c3c9.jpeg)

![image7](../../assets/675b139e58524459a141ade9c6716202.png)

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 49%" />
</colgroup>
<thead>
<tr class="header">
<th>prime implicants</th>
<th>essential</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>![image8](../../assets/67fe9b022055451f996fe78c1c0493fe.png)</p>
<p></p></td>
<td><p>![image9](../../assets/f6bd1dd6c1254cf6ab2af22a469f4d3d.png)</p>
<p></p></td>
</tr>
</tbody>
</table>

4、K-maps案例
案例1
![image10](../../assets/47e9c3f3a0464accb5a18cb8cd35cfb5.png)

![image11](../../assets/d136ce581da44f10b4de1dbc1bebb6d8.png)

案例2
| ![image12](../../assets/014251fb4eeb4514ad6630b24d0d103a.png) | ![image13](../../assets/87c99156a6ac4f8aae7799ff5605e69f.png) |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|

案例3
<table>
<colgroup>
<col style="width: 84%" />
<col style="width: 15%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image14](../../assets/53cb928c084f49bba6fd18d2012b51a0.png)</p>
<p></p></th>
<th></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

4，Don’t Care Terms on K-Maps
可0可1，对结果没有影响，用x来表示

案例
![image15](../../assets/dd1d8cfb9a304da7b3c5e591b758b743.png)

