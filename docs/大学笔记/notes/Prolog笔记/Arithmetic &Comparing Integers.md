---
title: 'Arithmetic &Comparing Integers '
updated: 2020-08-10T15:13:17.0000000+08:00
created: 2020-08-10T14:43:16.0000000+08:00
---

一、arithmetic
1，
![image1](../../assets/1fa55db3109c4910b30a39f9c426c3a5.png)
![image2](../../assets/bc5ca9b875f24e9e8c525c3937b92d98.png)

2，
+, -, / and \* do not carry out any arithmetic
•  Expressions such as 3+2, 4-7, 5/5 are ordinary Prolog terms
– Functor: +, -, /, \*
– Arity: 2
– Arguments: integers
![image3](../../assets/1496a9ca0fa547ffac013dd690b14444.png)

3，The is/2 predicate
![image4](../../assets/710ac13d65b340459e0589ff06c43b3e.png)

Restrictions on use of is/2
•  **variables on the right hand side of the is predicate**
•  But when Prolog actually carries out the evaluation, the variables must be instantiated with a variable-free Prolog term
•  This Prolog term must be **an arithmetic expression**
**右边必须是表达式**
4，Notation
Two final remarks on arithmetic expressions
– 3+2, 4/2, 4-5 are just ordinary Prolog terms in a user-friendly notation:

3+2 is really +(3,2) and so on.

– Also the is predicate is a two-place Prolog predicate

二、 tail-recursive

三、Comparing Integers
1，
![image5](../../assets/f6d9446e558e487783b65c0882026ffa.png)

2，Force both left and right hand argument to be evaluated
![image6](../../assets/8f4f8981263a4a1b89a6eed13822bb49.png)
The accumulator keeps track of the highest value encountered so far
![image7](../../assets/2972a28a7bae46d499dd749939c228e5.png)
the idea of using wrapper predicates ：
![image8](../../assets/5069c80c882b41b8a570e662a8316582.png)
