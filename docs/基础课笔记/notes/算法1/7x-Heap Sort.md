---
title: 7x-Heap Sort
updated: 2021-01-09T19:14:58.0000000+08:00
created: 2020-12-26T20:20:07.0000000+08:00
---

叶子结点 就是出度为0的结点 就是没有子结点的结点
近二叉树：不能满的二叉树
一、binary tree
1，binary tree
![image1](../../assets/de0fb07a11084ae5a272c40f9a700ba7.png)

2，Complete Binary Tree
定义：完备二叉树是指除了最后一层之外的每一层都是满的，并且所有节点都在尽可能远的左边的二叉树

堆：完全二叉树+父节点\>子节点（父节点\<子节点）
| max heap | 父\>子 |
|----------|--------|
| Min heap | 父\<子 |
. The heap can be represented by a binary tree or array.

3，Heap Property
3.1 a nearly complete binary tree with “heap property”:父节点\>两个子节点
注意序号
3.2
![image2](../../assets/79e67fac193d46848549625fac8bc462.png)
从一开始

4，Tree
height：从下往上；
depth：从上往下
![image3](../../assets/90850114032c4b71855122fe5fdd9ac8.png)

5，binary tree facts
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image4](../../assets/bb60ae89dbbb42f994d494ab58b05164.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>![image5](../../assets/95f90653531845dcbd51b3ef64a7da67.png)</p>
<p></p></td>
</tr>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image6](../../assets/50b34c644f0f4eadaff13e89cc5520cd.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>![image7](../../assets/773b83b36ab04b1c93d76cbf3d59dda0.png)</p>
<p></p></td>
</tr>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image8](../../assets/db9eda9f236941dc97f366f45f6b0633.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>![image9](../../assets/27e3e2da4ece4fdc8702d51abe5e95ef.png)</p>
<p></p></td>
</tr>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image10](../../assets/727c5d8a7759430895bb7dc6497d2a78.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
</tr>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image11](../../assets/4efaf9c6daa24b8a8d6f65274992a3a3.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
</tr>
</tbody>
</table>

数学公式
![image12](../../assets/0eb17b1b38b0405aa3660397c3624e5f.png)

![image13](../../assets/f14a2b6776884cacaa34e54111a14591.png)

二、Heap Sort  
1，
![image14](../../assets/882c3c8b85464ea583d03f4f5b5ebc88.png)

2，HEAPIFY\[调整为heap tree\]
<table>
<colgroup>
<col style="width: 34%" />
<col style="width: 33%" />
<col style="width: 31%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image15](../../assets/1feec142dfb545fa9fa5682cdaff067a.png)</p>
<p></p></th>
<th><p>![image16](../../assets/b8aec7b4adf748e8af9bc756f937af06.png)</p>
<p></p></th>
<th><p>![image17](../../assets/6ebe15fa1b2e452e83d9271a7f6dc484.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

步骤
A is a heap
1，把A中最大的放到B
2，把最小的放到A\[1\]
3，调整剩余的node，【除了当前最大的】，直到满足heap 性质
4，重复1-3步直到A空
5，B就是从大到小排列好的数组

3，两个缺点
1，need a lot of extra space=O(1)

2,移动元素后的tree很可能不满足堆性质

![image18](../../assets/bf300805df4140baa8d3dbcd3b3fc862.png)
4，heapify例子
<table>
<colgroup>
<col style="width: 32%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image19](../../assets/b343f96efff2460aa7c927dc94eaa4b4.png)</p>
<p></p></th>
<th><p>![image20](../../assets/41e4866d1fb24671af17bf0c7278c222.png)</p>
<p></p></th>
<th><p>![image21](../../assets/09271f9013f844a284d9246d9dd4cc99.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

5，时间复杂度
<table>
<colgroup>
<col style="width: 41%" />
<col style="width: 58%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image22](../../assets/c988234c57404be2b62a2b273757bbdf.png)</p>
<p></p></th>
<th><p>![image23](../../assets/fd5aa43dd75c45b78543bb9b4095c958.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
6，construct a heap tree
![image24](../../assets/a25cac009f414fbd9f2fa4c054705cb3.png)
方法1：top-down O(nlgn)
Extend the heap tree by add nodes one by one
从上至下,从左到右，一边加点一边调整结构
![image25](../../assets/b0c412e02d614f92a3e962f3180c4ebd.png)
Then we add A\[X\] to this tree and do "floating up"

![image26](../../assets/d44bb6fa31054fd3bb484d17a29abac3.png)

方法2：bottom up O(n)
从下往上，从右到左，开始构建
Use bottom up to construct heap ➔ 𝑂(𝑛)
![image27](../../assets/a01fec35fadd4395bd29ca1eba17eda5.png)

![image28](../../assets/d7e61d9e5a344d059c605e5e6c5e8a41.png)

时间复杂度：  

![image29](../../assets/373a4d4ea49542b5b54a0aade25c139a.png)

![image30](../../assets/1c70e9443df14437b993e5193420a56f.png)

![image31](../../assets/b70096cd4da84f14b53ab650d9276734.png)

7，堆排序时间复杂度
![image32](../../assets/7df8a51055ba403f83a31ce8bcaee746.png)

三、Priority queue
![image33](../../assets/db828d32b9934cc488c7d489df5c0d63.png)

![image34](../../assets/ef6cd0e7aa5c45e1825ce53c7f122542.png)

