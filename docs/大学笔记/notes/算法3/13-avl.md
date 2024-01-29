---
title: 13-avl
updated: 2024-01-29T12:20:40.0000000+08:00
created: 2021-06-07T17:47:01.0000000+08:00
---

为了解决：我们观察到，BST的最坏情况下的性能最接近线性搜索算法，即Ο(n)的问题而产生AVL
![image1](../../assets/8c566fb11f494cc19eeb7d0ca84f5377.png)

## 一、AVL Tree 
1，Balanced Binary Tree
具有n个节点的二元搜索树的缺点是，它的高度可以高达n-1。
![image2](../../assets/1c33ca32f6364d3a880bdbc0acad55a9.png)

2，AVL
1）概念
平衡二叉树AVL=平衡二叉树+（平衡因子\<=1）
**AVL树是带有==平衡条件==的==二叉查找树==**
特点：**任意结点的平衡因子的绝对值不超过1**
<u>平衡因子=左子树高度-右子树高度</u>
<u>BF =height(left subtree) – height(right subtree)</u>
![image3](../../assets/0cfe322677ca48a085317d2adae95cf8.png)
案例
![image4](../../assets/ebac4a636521446dbfbf20ce7738ec66.png)
案例
![image5](../../assets/c77ce08a0c1a42009e1a868c02c356f2.png)
目的
![image6](../../assets/309e4f6b9e6442d4bc2ecdd289eb93f3.png)

利弊
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>• Pros and Cons of AVL Trees</p>
<p>1. 搜索，插入和删除是O(log n)。</p>
<p>2. 高度平衡增加不超过一个恒定因素的插入速度。</p>
<p>1. Search, insertion and deletions are O(log n).</p>
<p>2. The height balancing adds no more than a constant factor to the speed of insertion.</p>
<p></p>
<p>• Arguments against using AVL trees:</p>
<p>1. 难以编程和调试;</p>
<p>需要更多的空间来平衡因子。</p>
<p>2. 渐近更快，但再平衡需要时间。</p>
<p>3.大多数大型搜索是在磁盘上的数据库系统中完成的，并使用其他结构(例如b -树)。</p>
<p>4. 如果多个连续操作的总运行时间很快(例如展开树)，那么单个操作的运行时间为O(N)是可以的。</p>
<p></p>
<p>1. Difficult to program and debug; need more space for balance factor.</p>
<p>2. Asymptotically faster but rebalancing costs time.</p>
<p>3. Most large searches are done in database systems on disk and useother structures (e.g. B-trees).</p>
<p>4. May be OK to have O(N) for a single operation if total run time for many consecutive operations is fast (e.g. Splay trees).</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## 二、Rotation 
插入node
如果==左右子树的高度差大于1==，则使用一些==旋转技术对树进行平衡==。
为了平衡自身，AVL树可以执行以下四种旋转−

### 1，Left rotation
**LL平衡旋转（右单旋转）**
原因：在结点A的**左孩子的左子树**上插入新结点
调整方法：右旋操作：将A的左孩子B代替A，将A结点称为B的右子树的根节点，而B的原右子树作为A的左子树【把B拎起来，A下去，B的右子树称为A的左子树】
![image7](../../assets/22d39bd78d8f467fbdf471ff1b00035e.png)
案例
![image8](../../assets/e12ee094671e494986cd7e24c5594a42.png)

![image9](../../assets/19397cf6574444918726a4518dd09868.png)

![image10](../../assets/93aaecce659e4f7097212d748a603037.png)

### 2， Right rotation 
**RR平衡旋转（左单旋转）**
原因：在结点A的右孩子的右子树上插入了新结点
调整方法：左旋操作：将A的右孩子B代替A，将A结点称为B的左子树根节点，而B的原左子树作为A的右子树【把B拎起来，A左边放下去，把B的左子树给A的右子树】
![image11](../../assets/4f881c97a2f148c597acb035fb4546f7.png)

![image12](../../assets/8716caff02844d3380d95e6a0ceaa0d9.png)

![image13](../../assets/b1fd7cbe809849c090a3f08c5fe6a633.png)

![image14](../../assets/4ea5197ced1f44a082adc8db547e2a10.png)

如何定位A,B?
A就是==距离插入点最近==，且==平衡因子不平衡==的那个点

案例
![image15](../../assets/a06556576c6849f8a002d41de0308d0e.png)

![image16](../../assets/320f0e32eadb4d0f80c9a3a1cb568ddd.png)

![image17](../../assets/b58b5481006040ada4826ef53f8a048a.png)

![image18](../../assets/d78846b519ca433dbefab4ab939e0dc5.png)

![image19](../../assets/4bba6c4641c3427187e92fbf90593bfe.png)
不，要LR选择

![image20](../../assets/39bd9a33d96f4ac284231155b28bc802.png)

### 3，Left-Right rotation 
**LR平衡旋转（先左后右双旋转）【先对B左旋，C领上来，再对C右旋】**
原因：在结点A的左孩子的右子树上插入新的节点
调整方法：先左旋转在右旋转：将A的左孩子B的右孩子C代替B，再将C向上代替A
![image21](../../assets/8b9ff61feeb948a091ec491889114028.png)

![image22](../../assets/a92fde965fed4363b94db61edae38802.png)

![image23](../../assets/74bce814f66045bebed1f90b66fef4f3.png)

案例
![image24](../../assets/1c46ea6c90454c91ba02d1685e1edcc1.png)

### 4，Right-Left rotation
**RL平衡旋转（先右后左双旋转）**
原因：在结点A的右孩子的左子树上插入了新结点【对B右旋转，把C提上来，再对C左旋转，把C上来】
调整方法：先右旋转再左旋转，将A的右孩子B的左孩子结点C代替B，再将C结点上调至A的位置

![image25](../../assets/e742d09d154f4bf792dc2452cb016b03.png)

## 三、在操作时，调整平衡因子
### 1，插入
• Insert
新节点总是作为叶节点插入，平衡因子等于0。
![image26](../../assets/18bfa62d7e8246fc851e49dd2c965c25.png)

插入步骤
1，转到相应的叶节点，以使用以下递归步骤插入新节点。比较当前树的newKey和当前树的rootKey。
1）如果newKey\<rootKey，在当前节点左子树上调用插入算法，直到到达叶节点。
2）否则，如果是newKey\>根键，则在当前节点的右子树上调用插
入算法，直到到达叶节点。
3）Else, return leafNode
4）更新平衡因子，做调整
![image27](../../assets/3800c51e94a145ea9e5c32c6ef5d916b.png)

![image28](../../assets/c32e7dd0e41b413e82a71f91e9b42057.png)

![image29](../../assets/f4c9180f97234fd38549a95af80b5bd4.png)

![image30](../../assets/96f3bf9c31f14031b9ddfa10026d4a92.png)

![image31](../../assets/4da9f869c0b046c1aa2c967abbf126bd.png)

![image32](../../assets/3664f05e34ab44889ccf8b8c772c9d1a.png)

### 2，删除
• Delete
==先按照BST要求删除节点，在调整平衡因子==
一个节点始终作为一个叶节点被删除。删除节点后，节点的平衡系数会发生更改。为了重新平衡平衡因子，我们进行了适当的旋转。

三种情况
1，如果没有删除是叶节点。没有任何子级)，然后删除未删除。
2，如果未删除有一个子项，则将未删除的内容替换为子项的内容。删除该子项。
3，如果没有被删除的人有两个子级，请找到没有被删除的人的顺序继承者w。在右侧子树中具有最小键值的节点）。
用未删除的内容替换为w的内容。

删除叶子节点w
![image33](../../assets/3fb01094f957428aa7942a652f9f3e36.png)

![image34](../../assets/e095278611c04762885994d4e98d1424.png)

4，更新节点的平衡系数。
![image35](../../assets/2afc7b5957244ae7bcf2887c23406609.png)

5，
![image36](../../assets/48bb702c342f4ce580610678c0231fc0.png)
![image37](../../assets/4eee1c56286d4089b6c94b9db950f476.png)

• Max and Min
1，最小--》最左边
![image38](../../assets/a326bdd842a0449094b13a5c1abb5cf4.png)

• Complexities of Different Operations【重点】

![image39](../../assets/02bd4f2da76d4f31b587445626b38087.png)

![image40](../../assets/9d458b15518e45dab1b4deb41735ff2d.png)

![image41](../../assets/5ec6857868d64c7eb6a8f17fbe5f3790.png)

## 四、计算高度和点数

一个高度为h的AVL
| 最少放 | ![image42](../../assets/b3d3d617635e41c4aa4f55995f8437aa.png)    |
|--------|-------------------------------------------------------------------------------------------------------------------------|
| 最多放 | ![image43](../../assets/58b5e8dcc9114f6a8ce64d9661f1394f.png) |
补充斐波那契数列
![image44](../../assets/e9f412d75ad743d3bed5e2088538603c.png)
案例
![image45](../../assets/3b1f3029dcdd441bbd39f91340e99a8d.png)
<table>
<colgroup>
<col style="width: 17%" />
<col style="width: 82%" />
</colgroup>
<thead>
<tr class="header">
<th>最少放</th>
<th><p>F5-1=5-1=4</p>
<p>![image42](../../assets/b3d3d617635e41c4aa4f55995f8437aa.png)</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>最多放</td>
<td>![image46](../../assets/d8e0f96020d149a1b70d1626c32d7784.png)</td>
</tr>
</tbody>
</table>

案例
| 高度是4的avl数，有可能放50个点吗                                                                                        |
|-------------------------------------------------------------------------------------------------------------------------|
| ![image47](../../assets/17ed65389d7743df9b92027b71d54b39.png) |

![image48](../../assets/1e6272f3b707461789700caf480a2fdc.png)

![image49](../../assets/79f5b0f8374c4c3f84a2525f7aa04272.png)

![image50](../../assets/decd803f4ef640e19a903373515e31f4.png)

补充：
高度为h的最小平衡二叉树的结点数Nh (最小--》结点最少)

![image51](../../assets/90d437828b504738bcad15cb37e57997.png)
![image52](../../assets/26dfc52063284a85930632f6ce86f917.png)

分析过程
- 为什么左子树Nh-1?---\>保证树的高度为h
- 右子树分析
![image53](../../assets/6f8f31af65a3467a80de604abc8226ab.png)

![image54](../../assets/7d9590ee4e3d495ba17ca57d0e2dc654.png)
