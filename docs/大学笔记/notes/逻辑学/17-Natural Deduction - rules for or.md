---
title: 17-Natural Deduction - rules for or, not
updated: 2020-08-12T20:34:20.0000000+08:00
created: 2020-08-12T20:30:22.0000000+08:00
---

## 一、Proofs using ‘or’
1、Introduction:
| To prove A∨B | you must prove A, or you must prove B |
|--------------|---------------------------------------|
2、Elimination:
If you know A∨B:，you must prove the theorem both
\- for the case where A is true
\- and also for the case where B is true (Proof by cases).
![image1](../../assets/79bb7cde3fcf46f1a5e1b89283f54e3a.jpg)
3、Example
![image2](../../assets/bbf60d63fba84d02b926a25548d93e1c.jpg)

![image3](../../assets/a744bc0fd78944d39cd962e9cba1912f.jpg)
4、Duality between ‘and’ and ’or’
Note that the introduction/elimination rules for ‘and’ and ’or’ seem to refiect each other:
The introduction rule for ‘or’ and the elimination rule for ‘and’ give you the choice (which to prove/use).

The elimination rule for ‘or’ and the introduction rule for ‘and’ inist you deal with both possibilities.

The connectives ‘and’ and ’or’ are not exactly logical opposites: instead we say that are dual to each other.
## 二、Negation
To assert “¬A” must be the same as saying “A is false”, but we only have rules to prove things that are true.
1、Introduction:
The introduction rule for contradiction is also a sort of elimination rule for negation: If you have a premise of the form ¬B, try to prove B, and then deduce a contradiction.
2、Elimination:
The usual approach is to work by means of a contradiction: if we assume A and derive a contradiction, then it must have been wrong to assume A, so deduce ¬A We use the symbol ⊥ to denote “contradiction”.

It’s rarely useful to deduce just “anything” from ⊥. Typically this rule is used to tidy up impossible cases in a proof.
![image4](../../assets/e8d90fe2e4004c3880790daa21c22ea2.jpg)
3、Example
![image5](../../assets/1d033e78311f4e74a6ebcdf07ef9778f.jpg)

![image6](../../assets/5c3cdb5b253d468c962b85b966671feb.jpg)
the elimination rule for negation as it is not accepted in all kinds of logic.

However, it is accepted in classical logic.

## 三、Brouwer’s Intuitionism
![image7](../../assets/03989f2663814faa9a9af6df3d8dafdb.jpg)

![image8](../../assets/f5db2244da3f4e0bb7bb0fa5d9e2c2e7.jpg)

![image9](../../assets/18101171cc2349ffae7f35e62192b2e7.jpg)
