---
title: 6-First Order Logic (Part 2)
updated: 2021-12-21T21:52:40.0000000+08:00
created: 2021-12-08T23:07:48.0000000+08:00
---

1，Terms
![image1](../../assets/3280f14b624b4455a596276282759517.png)
![image2](../../assets/3a35b06cf32a4fb094c483d6e9f257ad.png)
![image3](../../assets/2a4e3966f6014fa2af7a56dae554c618.png)
==例子==
![image4](../../assets/5de66764bada421a81cc3b73f65c851c.png)

2，**Formulae** of Predicate Logic
![image5](../../assets/5dc363b8a9164f7093718656653814ca.png)

![image6](../../assets/ed2020df807f4f09a6abb2e555d16ad4.png)

3，parse trees
用来表示predicate logic formulae
![image7](../../assets/4111ce1eea79475180659367beadea0c.png)

==不懂==
![image8](../../assets/62560203c4554f789085acef28c4c9de.png)

4，Scope
量词∀和∃的证明规则涉及到操作变量。
这里重要的是确保不会导致变量不适当地更改其作用域。
我们编写𝑖∶𝑆来表示在证明的一部分中引入了一个𝑆类型的变量𝑖。

在书面证明中，我们还在我们使用变量𝑖的行周围放置了一个方框，这样我们就可以跟踪它的范围。

==5，Free and Bound variables==

![image9](../../assets/3a3fa79cfb18447eaad26dc1dd0a2c79.png)
![image10](../../assets/85115a0313fe4f9e8c724b40841eb6f1.png)

==6，substitution==

替换：给定一个变量𝑥、术语𝑡和公式𝜙，我们将𝜙\[𝑡/𝑥\]定义为用𝑡将𝜙中变量𝑥自由出现的每次替换得到的公式。
![image11](../../assets/71a882dfc7e84fd2917e299085307c5c.png)

![image12](../../assets/0f98b38cef39400b84dbe82913ead133.png)

![image13](../../assets/e77bf4fb5c434b2e9e9b2323f3ae8f49.png)

![image14](../../assets/9fe7f58f2b164b15a850b4631a7058d8.png)

7,Natural Deduction Proof Rules for Predicate Logic
证据与命题逻辑的证据相似
添加了证明规则来处理量词（引入和消除规则）和相等符号。
我们超载了先前建立的命题连接词∧，∨，...的证明规则，因此任何命题逻辑的证明规则对于谓词逻辑的逻辑公式仍然有效

8,Natural Deduction Proof Rules: Equality
![image15](../../assets/fa0c3003a9364a558119187874b12ec8.png)

9,Proof rules for forall
![image16](../../assets/08de8713118b4ef2be66d815eb01ff38.png)

10, Proof rules for exists

![image17](../../assets/5865c72ac4904f3ca4b3d4cff5ca7738.png)

