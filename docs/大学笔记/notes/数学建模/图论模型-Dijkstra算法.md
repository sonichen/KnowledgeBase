---
title: '图论模型-Dijkstra算法 '
updated: 2024-01-29T12:38:25.0000000+08:00
created: 2020-11-12T09:51:00.0000000+08:00
---

图论模型-Dijkstra算法
2020年11月12日
9:51

需求；找到最小路径
![image1](../../assets/298fe3f979cc4b678854a21aa02f6f94.png)

一、Dijkstra算法
1，能求一个顶点到另一顶点最短路径。
Dijkstra算法是一种标号法：给赋权图的每一个顶点记一个数，称为顶点的标号（临时标号，称T标号，或者固定标号，称为P标号）。T标号表示从始顶
点到该标点的最短路长的上界；P标号则是从始顶点
到该顶点的最短路长。

2，步骤
![image2](../../assets/27e9e4ff8a984594a77579c34120663e.png)

![image3](../../assets/fa971661f8404acda0086ded72766cc0.png)

结果
![image4](../../assets/710213ab6cec4b99bed3c70e5b2cea69.png)

三、实现
1，带权邻接矩阵
注意无向和有向
无向
![image5](../../assets/6ba1174e3b5840109a8520a7a523ccf0.png)

有方
![image6](../../assets/d8bf1e45ba6e47f5b53d421ebd79bda8.png)

2，代码

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>function [min,path]=dijkstra(w,start,terminal)</p>
<p>n=size(w,1); label(start)=0; f(start)=start;</p>
<p>for i=1:n</p>
<p>if i~=start</p>
<p>label(i)=inf;</p>
<p>end, end</p>
<p>s(1)=start; u=start;</p>
<p>while length(s)&lt;n</p>
<p>for i=1:n</p>
<p>ins=0;</p>
<p>for j=1:length(s)</p>
<p>if i==s(j)</p>
<p>ins=1;</p>
<p>end,</p>
<p>end</p>
<p>if ins==0</p>
<p>v=i;</p>
<p>if label(v)&gt;(label(u)+w(u,v))</p>
<p>label(v)=(label(u)+w(u,v));</p>
<p>f(v)=u;</p>
<p>end,</p>
<p>end,</p>
<p>end</p>
<p>v1=0;</p>
<p>k=inf;</p>
<p>for i=1:n</p>
<p>ins=0;</p>
<p>for j=1:length(s)</p>
<p>if i==s(j)</p>
<p>ins=1;</p>
<p>end,</p>
<p>end</p>
<p>if ins==0</p>
<p>v=i;</p>
<p>if k&gt;label(v)</p>
<p>k=label(v); v1=v;</p>
<p>end,</p>
<p>end,</p>
<p>end</p>
<p>s(length(s)+1)=v1;</p>
<p>u=v1;</p>
<p>end</p>
<p>min=label(terminal); path(1)=terminal;</p>
<p>i=1;</p>
<p>while path(i)~=start</p>
<p>path(i+1)=f(path(i));</p>
<p>i=i+1 ;</p>
<p>end</p>
<p>path(i)=start;</p>
<p>L=length(path);</p>
<p>path=path(L:-1:1);</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>执行代码</td>
</tr>
<tr class="even">
<td><p>weight= [0 2 8 1 Inf Inf Inf Inf Inf Inf Inf;</p>
<p>2 0 6 Inf 1 Inf Inf Inf Inf Inf Inf;</p>
<p>8 6 0 7 5 1 2 Inf Inf Inf Inf;</p>
<p>1 Inf 7 0 Inf Inf 9 Inf Inf Inf Inf;</p>
<p>Inf 1 5 Inf 0 3 Inf 2 9 Inf Inf;</p>
<p>Inf Inf 1 Inf 3 0 4 Inf 6 Inf Inf;</p>
<p>Inf Inf 2 9 Inf 4 0 Inf 3 1 Inf;</p>
<p>Inf Inf Inf Inf 2 Inf Inf 0 7 Inf 9;</p>
<p>Inf Inf Inf Inf 9 6 3 7 0 1 2;</p>
<p>Inf Inf Inf Inf Inf Inf 1 Inf 1 0 4;</p>
<p>Inf Inf Inf Inf Inf Inf Inf 9 2 4 0;];</p>
<p>[dis, path]=dijkstra(weight,1, 11)</p></td>
</tr>
</tbody>
</table>

![image7](../../assets/ab69128033d542c696ddc528b3a17fa1.png)

