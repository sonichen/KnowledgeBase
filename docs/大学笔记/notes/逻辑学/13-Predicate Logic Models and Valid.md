---
title: '13-Predicate Logic: Models and Validity'
updated: 2020-08-13T10:41:18.0000000+08:00
created: 2020-08-12T20:14:46.0000000+08:00
---

## 一、Valid inference 
### 1. Valid inference in propositional logic

![image1](../../assets/7a30b845e42d4684a583b8950216d10a.gif)

### 2. Valid inference in syllogisms
![image2](../../assets/52eaa9380db345daa52f14322553e4e0.png)

### 3.Valid inference: predicate logic
An inference in predicate logic of the form
![image3](../../assets/438e2846efb14cfe894103cd181381e6.png)
is **valid** if, for every model M for which we have M \|= ϕ1 and ... and M \|= ϕn, then we also have M \|= ψ.
In such case we will “overload” the \|= operator and write ϕ1,...,ϕn \|= ψ.
### 4.valuation
| in **propositional logic** | a model was **a single line in the truth table**                                              |
|----------------------------|-----------------------------------------------------------------------------------------------|
| in syllogistic logic       | a model is **a Venn diagram with some information filled in** (crossing-out or adding a ‘•’). |

5\. Classification of formulas according to their behaviour
A formula ϕ in predicate logic is:
a tautology if, for every model M, we have M \|= ϕ. In this case we often simply write “\|= ϕ”.
a contradiction if there is no model M for which M \|= ϕ. In this case we often simply write “
![image4](../../assets/fa8935396f9f49ae84d96192b71b184c.jpg)
ϕ”.
satisfiable if there is at least one model M for which M \|= ϕ.
## 二、Models in predicate logic
1 build a model of some predicate logic formula ϕ
Define some **non-empty set D** called the **domain**
Provide an interpretation I that shows how each constant/predicate symbol used in
ϕ is mapped to an object/relation in the domain

Check that the formula ϕ is actually true for this domain and interpretation.
Reminder: A model consists of two things: - a domain D (sets and relations) - some interpretation I mapping symbols into D.
Only after we have been given (or have chosen) a model can we can evaluate a formula to either “true” or “false”.2.
![image5](../../assets/164475d906344d848cf74e3c2900e2e1.png)

![image6](../../assets/845e0abfaad6400fb7d6eda2d267ac3a.png)

3\. Notation
![image7](../../assets/64fef007b693494a9c944d152bc2acbe.png)
4\.
![image8](../../assets/70e9e8ef098843df8048332199b8b691.png)

![image9](../../assets/f68e438946dc460bae1b13b6168ea1c6.png)
