---
title: 5-Big O Notation
updated: 2021-01-05T17:18:48.0000000+08:00
created: 2020-09-13T11:02:23.0000000+08:00
---

一、基本内容
1，Big 𝑶 is always concerned with **worst case time requirement**

2，Big O计算：
看最高次项，忽略系数
![image1](../../assets/ba7b0ea1736440fd9821bae3a60fa140.png)

平行的O相加，内嵌的O相乘

<table>
<colgroup>
<col style="width: 48%" />
<col style="width: 51%" />
</colgroup>
<thead>
<tr class="header">
<th>![image2](../../assets/9dc90470253d4a6eb68c033c45a9dbc7.png)</th>
<th><p>![image3](../../assets/fe381713595545028a3bf1762501945f.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

3，search
<table>
<colgroup>
<col style="width: 42%" />
<col style="width: 57%" />
</colgroup>
<thead>
<tr class="header">
<th>linear Search</th>
<th>Binary Search</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>![image4](../../assets/83286aec962041a5aac28eb8d96d6f8a.png)</p>
<p></p></td>
<td><p>![image5](../../assets/967ec3d2d17b4996a6b89940a79f7d91.png)</p>
<p></p>
<p></p></td>
</tr>
</tbody>
</table>

4，基本操作的big O
![image6](../../assets/253c3692f14442b8afd57c460a64c2f4.png)

![image7](../../assets/bc73a588c849453c872b1e91985283d2.png)

二、Formalities

![image8](../../assets/87a49abe92a945adbe91fd96cdded623.png)

<table>
<colgroup>
<col style="width: 48%" />
<col style="width: 49%" />
<col style="width: 1%" />
</colgroup>
<thead>
<tr class="header">
<th>![image9](../../assets/544d70a4e78b46af9d9f3552649f7b20.png)</th>
<th><p>![image10](../../assets/951bda5b5bb547e1818c28c2463863c1.png)</p>
<p></p></th>
<th><p></p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 49%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image11](../../assets/74992ac7aeff49cfb3e39397b8378888.png)</p>
<p></p></th>
<th><p></p>
<p></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>![image12](../../assets/c2f0367e821d4c438a23ccc19b21ee09.png)</p>
<p></p></td>
<td><p>![image13](../../assets/db5c3024a2b94889b90ba8c5e0709c4e.png)</p>
<p></p></td>
</tr>
</tbody>
</table>

![image14](../../assets/f4249dda9f6d4d4ca23cd6d74740dd7b.png)

三、Usage
1,一直用最简形式来描述O-notation
![image15](../../assets/41ead6ce607c49a492ce9083726b6c95.png)

![image16](../../assets/08286499a2d9486ebc372e4164caa07d.png)

![image17](../../assets/2dcbbb75a3684e58a6008d397763e1e9.png)

五、Getting Big O of a program
1，
![image18](../../assets/7cd945ef7c4141dc8117cd469c715ebf.png)

![image19](../../assets/562b901f13ef46829b3b3cafe375d716.png)

![image20](../../assets/cee8ec0aaa6e448492b35721675d7805.png)

重点
![image21](../../assets/08593a3f30ed421ca65aeb53f0b46c02.png)

![image22](../../assets/46a85806a469411cb05b600b6114df35.png)

![image23](../../assets/85924378e815432d87e834322378cb73.png)

![image24](../../assets/d6802546976a4f14bb22a0edbc3d221e.png)

![image25](../../assets/c097eefa789443279acc0fb70af4d81a.png)

