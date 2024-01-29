---
title: L8-9-Formal Proof in Logic
updated: 2024-01-29T12:30:02.0000000+08:00
created: 2021-12-22T09:46:50.0000000+08:00
---

L8-9-Formal Proof in Logic
2021年12月22日
9:46

• Models in Propositional Logic
• Models in Predicate Logic
• Theorem Proving

1,Models in Propositional Logic
定义：命题逻辑中一个公式的估值或模型是对公式中每个变量的真赋值或假赋值
Definition: A valuation or model of a formula in propositional logic is an assignment of either true or false to each variable in the formula

![image1](../../assets/174c37537da946efb2f91fc71593268f.png)

在命题逻辑中，一个公式的model对应于其真值表中的一行
给定命题逻辑中的一个公式及其一个模型，整个公式在该模型中计算为真或假。

2,Validity and satisfiability
![image2](../../assets/f218015cd57a4ca69b9c7557324ca823.png)

| satisfiable   | model里有真的就好                |
|---------------|----------------------------------|
| valid         | 每一个model都是真的【tautology】 |
| unsatisfiable | 每一分行(model)都是错误          |

1）satisfiable:至少一行是真的
![image3](../../assets/42c67d723aac47c7b1285d9db7f6730b.png)

2）validity(全是真的tautology)
![image4](../../assets/9026706408184f0b829eb289f1209786.png)

3）Unsatisfiable
（全错）
![image5](../../assets/fea440a18fd64c7abc9c79328cc23659.png)

4）Validity and satisfiability
![image6](../../assets/22fb0425d346491c875b0299d9430962.png)

3，Semantics of Propositional Logic
![image7](../../assets/f3bc1ea121ab4bec86e62276c0b86fb5.png)
这意味着我们可以通过使用自然演绎或使用估值来证明命题逻辑中的公式

==4，CNF==
CNF中的公式允许简单地检查有效性，避免其原子数的时间指数
![image8](../../assets/0e751e4f80634bb3822c210fa868923f.png)

5，Horn Clauses
将一个命题逻辑公式转换为CNF可能是很昂贵的
CNF中的公式可以很容易地从语法上检查其有效性，但测试可满足性是困难的
Horn clauses是公式的一个子类，它们有更有效的方法来决定它们的可满足性
![image9](../../assets/020bbf21d6514cbfa9c6c2562c5b9dfb.png)

6,Semantics of Propositional Logic
![image10](../../assets/d0c124b9c35647c98c5cfc1873743849.png)

一组公式{𝐻1，𝐻2，...，𝐻𝑛}，如果它们至少有一个model，则说是consistent一致的，如果它们没有模型，则说是不一致或矛盾的。

7,Models as counter-examples
要么你应该能够证明演绎𝐻1，𝐻2，……，𝐻𝑛⊢𝐺是有效的（使用自然演绎证明系统）

或者你不应该找到一个𝐻1，𝐻2，…，𝐻𝑛都是真的，但𝐺不是真的。

![image11](../../assets/3e40a857107c4c08bb1a24daf2d536ce.png)

8,soundness and completeness
![image12](../../assets/0134d781517d4d81ad7efcaa30669406.png)

![image13](../../assets/ce37a33776684d568afbedb45e679e98.png)

9,Models in Predicate Logic

![image14](../../assets/5d61148756c3486e9c678949399734de.png)

10,Theorem Proving

![image15](../../assets/4e6b789e5e3a4307b3372396c5c351f0.png)

![image16](../../assets/a8d7338cbcb84b0f9ca11da8e3860612.png)

![image17](../../assets/be9fdee06d2b4ec4a657d02682893c82.png)

