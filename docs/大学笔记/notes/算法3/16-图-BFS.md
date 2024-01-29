---
title: 16-图-BFS
updated: 2024-01-29T12:23:52.0000000+08:00
created: 2021-07-05T20:07:16.0000000+08:00
---

## • Breadth First Search 

1，定义：(BFS)算法在BFS中遍历图形，并在任何迭代中出现死胡同时，使用队列记住让下一个顶点开始搜索
队列**First-In-First-Out system (FIFO)**

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><h2 id="算法">算法</h2>
<p>标准的BFS实现将图的每个顶点放为两类之一</p>
<p>• Visited</p>
<p>• Not Visited</p>
<h2 id="section"></h2>
<p>该算法的目的是将每个顶点标记为已访问的，同时避免循环</p>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>1.首先，将图的任何一个顶点放在队列的后面。</p>
<p>2.获取队列前面项目，并将其添加到访问列表中</p>
<p>3.创建该顶点的相邻节点的列表。将不在已访问列表中的那些列表添加到队列的后面。</p>
<p>4.继续重复步骤2和步骤3，直到队列为空</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
## 
![image1](../../assets/77bcf0ff3b304b5d9cd57ef0ff5fd3dc.png)

案例
![image2](../../assets/1c88d8f96d204379835cbae9e001fb7f.png)

## 
## 
## 案例
![image3](../../assets/311bb41efe3d4bb28d1eb2370c7d6cb0.png)
## 
![image4](../../assets/f9f3a35994f64cbc8a07e53a0bf2ebbb.png)
## 
## 时间复杂度
BFS算法的时间复杂度以O(V+E)的形式表示，其中V是节点数，E是边数。
该算法的空间复杂度为O(V)。
## 
## 

