# Hash functions

## 什么是Hash Function

定义：把**任意长度**的输出转化成**固定长度的**，**短的**输出

Hash functions can be *keyed* or *unkeyed*. We will assume unkeyed hash functions for 

simplicity

## Collision-resistance

collision: 一对**不同的输入x和x‘**，哈希函数相同，也就是H(x) = H(x')

Collision-resistance： 如果在H中不可能找到collision，那么H是*collision-resistant*（抗碰撞）的

## Generic hash-function attacks

TODO

![image-20240511085614337](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511085614337.png)

## “Birthday” attacks

Q：假设一年有366天，那么在一个房间里必须有两个人同时过生日的最低人数是多少？

A：367

Q：在一个房间里，让至少有两个人有相同生日的概率大于1/2，假设一年有366天，房间里的人的生日是独立的，每个生日的可能性是相等的？

A：设一年366天

![image-20240511091944298](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511091944298.png)

类似解释

![image-20240511091810364](assets\image-20240511091810364.png)



攻击

![image-20240511092040809](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511092040809.png)



## Building a cryptographic hash function

两种方法:

- Build a *compression function* h
- Build a full-fledged hash function (for arbitrary length inputs) from a compression function h（从压缩函数h构建一个完整的哈希函数（用于任意长度的输入））

Building a hash function



##  Merkle-Damgard transform

TODO

Merkle–Damgard变换是**将压缩函数扩展为完整哈希函数的常用方法**，同时保持前者的抗冲突特性。它在实践中广泛用于哈希函数，包括MD5和SHA系列（参见第6.3节）。这种转换的存在意味着，**在设计抗冲突哈希函数时，我们可以将注意力限制在固定长度的情况。**这反过来使设计抗冲突散列函数的工作变得更加容易。从理论角度来看，Merkle–Damg˚ard变换也很有趣，因为它意味着单比特压缩与任意量压缩一样容易（或一样难）。

具体而言，假设压缩函数（Gen，h）将其输入压缩一半；假设其输入长度为2n，输出长度为n。（只要h压缩，构造就可以不考虑输入/输出长度。）我们构造了一个抗冲突哈希函数（Gen，h），该函数将任意长度的输入映射到长度为n的输出。（Gen保持不变。）

![image-20240511093657025](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511093657025.png)

![image-20240511093702651](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511093702651.png)



## Hash functions in practice

- MD5
  - 128-bit output length
- SHA-1
  - 160-bit output length
  - 攻击方面的后续改进；不再建议；应该迁移到SHA-2
- SHA-2
  - Versions with 224, 256, 384, and 512-bit outputs
  - 没有明显的已知弱点
- SHA3/Keccak
  - 与SHA-1/SHA-2的设计非常不同(Does not use Merkle-Damgard transform)
  - Supports 224, 256, 384, and 512-bit outputs

## Application

**Hash functions are ubiquitous**

• Collision-resistance Þ “fingerprinting”

• Outsourced storage

• Used as a “random oracle”

• Used as a one-way function

– Password hashing

• Key derivation

**Application**

• E.g., hash-and-MAC

• E.g., virus scanning

• E.g., deduplication

• E.g., file integrity





• Collision-resistance Þ “fingerprinting”

### • Outsourced storage

### • Used as a “random oracle”

• Used as a one-way function

### – Password hashing

### • Key derivation

**Application**

• E.g., hash-and-MAC

• E.g., virus scanning

• E.g., deduplication

• E.g., file integrity

### HMAC

之前用CBC-MAC，现在用hash function构建一个更安全的MAC

HMAC， Hash-based Message Authentication Code

**什么是MAC**

![image-20240511094652526](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511094652526.png)

和其他散列函数的不同点在，输入前多了一个双方共享的密钥

没有密钥的就无法计算出这个MAC值来完成认证

双方计算的MAC相同确保了完整性

HMAC：结合散列函数和密钥，使用密钥对消息进行哈希运算，生成固定长度的哈希值

![image-20240511094957416](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511094957416.png)

计算公式

![image-20240511095023626](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511095023626.png)

message是信息m

key是密钥

opad, ipad是一个固定的值，取值多少取决于使用的散列函数

![image-20240511095052651](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511095052651.png)

![image-20240511095131756](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511095131756.png)



![image-20240511095245944](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511095245944.png)



![image-20240511095317428](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511095317428.png)

Constructed entirely from Merkle-Damgard hash functions

– MD5, SHA-1, SHA-2

– Not SHA-3

### Outsourced storage

TODO

### Merkle tree - Bitcoin

TODO



### RO Model

在密码学中，Random Oracle Model（ROM）是一种理想化的假设模型，用于分析密码协议和算法的安全性。在ROM中，存在一个称为随机预言机（random oracle）的理想化黑盒，它可以接收任意长度的输入，并产生相应的随机输出。随机预言机可以看作是一个完美的哈希函数，它能够将任意长度的输入映射到固定长度的输出，并且这个映射是随机的。

在ROM中，密码算法可以在随机预言机上运行，并且可以访问预言机的随机输出。这种理想化的黑盒假设可以使密码协议和算法的安全分析更加简单和严格。然而，ROM并不是现实中存在的模型，因为真实的哈希函数并不是完美的，并且可能存在各种攻击。

尽管ROM并不是现实中存在的模型，但它是密码学中一个重要的假设模型，许多密码协议的安全性分析都基于这个模型。



## 补充

### 什么是哈希函数

哈希函数提供了一种将**长输入字符串映**射到**短输出字符串**（有时称为摘要）的方法。

主要要求是避免冲突，或避免映射到同一摘要的两个输入。

![image-20240511093211544](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511093211544.png)

### 碰撞

具体地说，如果散列函数H的范围大小为N，则元素x存储在大小为N的表的行H（x）中。要检索x，只需为存储在其中的元素计算该表的行H（x）和probeth即可。用于此目的的“良好”散列函数是产生少量冲突的函数，其中冲突是**一对不同的项x和x0**，其中**H（x）=H（x0）**；在这种情况下，我们也说**x和x0碰撞**。（发生冲突时，两个元素最终存储在同一单元格中，从而增加查找时间。）

### 碰撞阻力 Collision Resistance

非正式地说，如果任何概率多项式时间算法都无法在H中找到冲突，则函数H是抗冲突的。我们只对域大于其范围的哈希函数感兴趣。在这种情况下，碰撞必须存在，但这样的碰撞应该很难找到。

##### Unkeyed hash functions

![image-20240511093335685](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511093335685.png)

### 域扩展

哈希函数通常是通过首先设计**一个处理固定长度输入的抗冲突压缩函数**，然后**使用域扩展来处理任意长度的输入来构造的。**

Merkle–Damgard变换是**将压缩函数扩展为完整哈希函数的常用方法**，同时保持前者的抗冲突特性。它在实践中广泛用于哈希函数，包括MD5和SHA系列（参见第6.3节）。这种转换的存在意味着，**在设计抗冲突哈希函数时，我们可以将注意力限制在固定长度的情况。**这反过来使设计抗冲突散列函数的工作变得更加容易。从理论角度来看，Merkle–Damg˚ard变换也很有趣，因为它意味着单比特压缩与任意量压缩一样容易（或一样难）。

具体而言，假设压缩函数（Gen，h）将其输入压缩一半；假设其输入长度为2n，输出长度为n。（只要h压缩，构造就可以不考虑输入/输出长度。）我们构造了一个抗冲突哈希函数（Gen，h），该函数将任意长度的输入映射到长度为n的输出。（Gen保持不变。）

![image-20240511093657025](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511093657025.png)

![image-20240511093702651](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511093702651.png)

## Reference

[1] https://blog.nowcoder.net/n/55337144722c40939366218b4c0ae14a

[2] https://www.bilibili.com/video/BV1c34y1M7NW