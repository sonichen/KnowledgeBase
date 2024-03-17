---
title: Math类
updated: 2020-09-08T08:01:01.0000000+08:00
created: 2020-09-07T13:20:00.0000000+08:00
---

java.lang.Math提供了一系列**静态方法**用于科学计算。**其方法的参数和返回 值类型一般为double型**。

| abs                        | 绝对值                                |
|----------------------------|---------------------------------------|
| acos,asin,atan,cos,sin,tan | 三角函数                              |
| sqrt                       | 平方根                                |
| pow(double a,doble b)      | a的b次幂                              |
| log                        | 自然对数                              |
| exp                        | e为底指数                             |
| max(double a,double b)     |                                      |
| min(double a,double b)     |                                      |
| random()                   | 返回0.0到1.0的随机数                  |
| long round(double a)       | double型数据a转换为long型（四舍五入） |
| toDegrees(double angrad)   | 弧度—\>角度                           |
| toRadians(double angdeg)   | 角度—\>弧度                           |

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>public void test1(){</p>
<p>System.out.println(Math.sin(30));</p>
<p>System.out.println(Math.pow(2,2));//4.0</p>
<p>System.out.println(Math.random());//0.764258932577392</p>
<p></p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
