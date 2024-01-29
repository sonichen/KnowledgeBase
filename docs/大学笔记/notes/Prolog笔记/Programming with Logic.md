---
title: Programming with Logic
updated: 2020-08-09T21:30:58.0000000+08:00
created: 2020-08-09T17:13:59.0000000+08:00
---

## 一、Introduction 
1，"Programming with Logic"
Different from other programming languages
– Declarative (not procedural)
– Recursion (**no “for” or “while” loops**)
– Relations (**no functions**)
– Unification
2，History
First 1972.

## 二、Basic
### 1、Structure
The **end** of a clause is marked with **a full stop**.
![image1](../../assets/a4404152529248fb9ceb2bf773be6977.png)

![image2](../../assets/c4fe5d8dfd2b4632a6e936d2b31e7309.png)
There are **five clauses** in this knowledge base: two facts, and three rules.
There are **three predicates** in this knowledge base: happy, listens2music, and playsAirGuitar
案例
![image3](../../assets/26398bad18cc4a7a93e3713893af828e.png)
facts, rules and queries built out of Prolog terms
### 2，Prolog Terms

![image4](../../assets/3012b0be074b49769324563b6b97c1b8.png)

#### *(1)Simple Terms*

![image5](../../assets/35651ec9cf464ba9b5577bcbde45d87b.png)

![image6](../../assets/6aa28bd0fe05488ab22f2e29665865f5.png)

注：**常量以小写开头，变量以大小或者_开头**

#### *(2)Complex terms*
Atoms, numbers and variables are building blocks for complex terms
Complex terms are built out of a functor **directly followed by a sequence of arguments**
– Arguments are put in **()**, separated **,**
– The functor must be an atom
Examples
– playsAirGuitar(jody)
– loves(vincent, mia)
–hide(X,father(father(father(butch))))

##### --Arity 
The **number of arguments** a complex term has is called its arity
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>woman(mia) is a term with arity 1</p>
<p>loves(vincent,mia) has arity 2</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
You can define two predicates **with the same functor but with different arity**
In Prolog documentation, **arity of a predicate** is usually indicated with the suffix **"/"** followed by a number to indicate the arity
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>happy(yolanda).</p>
<p>listens2music(mia).</p>
<p>listens2music(yolanda):- happy(yolanda).</p>
<p>playsAirGuitar(mia):- listens2music(mia).</p>
<p>playsAirGuitar(yolanda):- listens2music(yolanda).</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>– happy/1</p>
<p>– listens2music/1</p>
<p>– playsAirGuitar/1</p></td>
</tr>
</tbody>
</table>

## 三、logic
### 1，逻辑符号
|            | Prolog   | Logic |
|-------------|----------|-------|
| Implication | **A:-B** | B-\>A |
| Conjunction | **A,B**  | A∧B   |
| Disjunction | **A;B**  | A ∨ B |
| Negation    | **\\**   |      |
案例
![image7](../../assets/5d3b5cffbaf04c798c1053aac8ae30ca.png)
