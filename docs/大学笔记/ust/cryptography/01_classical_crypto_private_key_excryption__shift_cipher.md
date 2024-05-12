## Cryptography

历史上，密码学只专注于确保双方之间使用“code”提前共享秘密信息，这就是private-key encryption

现代密码学涉及的方面更多

– Data integrity, authentication, protocols, …

– The *public-key setting*

– Group communication

– More-complicated trust models

– Foundations

## Classical cryptography

特点：完全依赖于在通信各方之间预先共享的秘密信息（一个密钥）

*Private-key cryptography* – aka secret-key / shared-key / symmetric-key cryptography

## Private-key encryption

**场景**

![image-20240511212800185](assets\image-20240511212800185.png)

Bob和Alice通信，Bob提前和Alice共享一个key。

Bob发送信息m时，用加密函数得到加密后的密文c，然后传给Alice。

Alice收到密文c，用key对密文进行解密，得到信息m。

**定义**

A *private-key encryption scheme* 由**信息空间M**和**算法（Gen, End, Dec）**定义

- Gen: 密钥生成算法，输出密钥k，k∈K
- Enc：加密算法，输入密钥k和信息m∈M，输出密文c【c ⬅Enc k(m)】
- Dec: 解密算法，输入密钥k和密文c，输出信息m或者error

**对于all m∈M和Gen生成的密钥k，都有Dec k(End k (m)) = m**

![image-20240511213047511](assets\image-20240511213047511.png)





## Kerckhoffs’s principle

- *The encryption scheme* is not secret 加密方案不是秘密 ：攻击者了解加密方案，但唯一的秘密是密钥，密钥必须随机选择，并保持秘密 

- 支持这一原则的论点

  - 密钥比算法容易保密

  - 密钥比算法容易改变

  - 标准化：部署便利，公开审查 



## The shift cipher

### Basic

**案例**：考虑加密英语文本：a->0，b->1,..., z->25；密钥k∈K={0,...,25}

要使用密钥k进行加密，请将明文的每个字母移动k个位置（带行）

eg：因为c代表2，所以都移动两位

![image-20240510111250508](assets\image-20240510111250508.png)

#### 定义

M是英文小写

Gen: k∈{0,...,25}

Enc k(m1,...,mt)=输出密文c1,...ct, 并且ci := [mi + k mod 26]

Deck(c1…ct): 输出m1…mt, where  mi := [ci - k mod 26]

#### Security

不安全！--- 只有26个keys

- 给定一个密文，尝试用每一个可能的密钥解密
- 只有一种可能性将“有意义”

Example of a “brute-force” or “exhaustive search” attack



以下是改进的算法

### Byte-wise shift cipher

- 使用alphabet of *bytes*而不是（英文，小写字母），可以处理任意数据！
- 使用XOR异或而不是modular addition

#### 定义

![image-20240510112818105](assets\image-20240510112818105.png)

#### Security 

不安全！-- 只有256个可能的keys

- 给定一个密文，尝试用每一个可能的密钥进行解密

- 如果密文足够长，只有一个明文将“有意义”

思考，足够的密钥空间原理

- 密钥空间必须足够大，以使穷举搜索攻击不切实际

- 技术：只有当明文足够长时才成立

#### Code

![image-20240511214137068](assets\image-20240511214137068.png)

### The Vigenère cipher

#### 定义

1. **密钥是多个字符，而不仅仅是一个字符**：维吉尼亚密码使用的密钥由多个字符组成，而不是单个字符。
2. **加密过程**：
   - 对于每个明文字符，按照密钥的下一个字符所规定的量进行移位操作。
   - 需要时可以在密钥中循环使用。
   - 这里的移位操作是指按照密钥字符所代表的数量将明文字符进行移动，移位操作可以是字母的向后移动（加密）或向前移动（解密）。
3. **解密过程**：
   - 解密只是加密过程的逆向操作。

维吉尼亚密码是由d个字母序列给定的密钥ki（i∈[1,d])，ki确定第i+td（t为整数）个字母的移位次数。现代维吉尼亚密码代换表如下，**第一行为密钥，第一列为明文，某明文对应密钥加密产生的密文即为该行该列处的字母。**

![image-20240510113945712](assets\image-20240510113945712.png)

![image-20240510114004649](assets\image-20240510114004649.png)

t-c：v；e-a: e；l-f: q；...

#### Security

1. **密钥空间的大小**：
   - 如果密钥是由英文字母组成的14个字符的字符串，那么密钥空间的大小为2614，约等于266。
   - 如果密钥长度不固定，那么密钥空间会更大。
   - 这种密钥空间的巨大性使得暴力破解搜索变得不可行。
2. **维吉尼亚密码的安全性**：
   - 即使维吉尼亚密码的密钥空间如此之大，暴力搜索依然变得不可行。
   - 但是，这并不意味着维吉尼亚密码是安全的。
   - 其他攻击方法，如频率分析等，仍然可能会成功破解密码。

#### Attacking

**针对第一个 "流" 的分析**：

- 从密文的第一个字符开始，每隔14个字符取一个字符，这被称为第一个“流”。
- 在这个流中，找出出现频率最高的字符，记为a。

**猜测第一个密钥字符**：

- 最有可能的情况是，a对应于明文中出现频率最高的字符，通常是 'e'。
- 假设第一个密钥字符是 a 减去 'e'。

**重复分析**：

- 对于每一个流中的字符，重复以上步骤。
- 通过这种方式，逐个猜测密钥的每个字符。

**不充分利用所有信息**：

- 这种方法有些随意，并没有充分利用所有可用的信息，因此可能并不是最有效的攻击方式

#### A better attack (high level) 

1. **字母频率的分析**：
   - 让 pi（0 ≤ i ≤ 25）表示正常英文明文中第i个英文字母的频率。
   - 可以计算得到 Σi pi^2 约为 0.065。这是正常英文明文中每个字母的频率的平方的总和。
2. **观察密文中字母频率**：
   - 让 qi 表示在给定密文流中第i个字母的观察频率。
3. **预期的频率变化**：
   - 如果流的移位为j，则期望每个字母的观察频率qi+j大致等于对应明文字母的频率pi。
   - 因此，期望 Σi pi * qi+j 大致等于 0.065。
4. **测试不同的移位值**：
   - 对于每个流，测试不同的移位值j，以找到正确的移位值。
   - 对每个流都重复这个过程。



## 补充

### Modular arithmetic

TODO

- 当且仅当N除以x-y时，可以写x=y mod N【也就是N能够整除(x - y)】
- [x mod N] = x除以N的余数【】

比如

25 = 35 mod 10（35/10余数是）

25 ≠ [35 mod 10]

5 = [35 mod 10] （35/10=3...5）



### 16进制

![image-20240510112655092](assets\image-20240510112655092.png)

![image-20240510112724336](assets\image-20240510112724336.png)





### ASCII

Characters often represented in ASCII

– 1 byte/char = 2 hex digits/char

![image-20240511214628671](assets\image-20240511214628671.png)

