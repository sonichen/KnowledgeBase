## RSA加密算法

成熟的公钥密码体制

之前的公钥加密：当Bob给Alice发消息时，Alice需要公开一个公钥，bob需要用Alice公开的公钥进行加密，然后Alice自己保留一个只有自己知道的私钥用来解密，这里看出Alice要先生成一个公钥和私钥

## 算法描述

### 密钥生成

1. 选取两个保密的大素数p和q

2. 计算n=p✖q，𝜑(n) =(p-1)(q-1), 其中𝜑(n)是n的欧拉函数值
3. 选一个整数e，满足1<e<𝜑(n)，且gcd(𝜑(n),e)=1 （gcd是最大公因数，意思是这两个互质）
4. 计算d，满足d·e≡1mod𝜑(n), 即d是e在模𝜑(n)下的乘法逆元，因e和𝜑(n)互素，由模运算可知，它的乘法逆元一定存在
5. 以{e,n}为公开钥，{d,n}为秘密钥



### 加密



### 解密



### 补充



#### 乘法逆元

d*e=1mod 𝜑(n)

换一个形式

d*e-1=k 𝜑(n)

怎么求d

假设e=3, 𝜑(n) =11,k取1

那么d*3-1=11 , d=4



假设e=13,𝜑(n)=160，怎么计算

用拓展欧几里得算法：a*x=1 mod p，求x （可以写为a * x-p*n=1）

1 = a*x - p* n

4    = 160 - 12 *  13

希望是1，现在是4，继续算

1=13 - 3*4

1=13*x-160 *n

 

<br>

## 总结

1. 选取两个保密的大素数p和q

2. 计算n=p✖q，𝜑(n) =(p-1)(q-1), 其中𝜑(n)是n的欧拉函数值

3. 选一个整数e，满足1<e<𝜑(n)，且gcd(𝜑(n),e)=1 （gcd是最大公因数，意思是e和𝜑(n)互质）

4. 计算d，满足(de)≡1 mod 𝜑(n), 即d是e在模𝜑(n)下的乘法逆元，因e和𝜑(n)互素，由模运算可知，它的乘法逆元一定存在【**(de) mod 𝜑(n) =1（即de=k𝜑(n) + 1, k≥1）**】

5. 以{e,n}为公开钥，{d,n}为秘密钥

6. 加密算法和解密算法

   (这里N就是上面n)

![image-20240502135746338](assets\image-20240502135746338.png)



## 1 初步认识

RSA算法是现今使用最广泛的[公钥](https://so.csdn.net/so/search?q=公钥&spm=1001.2101.3001.7020)密码算法，也是号称地球上最安全的加密算法。

宏观看加密和解密的基本过程

RSA采用的是非对称加密。公钥密码学算法

![image-20240502134044822](assets\image-20240502134044822.png)

![image-20240502134113000](assets\image-20240502134113000.png)



![image-20240502134222125](assets\image-20240502134222125.png)



如何计算公钥和私钥

欧拉函数计算𝜑(n)

然后选取e，保证e和𝜑(n)互质且e的分为

然后选取d，只要知道𝜑(n)就可以算出d，私钥就有了

![image-20240502134738461](assets\image-20240502134738461.png)

案例

![image-20240502134848076](assets\image-20240502134848076.png)

加密和解密补充

加密：RSA加密是对明文的e次方后除以N后求余数的过程。

![image-20240502135921881](assets\image-20240502135921881.png)

解密:RSA解密，密文进行D次方后除以N的余数就是明文。

![image-20240502135939364](assets\image-20240502135939364.png)

![image-20240502135949603](assets\image-20240502135949603.png)

![image-20240502140023109](assets\image-20240502140023109.png)





生成密钥对

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200806194011614.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3ZhbmFycm93,size_16,color_FFFFFF,t_70)



![在这里插入图片描述](https://img-blog.csdnimg.cn/20200806194030845.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3ZhbmFycm93,size_16,color_FFFFFF,t_70)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200806194042421.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3ZhbmFycm93,size_16,color_FFFFFF,t_70)





## 补充知识点

### 对称加密和非对称加密

对称加密：使用的密钥一样，加密解密使用相同的密钥

Alice给Bob传递密文m，比如信息是8，密钥是3，那么生成密文5。

Bob拿到密文5，用一样的密钥3进行解密，得到信息8.

以上意味着通信之前需要双方沟通密钥

![image-20240502132754653](assets\image-20240502132754653.png)

非对称加密：无密码加密，通信之前无需双方沟通密钥（对称加密）

场景：Alice要和bob通信，Alice有一个锁和钥匙，Alice把打开的锁给bob，bob用锁把信息加密给alice，Alice那边可以用自己的要是打开锁看到信息。Alice可以把锁copy多个给多人。

换成数学思想就是，一个加密锁（对信息加密），一个解密锁（对信息解密）

也就是要找一个函数，函数正向运算容易，逆向运算很难

![image-20240502133423221](assets\image-20240502133423221.png)

### 取模运算

也就是算余数

≡ 表示等式两侧余数相等

![image-20240502133643820](assets\image-20240502133643820.png)

a与b分别用n除，余数相同

a=3, n=2, 那么b=1， 

![image-20240502133711168](assets\image-20240502133711168.png)

#### 欧拉函数

重点总结: 

![image-20240502134512860](assets\image-20240502134512860.png)

定义：小于n的正整数中与n互质的数的数目

比如

6，比6小的有12345，互质的有1和5，所以𝜑(6)=2

7, 比7小的123456，都互质，所以𝜑(7)=6，7是质数，比它小的都是

如果n是指数，那么𝜑(n)=n-1

**如果 n 可以分解为 2 个互质的整数之积，那么 n 的欧拉函数等于这两个因子的欧拉函数之积**
**n=p*q,且 p，q 互质，则 𝜑(𝑛)= 𝜑(p ∗ q)= 𝜑(p) ∗ 𝜑(𝑞)**

比如21=3*7，3和7互质

𝜑(21) = 𝜑(3*7) =𝜑(3) *(7) =2 * 6=12

















## Reference

[1] https://www.bilibili.com/video/av73858330 RSA基本原理

[2] https://www.bilibili.com/video/BV1gE411i7Xr RSA计算公钥私钥

[3] https://blog.csdn.net/vanarrow/article/details/107846987

draft



要证明算法B能够高效地计算 `a ∈ Z_N` 和 `b ∈ Z`，使得 `a^e ≡ u^b (mod N)` 且 `0 = |b| < e`，我们将利用问题中描述的算法A。

给定 `(x_1, y_1) = (x_2, y_2)`，满足 `H_{N,e,u}(x_1, y_1) = H_{N,e,u}(x_2, y_2)`，我们知道：

x_1^{eu^{y_1}} ≡ x_2^{eu^{y_2}} (mod N)

令 `a = x_1 * x_2^{-1}`，`b = y_1 - y_2`。则：

a^{eu^{y_1}} ≡ x_1^{eu^{y_1}} * (x_2^{-1})^{eu^{y_1}} 
          ≡ x_1^{eu^{y_1}} * (x_2^{eu^{y_1}})^{-1} (mod N)
          ≡ x_1^{eu^{y_1}} * x_2^{eu^{y_2}} (mod N)
          ≡ x_1^{eu^{y_2}} * x_2^{eu^{y_2}} (mod N)
          ≡ (x_1 * x_2^{-1})^{eu^{y_2}} (mod N)
          ≡ a^{eu^{y_2}} (mod N)

因此，我们有 `a^{eu^{y_1}} ≡ a^{eu^{y_2}} (mod N)`。现在，由于 `e` 和 `u` 与 `φ(N)` 互素，`eu^y` 将涵盖 `N` 模下所有可逆的剩余，当 `y` 范围从 `0` 到 `e-1` 时。

这意味着 `a` 在模 `N` 下有一个模反元素，我们将其表示为 `a^{-1}`，并且我们可以计算 `b = y_1 - y_2`，使得 `0 ≤ b < e`。

因此，算法B能够高效地计算 `a` 和 `b`，因此它能够高效地计算 `a` 和 `b`，使得 `a^e ≡ u^b (mod N)` 且 `0 = |b| < e`。