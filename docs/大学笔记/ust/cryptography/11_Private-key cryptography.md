## Private-key cryptography

定义：运行两个用户在一个安全的信道内共享密钥

- 两个（或更多）希望安全通信的双方提前共享一个统一的秘密密钥k

- Same key k used for sending or receiving
- k的保密是至关重要的

共享密钥的这个需求有以下缺点：密钥分发问题

- 用户如何首次共享密钥？
- 需要使用安全通道来共享密钥…
- 在某些情境下可以解决这个问题
  - 例如，物理接近、可信的信使…
  - 注意：这并不意味着私钥加密无用！
- 在其他情境下可能难以解决，成本高昂，或者根本不可能解决

密钥管理问题

- 想象一家拥有N名员工的组织，每对员工可能需要进行安全通信
- 使用私钥加密的解决方案：
  - 每个用户与所有其他用户共享一个密钥
  - 每个用户必须存储/管理N-1个秘密密钥！
  - 总共O(N^2)个密钥！

缺乏对“开放系统”的支持

- 假设两个没有先前关系的用户想要安全通信
  - 他们什么时候会共享一个密钥？
- 这种情况经常发生！
  - 客户向商家发送信用卡数据
  - 在社交媒体上联系一个朋友的朋友
  - 给同事发送电子邮件

传统密码学很难解决以上问题





## The public-key setting

特点：

- 一方生成一对keys，public key pk和private key sk
  - 公钥被广泛传播
  - 私钥是保密的，并且不与任何人共享
- 生成它的一方使用的私钥；其他人使用的公钥（也被称为非对称密码学）
- 即使攻击者知道pk，安全措施也必须保持不变

**这是如何解决私钥加密技术的缺点的呢？**

- 密钥分发
  - 公钥可以通过公开（但经过认证的）

- 渠道分发 ，在N个用户系统中的密钥管理
  - 每个用户存储1个私钥和N-1个公钥；总共只有N个密钥
  - 公钥可以存储在中央、公开的目录中 
- 适用于“开放系统”
  - 即使双方之间没有先前关系，也可以找到彼此的公钥并使用它们

**公钥与私钥加密** 

需要注意的是，公钥加密严格地比私钥加密更强大

- 希望安全通信的各方可以各自生成公钥/私钥，然后彼此分享
- 根据发送方或接收方的身份使用适当的密钥

**为什么要研究私钥加密？** 

- 公钥加密大约比私钥加密慢2-3个数量级

- 同样，通信开销也高2-10倍
- 公钥加密需要更强的假设
- 如果私钥加密是一个选择，最好使用它！ 
- 正如我们将看到的，即使在公钥设置中，私钥加密也用于提高效率

## Primitives

![image-20240511154517483](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511154517483.png)

## Public-key encryption

![image-20240511154545902](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511154545902.png)

公钥加密方案包括三个PPT算法：

- Gen: 输入1^n，输出pk、sk的密钥生成算法
- Enc: 输入pk和消息m，输出密文c的加密算法
- Dec: 输入sk和密文c，输出消息m或错误的解密算法

![image-20240511154651303](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511154651303.png)



## CPA-security

### private key CPA

![image-20240511161257708](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511161257708.png)

### public key CPA

![image-20240511161243697](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511161243697.png)

## Dlog-based PKE

## Hybrid encryption and KEMs
