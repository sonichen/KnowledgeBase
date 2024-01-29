---
title: 图论模型-Floyd算法
updated: 2020-11-12T12:11:35.0000000+08:00
created: 2020-11-12T11:23:17.0000000+08:00
---

一，

1，需求
![image1](../../assets/8cd3d1b0ce5249a7adf27e0ff85a058a.png)

2，Floyd算法思想
![image2](../../assets/d75f7323617749998aadaf0456c8c066.png)
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>function [D,path,min1,path1]=floyd(a,start,terminal)</p>
<p>D=a;n=size(D,1);path=zeros(n,n);</p>
<p>for i=1:n</p>
<p>for j=1:n</p>
<p>if D(i,j)~=inf</p>
<p>path(i,j)=j;</p>
<p>end,</p>
<p>end,</p>
<p>end</p>
<p>for k=1:n</p>
<p>for i=1:n</p>
<p>for j=1:n</p>
<p>if D(i,k)+D(k,j)&lt;D(i,j)</p>
<p>D(i,j)=D(i,k)+D(k,j);</p>
<p>path(i,j)=path(i,k);</p>
<p>end,</p>
<p>end,</p>
<p>end,</p>
<p>end</p>
<p>if nargin==3</p>
<p>min1=D(start,terminal);</p>
<p>m(1)=start;</p>
<p>i=1;</p>
<p>path1=[ ];</p>
<p>while path(m(i),terminal)~=terminal</p>
<p>k=i+1;</p>
<p>m(k)=path(m(i),terminal);</p>
<p>i=i+1;</p>
<p>end</p>
<p>m(i+1)=terminal;</p>
<p>path1=m;</p>
<p>end</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>a= [ 0,50,inf,40,25,10;</p>
<p>50,0,15,20,inf,25;</p>
<p>inf,15,0,10,20,inf;</p>
<p>40,20,10,0,10,25;</p>
<p>25,inf,20,10,0,55;</p>
<p>10,25,inf,25,55,0];</p>
<p>[D, path]=floyd(a)</p></td>
</tr>
</tbody>
</table>

![image3](../../assets/b8de2eb3610c4a64b387a4b91faf8497.png)

路程：D（2,5）+D（4,5）=30+10

二，Dijkstr与Floyd对比
输入
\[0 8 Inf Inf Inf Inf 7 8 Inf Inf Inf;
Inf 0 3 Inf Inf Inf Inf Inf Inf Inf Inf;
Inf Inf 0 5 6 Inf 5 Inf Inf Inf Inf;
Inf Inf Inf 0 1 Inf Inf Inf Inf Inf 12;
Inf Inf 6 Inf 0 2 Inf Inf Inf Inf 10;
Inf Inf Inf Inf 2 0 9 Inf 3 Inf Inf;
Inf Inf Inf Inf Inf 9 0 Inf Inf Inf Inf;
8 Inf Inf Inf Inf Inf Inf 0 9 Inf Inf;
Inf Inf Inf Inf 7 Inf Inf 9 0 2 Inf;
Inf Inf Inf Inf Inf Inf Inf Inf 2 0 2;
Inf Inf Inf Inf 10 Inf Inf Inf Inf Inf 0;\];

Dijkstr
![image4](../../assets/0c2164da9e8a4b46bfe319fb70bda84f.png)

Floyd
![image5](../../assets/98d6855952b0458299c762e442cc0b9c.png)
![image6](../../assets/5a721ab37fb54667ab9d441039928f63.png)

