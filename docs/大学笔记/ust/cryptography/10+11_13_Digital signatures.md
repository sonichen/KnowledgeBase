## Digital signatures

- Provide *integrity* in the public-key setting
- 类似于MAC，但也有一些关键的区别

### 安全性

即使在观察了多个消息上的签名之后，攻击者也应该无法在新消息上伪造有效的签名





### Comparison to MACs

- *Public verifiability*

  - “Anyone” can verify a signature	

  - (Only a holder of the key can verify a MAC tag)

- *Transferability*
  - Can forward a signature to someone else…

- *Non-repudiation*
  - 签名人不能拒绝发出签名
    - 对法律应用至关重要
    - 法官可以使用pk的公共副本来验证签名
  - MACs cannot provide this functionality
    - 如果没有访问密钥，就无法验证标记
    - 即使接收者给了钥匙来判断，法官也如何才能验证钥匙是正确的

### Signature schemes

![image-20240511211406726](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511211406726.png)

#### Security

• 与 MAC 安全性完全类似。 

- 威胁模型

- “自适应选择消息攻击”

- 假设攻击者可以诱使发送者签署攻击者选择的消息。 

-  安全目标

  - “存在性不可伪造性”
  - 攻击者应该无法伪造对发送者未签署的任何消息的有效签名。 

  

  

![image-20240511211616508](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511211616508.png)

#### Security

![image-20240511211633742](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511211633742.png)



![image-20240511204542610](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511204542610.png)

![image-20240511204616910](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511204616910.png)

## Hash-and-sign paradigm

TODO

## RSA-based signatures

## RSA-FDH

## dlog-based signatures

## Public-key infrastructure (PKI)

### 什么是证书

在使用公钥加密算法和数字签名技术时，需要使用他人公钥，如何验证公钥是真的？这时就需要证书

![image-20240511204002123](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511204002123.png)

### 证书工作原理

Alice要发送信息给Bob，所以Alice需要得到Bob的公钥

![image-20240511204207529](assets\image-20240511204207529.png)



### 什么是PKI

![image-20240511204231781](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511204231781.png)

### PKI组成

![image-20240511204308922](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511204308922.png)

### PKI工作原理

![image-20240511204350658](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511204350658.png)

![image-20240511204401073](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511204401073.png)

![image-20240511204419131](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511204419131.png)

### 攻击方法

![image-20240511204426908](D:\Workplace\github\soni_notes\docs\大学笔记\ust\cryptography\assets\image-20240511204426908.png)

## SSL/TLS

## Handshake protocol