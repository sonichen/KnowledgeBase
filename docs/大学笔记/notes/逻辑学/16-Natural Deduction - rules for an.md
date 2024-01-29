---
title: 16-Natural Deduction - rules for and, iﬀ
updated: 2020-08-13T11:11:59.0000000+08:00
created: 2020-08-12T20:26:29.0000000+08:00
---

## 一、Notation
| 1，ϕ1,...,ϕn \|= ψ: | in any model where **ϕ1,...,ϕn are all true, then so is ψ.** |
|---------------------|--------------------------------------------------------------|
2\.
![image1](../../assets/a84781a473c94a6797c70c81b0e3da52.jpg)
3.eg
This proof shows that implies is a transitive relation
![image2](../../assets/0da89696365a452b9e70e862e0ab2766.png)
## 二．Proofs using ‘and’
**1. Introduction**
| To prove A∧B | you must prove A and you must also prove B. |
|--------------|---------------------------------------------|
**2. Elimination:**
If you know A∧B: then you can deduce that A is true, also you can deduce that B is true (you can deduce both, if you like).
![image3](../../assets/1a9efdcec5bb4e7e9a99317feb886665.jpg)

![image4](../../assets/ab3b6b0f5fa64f78a7a825da1c1a0cec.jpg)
**3. Example of a proof using ‘and’ and ‘implies’**
![image5](../../assets/2249e86bcd9a49f785b19e6537f016c2.jpg)
## 三、Proofs using equivalence (‘iﬀ’)
**1、Introduction:**
| To prove A ↔ B | you must prove A → B ，and you must also prove B → A. |
|----------------|-------------------------------------------------------|
**2、Elimination**
If you know A ↔ B: then you can deduce
that A → B is true, also that B → A is true
(you can deduce both, if you like).
![image6](../../assets/2773d205d93a42579f9e20abbd06e77f.jpg)
**3、Suppose that x is an integer. Then x is even iﬀ x2 is even.**
![image7](../../assets/637b76ffe49741e1ba88d7f8a7b2a931.jpg)
