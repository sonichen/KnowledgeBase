---
title: 20-N&NP&NPC
updated: 2024-01-29T12:29:12.0000000+08:00
created: 2021-07-01T12:16:59.0000000+08:00
---

• P vs. NP
• NP-complete
• co-NP
• NP-hard

## 一、P vs. NP 
1，P,NP
P：用==确定性多项式算法==可以解决的一类问题。
NP：用==非确定性多项式算法==可以解决的一类决策问题。
NP-hard：每个NP问题都被简化为的一类问题
NP-complete (NPC): NP-hard和NP的交集
![image1](../../assets/a2ea2d5d21fa44e58b589d9218c62a5d.png)

2，Decision Problems
![image2](../../assets/4642395f87ac4cfb8f5fc64f5d2d90bd.png)
决策问题。解决方案只是“是”或“否”
而==优化问题则比较困难Optimization problems==
![image3](../../assets/d347580826e94bf680faad8ab980ab52.png)

3，P
![image4](../../assets/e6695bb16eb343cab8a4eaaa38cfa646.png)

4，NP
Decision problems for which there is a poly-time certifier
存在多种时间认证器的决策问题
![image5](../../assets/0ceda97b4f6d4e519565d718bf87bbf3.png)

• Certification algorithm intuition.
Certifier从“管理”的角度来看待事物。

Certifier自己<u>不能确定S∈</u>X；相反，它检查==一个提议的证明t，s∈X==
![image6](../../assets/428dc2772ec643798427e9efe70f6935.png)

![image7](../../assets/02f84546e6e34a76ae94a7c3df6ffc7d.png)

给定一个CNF公式Φ，有一个令人满意的分配吗？
![image8](../../assets/558167bde7a949619fdc1359f5e69b14.png)

给定一个无向图G=(V、E)，是否存在一个访问每个节点的简单路径P？
![image9](../../assets/fc4e230063c24860908b556076ce6194.png)
检查排列是否恰好包含V中的每个节点一次，并且每对相邻节点之间是否有一条边

5， P, NP, and EXP
• P. Decision problems for which there is a poly-time algorithm.
• NP. Decision problems for which there is a ==poly-time certifier.==
• EXP. Decision problems for which there is ==an exponential-time algorithm==

![image10](../../assets/77268e1116be4d39b564ebca1d59a9cf.png)

![image11](../../assets/02b5bf0f94414e6db21129f1640b0fad.png)
6,P, The main question: P vs. NP
P是否等于NP
![image12](../../assets/8e08e3cf87bf4c799d205ee16ec3dff6.png)

![image13](../../assets/cd95ebd0e783415eabebd3fd0f07c910.png)
二、NP-complete
1，多项式转换
Definition.
如果问题X的任意实例可以用来解决，问题X多项式(Cook)将简化为问题Y：

标准计算步骤的多项式数，加上

解决问题Y的oracle的多项式数。

定义
问题X多项式(Karp)转换为问题Y，如果给定任何输入x到X，我们可以构造一个输入y，使x是X的yes实例，当且仅当y是Y的yes实例

我们要求\|y\|在\|x\|中是多项式的大小的

注意：
多项式变换是多项式约简，只有对Y的oracle的一个调用，正好在X算法的末尾

几乎所有的化简都是这种形式。

开放性问题：这两个概念对于NP是相同的吗？
![image14](../../assets/036c247c5fd34e26ae23f9c2d4932baf.png)

2，NP-complete
定义
![image15](../../assets/57f8e8d057b943388aed24add20aab1a.png)

Definition of reduction:
当且仅当问题B(A≤pB)，当A可以用确定性多项式时间算法求解时，问题A才简化为问题B(A≤pB)。

3，Reduction
到目前为止，在最坏情况下，确定性多项式时间算法都不能解决任何NPC问题。
它似乎没有任何多项式时间算法来解决NPC问题。
The theory of NP-completeness always considers the worst case
任何NPC问题的下界似乎都是一个指数函数的阶数。
并不是所有的NP问题都很困难。(e.g.MST问题是一个NP问题。)
![image16](../../assets/b885464966bb430ba96df46f9953afbb.png)

4，N=NP?(重点
![image17](../../assets/ab24cc18e1a046c5a05e7f924faa7a20.png)

5，Cook’s theorem
NP = P iff the satisfiability problem is a P problem
• SAT is NP-complete.
• Every NP problem reduces to SAT.

6，Circuit satisfiability
给定由D、或和非门构建的组合电路，有没有方法设置电路输入以使输出为1？
![image18](../../assets/a7c4b98c47104b3caab5ebda4a81a399.png)

7，
![image19](../../assets/af478f7b893047d7aceea05f190031c2.png)

8，Proof of NP-Completeness（重点
![image20](../../assets/3febec821f18403f9c359cfbaab98129.png)

![image21](../../assets/65457b2ccf124cb1b129f8690bd993fd.png)

![image22](../../assets/dc89cfbea2494b5f85d04c9ef0707b35.png)

9，3-satisfiability is NP-complete

三、co-NP
1，Asymmetry of NP
NP的不对称信息
我们只需要有是的实例的简短证明。
![image23](../../assets/89b3146153ce4cd19c681a97b98cb009.png)
2，NP and co-NP

3，Good characterizations
![image24](../../assets/8fee924843e246cd8fce2377170da0b0.png)

四、NP-hard
1，A note on terminology: consensus
NP-complete
NP中的一个问题，使得NP多时中的每一个问题都简化为它。
NP-hard. \[Bell Labs, Steve Cook, Ron Rivest, Sartaj Sahni\]
一个使NP多项式时间中的每一个问题都简化为它的问题。

• This problem can be P

![image25](../../assets/e5e15fc01d11498ba993d483083c7d8b.png)

