---
title: 'Unification&Proof search '
updated: 2020-08-09T21:30:40.0000000+08:00
created: 2020-08-09T20:46:32.0000000+08:00
---

## 一、Unification
### 1,Definition 
– two terms unify:
•  if they are **the same term**, or
•  if they contain variables that can be uniformly instantiated with terms in such a way that the resulting terms are equal
2,how
-- If T1 and T2 are **constants**, then T1 and T2 unify if they **are the same atom, or the same number**  
--**T1 is a variable** and T2 is any type of term, then T1 and T2 unify, and T1 is instantiated to T2 (and vice versa)
3.  If T1 and T2 are complex terms then they unify if:
1.  They have the **same functor and arity**, and

2.  **all their corresponding arguments unify**, and

3.  the variable instantiations are compatible
Eg
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>?- X=mia,</p>
<p>X=vincent.</p>
<p>no</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Prolog has instantiated X with mia, so that it cannot unify it with vincent anymore</td>
</tr>
</tbody>
</table>
Which of the following pairs of terms unify?

![image1](../../assets/36eb44c8a38547788aeabc0d3d041714.png)
### 3,Occurs Check 
Prolog does not use a standard unification algorithm
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th>?- father(X) = X.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>X=father(father(father(…))))</p>
<p>yes</p></td>
</tr>
</tbody>
</table>

A standard unification algorithm carries out an occurs check
•  If it is asked to unify a variable with another term it checks whether the variable occurs in this term
•  In Prolog (ISO standard):
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>?- unify_with_occurs_check(father(X), X).</p>
<p>no</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
### 
### 4,eaxmple
![image2](../../assets/f2c8f98122214f14863fc4c19944c722.png)

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>house_elf(dobby).</p>
<p>witch(hermione).</p>
<p>witch("McGonagall").</p>
<p>witch(rita_skeeter).</p>
<p>magic(X):- house_elf(X).</p>
<p>magic(X):- witch(X).</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>?-<em>magic</em>(Hermione).</p>
<p><strong>Hermione</strong> = dobby</p>
<p><strong>Hermione</strong> = hermione</p>
<p><strong>Hermione</strong> = "McGonagall"</p>
<p><strong>Hermione</strong> = rita_skeeter</p></td>
</tr>
</tbody>
</table>
## 二、Search trees 
1,
![image3](../../assets/f3db7a69caa849daadf71fe3e2183304.png)

**2,**
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>loves(vincent,mia).</p>
<p>loves(marsellus,mia).</p>
<p>jealous(A,B):- loves(A,C), loves(B,C).</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>?-jealous(X,Y).</td>
</tr>
<tr class="even">
<td><p><strong>X</strong> = Y, <strong>Y</strong> = vincent</p>
<p><strong>X</strong> = vincent,</p>
<p><strong>Y</strong> = marsellus</p>
<p><strong>X</strong> = marsellus,</p>
<p><strong>Y</strong> = vincent</p>
<p><strong>X</strong> = Y, <strong>Y</strong> = marsellus</p></td>
</tr>
</tbody>
</table>

![image4](../../assets/a1819e85f68b41caa6b1a5fcdef3676f.png)
