---
title: L4-logic for program specification part2
updated: 2021-12-21T21:02:37.0000000+08:00
created: 2021-12-07T17:30:08.0000000+08:00
---

1，Natural deduction proof rules for AND
1）==看不懂==
![image1](../../assets/15e23d9cc2054db293e7de8e9be43146.png)

![image2](../../assets/465fe6b0c09f43aaaf0115b41fe02d60.png)

2）Proof tactics in Coq for conjunction (AND)
至于implication，我们有两种处理Coq中的结合的证明策略：
![image3](../../assets/cb3901e7a340489280300778dfd2386c.png)

2，Natural deduction proof rules for EQUIVALENCE
![image4](../../assets/de0e5bab4d194ee4a9ce4cdc00be676c.png)

3，Natural deduction proof rules for OR
![image5](../../assets/a483e9c58a1f44809c21435000685c73.png)

![image6](../../assets/21e7f846afc440feaf29ad2ab88483be.png)

![image7](../../assets/a1376f01b6f44fc88edc77e3baf7032a.png)

4，Natural deduction proof rules for negation
2种
Constructive logic构造逻辑认为**~P**只是**P-\>False**的缩写——也就是说，如果我们曾经要证明P，那么我们将证明一些不可能是真的东西（即假的）

Classical logic经典逻辑有一个“更强”的版本，它本身对待否定，允许通过矛盾来证明
![image8](../../assets/a2591edef3dd481492cb5d47ad691539.png)

5，Natural deduction proof rules for False
![image9](../../assets/de977bab64c14ab5bff276fc71c90e84.png)

![image10](../../assets/c0dba5fda1684711aacb67358c503b60.png)
6，Proof tactics in Coq for False
![image11](../../assets/b8a12701e6414558b73f7dd95ec5bb5a.png)

7，classical logic
在经典逻辑中，我们假设每个命题都是对的或假的，即使我们不能单独证明这两者。

The core rule for classical logic is the Law of the Excluded Middle
![image12](../../assets/3594119758bd4aa99e7797c6aeb54383.png)

经典逻辑是建设性逻辑的扩展：如果一个经典的证明不使用LEM（或它的结果），那么它就是“建设性的”。

==8，Consequences of LEM==
一旦我们进入经典逻辑(当我们假设LEM时)，其他“非建设性”结果自然会随之而来。
![image13](../../assets/a05bfe46b58c4948b9fa5734f65f9b58.png)

==9，WFF Well Formed Formulae==
![image14](../../assets/bd02ae6dad8c4cf6b600dbef0926a6b0.png)

![image15](../../assets/40649de00cb84c08a602f6ad1a40b12a.png)

看看语法规则，反转构建公式的过程（反演原理）

