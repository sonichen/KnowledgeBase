# Hash functions

## 数据完整性

数据完整性概念：用户通过某种方法知道数据是否被修改过。

为了解决这个问题，提出了解决方案：数据完整性技术。

数据完整性技术分为两个大类：

- MAC为代表的对称密码技术
- Digital Signature为代表的公钥密码学技术

## Hash函数

作用：把任意长度的长消息转成长度固定的短消息

定义：如果 h 是一个 Hash 函数，输入空间是 X，输出空间是 Y，则称 h 是定义在 (X, Y) 上的Hash 函数

分类：两种：key带密钥的、unkeyed不带密钥的。无特别说明时一般指的是不带密钥的hash 函数

哈希函数可以被视为位于私钥和公钥密码学之间。

## Hash安全性 - Collision-resistance

![image-20240512194329975](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240512194329975.png)

collision: 一对**不同的输入x和x‘**，哈希函数相同，也就是H(x) = H(x')

Collision-resistance： 如果在H中不可能找到collision，那么H是*collision-resistant*，也就是说如果找到任意一对 x 和 x’∈X 且 x≠x’，使得 h(x)=h(x’)，是计算上困难的，则称 h 是碰撞稳固的。  

## Generic hash-function attacks

**Q:What is the best “generic” collision attack on a hash function**

![image-20240512194552235](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240512194552235.png)

A: 最好的“通用”碰撞攻击是生日攻击。这种攻击利用了生日悖论，即在一个随机选择的元素集中，两个元素共享相同值的概率随着元素数量的增加而显著增加。在哈希函数中，这意味着随着对更多输入进行哈希处理，发现两个输入具有相同哈希值（碰撞）的概率迅速增加。生日攻击利用这一概率来高效地找到碰撞。

> 对于一个输出长度是n-bit的Hash函数，寻找碰撞最直接的方法是穷举攻击：
>
> 产生(2^n)+1个不同的消息，分别计算它们的Hash值。很明显，最多有2^n个不同的Hash值。而(2^n)+1个消息必然产生(2^n)+1个Hash值。根据抽屉原理，必然有两个不同的消息，它们的Hash值相同，如此便找到了一对碰撞。
>
>    很明显，穷举攻击的时间复杂度为O(2^n)。
>
>    有没有更快的方法呢？当然有。
>
>    生日攻击可以O(2^{n/2})的时间复杂度找到一对碰撞。



**Q:If we compute H(x1), …, H(x2l + 1), we are guaranteed to find a collision (why?)**

A: 这是因为如果我们有 2l + 1 个不同的输入，它们的哈希值是通过 H 哈希函数计算的，并且输出空间的大小是 2^l，根据鸽笼原理，必定会有至少两个输入产生相同的哈希值，即产生碰撞。

我们能否做得更好呢？生日攻击就是一种方法，它利用了生日悖论。通过仅计算较少数量的哈希值，如 sqrt(2^l)，然后进行比较，生日攻击可以在更短的时间内找到碰撞。这比计算所有可能的哈希值并进行比较更为高效。

### “Birthday” attacks

Q：假设一年有366天，那么在一个房间里必须有两个人同时过生日的最低人数是多少？

A：367

Q：在一个房间里，让至少有两个人有相同生日的概率大于1/2，假设一年有366天，房间里的人的生日是独立的，每个生日的可能性是相等的？

A：设一年366天

![image-20240511091944298](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511091944298.png)



![image-20240512212523650](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240512212523650.png)

**生日攻击**

![image-20240511092040809](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511092040809.png)

![image-20240512195418009](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240512195418009.png)

> ### 生日攻击
>
>   根据公式(1)，对于n-bit的Hash函数（N=2^n），只要准备t≈1.177sqrt(2^n)个消息，就能以至少p=1/2的概率成功找到一对碰撞。
>
> 生日攻击：随机产生t=INT(1.177sqrt(2^n))个不同的消息，分别计算它们的Hash值，如果找到两个Hash值相同的消息，则将之输出，否则攻击失败。   
>
> 以上过程大约执行两遍就能找到一对碰撞。
>
> 可见，生日攻击的时间复杂度是O(2^{n/2})，比穷举攻击快了很多很多，成功概率还挺高。
>
> ### 抵抗生日攻击
>
>    生日攻击说明了这样一个事实，比如使用80-bit的Hash函数，在生日攻击下，其安全性只有O(2^40)，非常不安全，达咩！
>
> 要想抵抗生日攻击，必须保证Hash函数的输出长度足够长，使得产生t个消息是计算上不可行的。比如，256-bit的Hash函数，生日攻击的时间复杂度为O(2^128)，是计算上不可行的。（话又说回来，即使长度达到256-bit，也未必保证安全性就能达到O(2^128)，因为生日攻击并没有考虑Hash函数的内部构造细节。如果Hash函数设计的不好，攻击者通过分析内部构造细节，可以找到效率更高的攻击方法）
>
>  实际应用中，为抵抗生日攻击，选择Hash函数的一个原则是：要达到O(2^n)的安全性，需选择2n-bit的Hash函数

## Building a cryptographic hash function

两种方法:

- Build a *compression function* h
- Build a full-fledged hash function (for arbitrary length inputs) from a compression function h（从压缩函数h构建一个完整的哈希函数（用于任意长度的输入））

**Building a hash function**

Construct a hash function H (for arbitrary  length inputs) based on *h*

– Prove that collision resistance of *h* implies collision resistance of H

##  Merkle-Damgard transform

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



### HMAC

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



如果MAC对于固定长度的消息是安全的，而H是抗碰撞的，那么前面的构造对于任意长度的消息是安全的MAC

If the MAC is secure for fixed-length messages  and H is collision-resistant, then the previous construction is a secure MAC for arbitrary length messages

![image-20240512200300854](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240512200300854.png)

- Hash function + block-cipher-based MAC?
  - Block-length mismatch (e.g., if using AES as the block cipher)
  - Need to implement two crypto primitives (block cipher and hash function)
- Constructed entirely from Merkle-Damgard hash functions
  - MD5, SHA-1, SHA-2

  - Not SHA-3
- Can be viewed as following the hash-and-MAC paradigm
  - With (part of the) hash function being used as a pseudorandom function

### Fingerprinting

E.g., deduplication

E.g., file integrity

- 假设有可能为文件x获得一个可靠的H (x)副本，注意：不同于消息身份验证代码上下文中的完整性

### Outsourced storage

How to outsource files to an untrusted server

![image-20240512200800639](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240512200800639.png)

外包存储加密，通常称为“外包存储加密”，涉及设计用于保护存储在外包存储系统（例如云存储服务）中的数据的加密技术和协议。

在外包存储中的主要挑战是确保数据在不完全信任的服务器上存储时的机密性和完整性。以下是外包存储中常用的一些加密技术：

1. **加密**：在将数据外包到存储服务之前对其进行加密。这确保了即使存储提供者遭到入侵，数据也仍然保持机密性。此外，可以采用访问控制机制来控制谁可以访问解密密钥。
2. **同态加密**：这允许在不解密数据的情况下对加密数据执行计算。这在需要对数据进行处理或分析而数据仍然加密的情况下特别有用，例如在外包计算中。
3. **零知识证明**：这些是允许证明者说服验证者一个陈述的有效性，而不会透露任何附加信息的协议。零知识证明可用于验证存储提供者正确存储数据，而不会透露数据本身。
4. **可验证计算**：这涉及协议，其中客户端可以将计算外包给不受信任的服务器，然后在不必重新执行计算的情况下验证计算的正确性。这对于像将复杂计算外包给云服务器并确保结果完整性的任务非常有用。
5. **数据完整性检查**：哈希函数和加密校验和可用于验证外包存储中的数据完整性。通过定期检查数据与预先计算的哈希值的完整性，客户端可以检测到任何未经授权的修改。

这些技术与其他技术一起构成了外包存储加密的基础，使用户能够在诸如云等不受信任的环境中安全地存储和处理其数据。

将文件外包到不受信任的服务器可以通过以下步骤完成：

1. **数据加密**：在将文件上传到服务器之前，首先对文件进行加密。使用强大的加密算法，如AES或RSA，确保文件在传输和存储过程中保持机密性。确保只有授权用户持有解密密钥。
2. **访问控制**：在向服务器上传文件之前，确保配置适当的访问控制措施。这可以通过服务器设置来实现，例如基于角色的访问控制（RBAC）或访问控制列表（ACL）。这样可以限制谁可以访问上传的文件，以及他们能够执行的操作。
3. **数据完整性检查**：在上传文件时，生成文件的哈希值，并在服务器上存储该哈希值。之后，可以定期检查服务器上的文件是否被篡改，方法是重新计算文件的哈希值并与存储在服务器上的哈希值进行比较。
4. **加密通信**：确保在文件上传到服务器时和从服务器下载文件时使用加密通信协议，例如HTTPS。这可以防止在传输过程中窃听者获取文件内容。
5. **监控和审计**：定期监控服务器以检测任何异常活动，并记录文件访问和操作。这可以帮助及时发现潜在的安全问题，并为后续审计提供重要数据。
6. **备份策略**：制定适当的备份策略，确保文件在上传到服务器后仍然可用。备份应存储在安全的位置，并受到适当的保护，以防止数据丢失。

Using **a Merkle tre**e, we can solve the outsourcing problem **with O(1) client storage and |x| + O(log n) communication**



### Merkle tree - Bitcoin

Merkle 树被用于有效地存储和验证交易数据。Hash function 在 Merkle 树中的应用如下：

1. **数据结构**：Merkle 树是一种二叉树结构，其中每个叶节点都是数据块的哈希值，而非叶节点是其子节点哈希值的组合（通常是它们的父节点的哈希）。这种结构允许有效地验证大量数据的完整性，而无需逐个验证每个数据块。
2. **交易数据**：在比特币中，每个区块都包含一系列交易。为了有效地验证这些交易的完整性，Merkle 树被用来将所有交易数据哈希为一个根哈希值。
3. **快速验证**：当比特币网络中的节点接收到一个新的区块时，它们可以通过接收到的 Merkle 树的根哈希值来快速验证整个区块的交易数据的完整性。这是通过将接收到的根哈希值与区块头中的已知根哈希值进行比较来完成的。
4. **节省空间**：由于 Merkle 树的性质，即每个节点只需要存储其子节点的哈希值，而不需要存储完整的数据块，因此可以大大节省存储空间。



### RO Model

在密码学中，Random Oracle Model（ROM）是一种理想化的假设模型，用于分析密码协议和算法的安全性。在ROM中，存在一个称为随机预言机（random oracle）的理想化黑盒，它可以接收任意长度的输入，并产生相应的随机输出。随机预言机可以看作是一个完美的哈希函数，它能够将任意长度的输入映射到固定长度的输出，并且这个映射是随机的。

在ROM中，密码算法可以在随机预言机上运行，并且可以访问预言机的随机输出。这种理想化的黑盒假设可以使密码协议和算法的安全分析更加简单和严格。然而，ROM并不是现实中存在的模型，因为真实的哈希函数并不是完美的，并且可能存在各种攻击。

尽管ROM并不是现实中存在的模型，但它是密码学中一个重要的假设模型，许多密码协议的安全性分析都基于这个模型。

#### **Pros and cons of the RO model**

Cons

- There is no such thing as a public hash function that “is random”
  - Not even clear what this would mean, formally
- Known counterexamples
  - There are (contrived) schemes secure in the RO model, but insecure when using *any* real-world hash function Pros and cons of the RO mode

Pros

- No known example of “natural” scheme secure in the RO model being attacked in the real world
- If an attack *is* found, just replace the hash
- Proof in the RO model better than no proof at all
  - Evidence that the basic design principles are sound



#### **Applications** 

- Password hashing
  - Server stores H(pw) instead of pw
  - 在q尝试中从H（pw）恢复pw应该就像在q尝试中猜测pw一样困难

- Key derivation

  - 密钥派生是从高熵信息中派生密钥的过程。这意味着从共享的高熵信息（例如生物特征数据）中生成一个密钥。密码学密钥必须是均匀的，但共享数据只是高熵的，所以密钥派生是将高熵数据转换为均匀密钥的过程。

    最小熵是衡量概率分布熵的一种方法，用于评估密钥派生的安全性。如果一个分布的最小熵为 n 位，则从该分布中抽样的元素的猜测概率（最多）为 2^(-n)。与标准（香农）熵相比，最小熵更适合用于加密，因为它更好地捕获了潜在的不确定性。

    在密钥派生中，通过将共享信息 x（从分布 X 中抽样）传递给哈希函数 H，生成共享密钥 k=H(x)。我们可以声称 k 是一个良好的（即均匀的）密码学密钥吗？如果 H 是一个随机预言机，那么只要攻击者不将 x 查询到 H，H(x) 就是均匀的。但是，如果 X 具有高最小熵，攻击者不太可能这样做（高概率）。

- Will see many more in the context of public key cryptography



### SHA-256 is “puzzle-friendly

**Optimization-free**

No better strategy than trying random nonces

**Progress-free**

You don’t get any closer the more work you do

**Parameterizable**

Easy to adjust difficulty

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

[3] https://blog.csdn.net/weixin_45732058/article/details/132056990