---
title: 12-Binary Search Tree
updated: 2024-01-29T12:19:32.0000000+08:00
created: 2021-06-05T09:59:38.0000000+08:00
---

12-Binary Search Tree
2021年6月5日
9:59

## 一、认识二叉树

1，二叉树和二叉搜索树
二叉树是一种递归数据结构，其中每个节点最多可以有两个子级。
==binary search tree：节点的值≥左子节点，节点的值≤右子节点，左小右大==

案例
![image1](../../assets/42367aed2d404ee39e20eb3d7db6d288.png)

2，Binary Search Tree
| 最大的值 | 最右边的节点 |
|----------|--------------|
| 最小的值 | 最左边的节点 |

![image2](../../assets/9a1f2a3faa2545b6b0f5083cd86ba61e.png)

3，搜索的时间复杂度
![image3](../../assets/a9db217e8e5e424d9d5f66b3a9380e36.png)

## 二、增删操作

准备
a.排列
![image4](../../assets/1246685990ce4e2bbd5e2bdfce9c661d.png)
b.节点
![image5](../../assets/a68d79d823ac480cad708bdf64be99c1.png)

c.创建树并加入root【add the starting node of our tree】
![image6](../../assets/c5390898aaff46888d931eddfb83a520.png)

### 1，Inserting Elements 
A.步骤
1），我们必须找到要添加新节点的位置，以保持树的排序
2），插入规则
如果新节点的值==低于当前节点的值==，则转到==左子节点==
如果新节点的值==大于当前节点的值==，则将转==到右子节点==
==当前节点为空时==，我们已到达一个叶节点，我们可以在该位置插入新节点

B.代码
案例：请自己画一遍
![image7](../../assets/3764ffae43c3406a96fde618447443e0.png)
案例
![image8](../../assets/7c7c9149335640a3a7fed5687070364b.png)

### 2，Finding an Element 
A.步骤
在这里，我们通过将其==与当前节点中的值进行比较==，如果小于当前值，向左子树搜索，如果大于当前值，向其右子树搜索
B.代码

### 3，Deleting an Element 
步骤
先找到它,再删除它,再调整它
注意
一旦找到要删除的节点，主要有3种不同的情况：
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>1. 节点没有子节点，这是最简单的情况；我们只需要用空的父节点替换该节点</p>
<p>2. 节点正好有一个子节点—在父节点中，我们用其唯一的子节点替换该节点。</p>
<p>3. 一个节点有两个子节点——这是最复杂的情况，因为它需要重组树</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

![image9](../../assets/8a9311f5379542ddbd4c46bf7222710f.png)

4，implementation的时间复杂度
![image10](../../assets/cd88cb139dab45718745c3769f89d0f1.png)

三、遍历操作
• Tree Traversal
前序遍历是：==根==、左、右

中序遍历是：左、==根==、右

后序遍历是：左、右、==根==

![image11](../../assets/2495098a148f47e5abc83634c82a9c97.png)

==• In-order Traversal 当前节点中间==
步骤
步骤1−递归遍历左子树。
步骤2−访问根节点。
步骤3−递归遍历右子树。

案例
![image12](../../assets/34a7d5617cae4c80abe52662529967e0.png)

代码

==• Pre-order Traversal 当前节点先==
步骤1−访问根节点。
步骤2−递归遍历左子树。
步骤3−递归遍历右子树。

案例
![image13](../../assets/626409f1e9ea4af68772cad6dfa85049.png)

代码

==• Post-order Traversal当前节点最后==
• Note. Data structure: stack
步骤
步骤1−递归遍历左子树。
步骤2−递归遍历右子树。
步骤3：−访问根节点。

案例
![image14](../../assets/90fb09979e36420583f12618d6c128b7.png)
代码
![image15](../../assets/e9f5b34f7b3842a795055abed3e0f03a.png)

==Level-Order Traversal==
1，uses a queue to keep track of nodes to visit
级别顺序遍历使用队列来跟踪要访问的节点。访问节点后，其子节点将被放入队列中。要历一个新节点，我们从队列中取出元素。
,2，算法步骤
![image16](../../assets/a2543719c49e4b48905bedefa834ebf2.png)

案例
![image17](../../assets/422312386b764b58b67d5de3f1d71030.png)

代码

