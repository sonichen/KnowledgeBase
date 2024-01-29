---
title: Recursion
updated: 2020-08-10T14:10:47.0000000+08:00
created: 2020-08-09T21:30:42.0000000+08:00
---

## 一、Recursion
1,A predicate is recursively defined if **one or more rules in its definition refers to itself**
2,example
\(1\)
![image1](../../assets/03684fab6c864ab9babec62fa1eb0169.png)
\(2\)
![image2](../../assets/399df12f22d94405a528f4c9e92233d0.png)
\(3\)
![image3](../../assets/2b4b3dbd42d7451a87f47a34d9e8e3ac.png)
\(4\)
![image4](../../assets/64494eccf8564c3486f26ebe1b90c91e.png)
\(5\)
![image5](../../assets/45840be52e5743c2bc4cf04e6add5119.png)
（6）
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>child(anna,bridget).</p>
<p>child(bridget,caroline).</p>
<p>child(caroline,donna).</p>
<p>child(donna,emily).</p>
<p>descend(X,Y):- child(X,Y).</p>
<p>descend(X,Y):- descend(Z,Y), child(X,Z).</p>
<p>？-descend(A,B).</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
![image6](../../assets/2c0bd44162a14a9e8695eb12ffcce317.png)
## 二、Prolog and Logic 
1,Prolog was the first reasonable attempt to create a logic programming language
2,特点
not have to tell the computer what to do
To get information, simply asks a query
Prolog is not a full logic programming language!

