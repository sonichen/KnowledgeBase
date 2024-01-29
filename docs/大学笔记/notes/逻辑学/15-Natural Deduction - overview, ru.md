---
title: 15-Natural Deduction - overview, rules for implies
updated: 2020-08-13T10:54:51.0000000+08:00
created: 2020-08-12T20:21:06.0000000+08:00
---

## 一、Deciding if an inference is valid
1，if an inference using propositional logic is valid
![image1](../../assets/6b7638bf139944aeacf676cbb31e1a51.png)
2，Problems with true tables
--Size of truth table is exponential in the number of atomic propositions.
![image2](../../assets/b644a4cb1a0444988052d19d17d00ab8.png)
--Doesn’t mimic the “natural” way of reasoning.
--Won’t work for predicate logic
## 二、Gentzen’s “natural” deduction
（study the natural deduction proof system for ==predicate logic==.）,
1，The structure of a ’typical’ proof
![image3](../../assets/7ce307661c794e8eb29e36c394b9b634.png)
2，build software

![image4](../../assets/7680141d89774c6e955a5f6a961601e2.gif)

3，General structure of a natural deduction proof
Each of the ﬁve connectives and two quantiﬁers has an introduction rule and an elimination rule.
![image5](../../assets/c1d03c8c92bf4e0fbe589c6f1c8ce05f.gif)

![image6](../../assets/e0bd4f064a7243978804deda000c9db2.png)

![image7](../../assets/84356b1c06b04c2ab6efdb0a775633fe.png)
4\. Examining that theorem

![image8](../../assets/bd359ba747204b4a9e1ad0e796e08706.png)
![image9](../../assets/ba99aef181034fc1a69ac4f7a9eb48fb.png)

5.Introducing ‘implies’
1）If you want to prove a conclusion of the form P → Q then
---Assume that P is true ...

---and go on to prove that Q is true

Here P is called a local assumption. It is only assumed temporarily, for part of the proof.
6\. Formal proof rules for ‘implies’
![image10](../../assets/9af93b108f0c42eb974ed5bb306b594c.png)

