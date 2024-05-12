## Parity Bit Error-Detection

![image-20240511202431112](assets\image-20240511202431112.png)

 如果发送的比特数量在传输过程中发生了改变（即出现了单比特错误），则奇偶校验位会检测到这种变化。例如，在发送端计算奇偶校验位时，如果原始数据中有奇数个 1，则添加的校验位使总数为偶数，如果有偶数个 1，则添加的校验位使总数为奇数。接收端在计算奇偶校验时，如果接收到的数据中的比特数与发送的数据不一致（即出现了单比特错误），则奇偶校验位的结果将为奇数。



## Passive attacks vs. active attacks


被动攻击与主动攻击

• 到目前为止，我们只考虑了被动（即窃听）攻击

- 攻击者只是观察通道（即使它也可能执行选择明文攻击） 

• In the setting of integrity, we explicitly consider *active* attacks主动攻击

​	– Attacker has **full control over the channel**

• 处理以上问题的工具可以用MAC ， *message authentication code*



## Secrecy vs. integrity

![image-20240511202653194](assets\image-20240511202653194.png)

## MAC

MAC是一种确认完整性并进行认证的技术。

MAC是一种和密钥相关联的单向散列函数。

![image-20240512151852876](assets\image-20240512151852876.png)

认证是通过双方共享密钥实现的，没有密钥的就无法进行认证

收发双方计算的MAC相同，确保消息完整性

### 定义

消息认证码由三个概率多项式时间（PPT）算法（Gen、Mac、Vrfy）定义：

- Gen：接受输入 1^n；输出 k。（假设 |k| ≥ n。）

- Mac：接受密钥 k 和消息作为输入；输出一个标签 t。
  - t⬅Mac_k(m)
  
- Vrfy：接受密钥 k、消息 m 和标签 t 作为输入；输出 1（“接受”）或 0（“拒绝”）对于所有 m 和由 Gen 输出的所有 k。

  ![image-20240511202747352](assets\image-20240511202747352.png)

### Security

- Threat model
  - Adaptive chosen-message attack
  - 假设攻击者可以诱导发送者对攻击者所选择的消息进行身份验证
- Security goal
  - Existential unforgeability 存在性不可伪造
  - 攻击者应该无法在任何以前未经发件人身份验证的邮件上伪造有效的标记

### Formal definition

![image-20240512152358356](assets\image-20240512152358356.png)

![image-20240511202842788](assets\image-20240511202842788.png)

## A fixed-length MAC

- 我们需要一个密钥函数Mac，使得：
  - 给定 Mack(m1), Mack(m2), …,
  - 对于任意的 m 不属于 {m1, …, }，预测 Mack(m) 的值是不可行的。
- 让 Mac 成为一个伪随机函数PRF

构造

- 设 F 为保长度的、带密钥的函数。length-preserving, keyed function
- 构造如下MAC P：
  
  ![image-20240512152552806](assets\image-20240512152552806.png)
- 定理：如果 F 是一个伪随机函数，那么 P 就是一个安全的 MAC、

![image-20240511202946657](assets\image-20240511202946657.png)

分析

![image-20240512152616864](assets\image-20240512152616864.png)

![image-20240512152629483](assets\image-20240512152629483.png)

缺点

- only works for *fixed-length* messages
- only works for *short* messages
- the previous construction is limited to 
- authenticating short, fixed-length messages

## CBC-MAC

![image-20240512170831100](assets\image-20240512170831100.png)

![image-20240511203033072](assets\image-20240511203033072.png)

### CBC-MAC vs. CBC-mode

- CBC-MAC is *deterministic* (no IV)
  - MACs do not need to be randomized to be secure
  - Verification is done by re-computing the result

- In CBC-MAC, *only the final value* is output

- Both are essential for security

###  Security

- 如果F是一个块长度为n的伪随机函数，那么对于任何固定的l，基本的CBC-MAC是一个针对l-块消息的安全MAC
- 发送方和接收方必须事先就长度参数l达成一致
- Basic CBC-MAC is *not* secure if this is not done!

### Exrtension

Several ways to handle variable-length messages

One of the simplest: *prepend* the message length before applying (basic) CBC-MAC

## Malleability

如果可以修改密文，从而导致明文的可预测变化，则方案是*malleable*的

Malleability can be dangerous!

到目前为止，我们所看到的所有加密方案都是malleable！

## CCA

Chosen-*ciphertext* attacks

CCA（选择密文攻击）是指攻击者可以影响被解密的内容并观察其效果的一种攻击模型。换句话说**，攻击者除了与加密方（发送者）进行交互外，还可以与解密方（接收者）进行交互**。在这种攻击中，攻击者可以向接收者提交其选择的密文，并学习相应的明文，这是为了执行所谓的选择-密文攻击。这种攻击允许攻击者执行所谓的选择-明文攻击之外的攻击。

### CCA-security

![image-20240512171649220](assets\image-20240512171649220.png)

![image-20240512171656310](assets\image-20240512171656310.png)

在CCA安全性的定义中，攻击者可以获取其选择的任何密文的解密（除了挑战密文）。然后提出了一个问题，即这种情况是否现实可行。在现实世界中，攻击者通常不会拥有完整的解密预言（即可以随意获取密文的解密），但可能会获取关于解密密文的部分信息。在许多这种情况下，提交挑战密文将不会提供额外的信息。

## Authenticated encryption

We have shown primitives for achieving  ***secrecy*** and ***integrity*** in the private-key setting

认证加密是一种实现保密性和完整性的加密方案。在保密性方面，它通常采用CCA安全性。在完整性方面，它通常采用不可伪造性，也就是说，攻击者不能生成任何解密为以前未加密消息的密文。

• Secrecy notion: CCA-security

• Integrity notion: *unforgeability*

### Unforgeability

![image-20240512171901009](assets\image-20240512171901009.png)

![image-20240512171915523](assets\image-20240512171915523.png)