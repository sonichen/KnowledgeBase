## Number Theory

定义：数学中专门研究整数及其性质的部分。

为什么需要：

Reason 1: Culmination of “top-down” approach

Reason 2: The public-key setting – Public-key encryption *requires* number theory

掌握基础就好

## Computational number theory

根据所涉及的输入长度来衡量算法的运行时间

![image-20240511101402908](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511101402908.png)

![image-20240511101416315](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511101416315.png)

## Representing integers

密码学中需要处理比标准（无符号）整数大得多的整数，而标准整数通常是固定长度的（如16位或32位）。为了处理这种情况，提出了使用**数组**的解决方案。这种数组被称为“bignum”，它由无符号字符（字节）组成。为了更有效地处理这些大整数，可能需要维护一个变量来指示数组的长度，或者可以假设数组的长度是固定的（这限制了bignum的最大大小）。

现在需要定义大数字上的所有算术运算

**Example: addition**

Assume as a subroutine a way to add two bytes modulo 28 (i.e., discarding overflow)

![image-20240511101745182](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511101745182.png)

![image-20240511101812009](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511101812009.png)

Example: multiplication

![image-20240511101840962](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511101840962.png)

正如我们所看到的基本算术运算，所有的加法/减法/乘法都可以有效地完成——使用小学算法（或更好的）用余数除法也可以有效地完成——更难实现！

## Modular arithmetic

表示

[a mod N] = 是a除以N的余数，eg. 5 = [35 mod 10] 

 0 ≤ [a mod N] ≤ N-1

![image-20240511101929429](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511101929429.png)

eg. 17 mod 12 =5, [5 mod 12] =12, [17 mod 12] = 5?? TODO

定理

![image-20240510173927137](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240510173927137.png)

![image-20240510173943975](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240510173943975.png)

加减乘适用，对除法不一定适用

![image-20240510174014720](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240510174014720.png)

## Exponentiation

![image-20240511102243065](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511102243065.png)

## Primes and divisibility

- 记号 a | b 表示如果 a 能整除 b，则 a 是 b 的一个因子。
- 如果 p > 1 是素数，那么它的唯一因子是 1 和 p，否则它是合数。
- gcd(a, b) 表示 a 和 b 的最大公约数，即同时整除 a 和 b 的最大整数。

## Computing gcd

**计算最大公约数**

- 可以通过分解 a 和 b 并寻找共同的质因子来计算 gcd(a, b)。
- 举例：将 120 和 500 分解为质因数后，求它们的最大公约数为 20。

**互质的定义和计算 gcd：**

- 如果两个整数 a 和 b 的最大公约数为 1，则它们称为互质。
- 计算 gcd(a, b) 可以通过分解 a 和 b 并寻找共同的质因子，但这不是高效的方法。
- 相反，可以使用欧几里得算法来计算 gcd(a, b)，这是最早的非平凡算法之一。

## Euclidean Algorithm

定理：![image-20240511102547896](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511102547896.png)

案例

![image-20240511102635959](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511102635959.png)





Proposition

![image-20240511102822340](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511102822340.png)

![image-20240511102842776](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511102842776.png)

## The Extended Euclidean Algorithm

![image-20240511102934599](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511102934599.png)





## Group theory