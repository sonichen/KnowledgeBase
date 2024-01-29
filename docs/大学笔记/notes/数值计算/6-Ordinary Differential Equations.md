---
title: 6-Ordinary Differential Equations
updated: 2024-01-29T12:50:00.0000000+08:00
created: 2022-12-19T14:19:48.0000000+08:00
---

总结：
![image1](../../assets/4cff1041464b49ecadca1ae6a2e2fccf.png)

![image2](../../assets/b9403406d51c46bc990eee858b829821.png)

常微分方程是一个包含导数的方程。

![image3](../../assets/3eb31c8918dd43c1a82974fc1d90a236.png)
形如，一阶常微分方程

## 6.1 INITIAL VALUE PROBLEMS
一阶常微分方程的initial value problem初值问题是该方程与特定区间a≤t≤b上的初始条件：
![image4](../../assets/627160cfeb544e45a2d1af55bc953fc8.png)

### 6.1.1 Euler’s Method
![image5](../../assets/f8fc77b810b04304ac00ddbfd184d904.png)

![image6](../../assets/f5d276a451ac4a1b92eb809521db35c1.png)

### 6.1.2 Existence, uniqueness, and continuity for solutions
本节为计算初值问题的方法提供了一些理论背景。在我们开始计算一个问题的解之前，知道这一点是有帮助的
(1)解决方案存在，
(2)只有一个解决方案

![image7](../../assets/3e306bd526e04136b390cb9b151c30e8.png)

![image8](../../assets/4f6127a6ca1641e7a51eea2f8b87384f.png)

![image9](../../assets/62f5a653cf6b4413b5dfd03a3e45279a.png)

![image10](../../assets/37569e240f674199ab89aab8a7721478.png)

![image11](../../assets/3e9896f07ab64a41a109a93eeaa10b7d.png)

![image12](../../assets/b330bc6e02fa46c6b56ed24ce8e0f3b7.png)

### 6.1.3 First-order linear equations
一类易于求解的特殊常微分方程提供了一套方便的说明性例子。
它们是一阶方程，其y变量的右侧是线性的。考虑初值问题
![image13](../../assets/d2cc3761ac754ecc9e986bf870f87121.png)
结论
![image14](../../assets/e93e09d122464854bcec6a55912beca8.png)

带公式

![image15](../../assets/00d4277a0d65444f89c465d279681ca6.png)
Separation of variables
![image16](../../assets/e624797b1f664796bd234fe1a98a68c7.png)

![image17](../../assets/2117d8e6040641f282b8a50360d50dbb.png)

## 6.2 ANALYSIS OF IVP SOLVERS
## 6.2.1 Local and global truncation error

![image18](../../assets/6e7f42649ea14982ac6d53039e8e369e.png)

![image19](../../assets/e18044122e6f46108f3e9b8683b79761.png)

![image20](../../assets/c7a85baf90f845a3b81eede7ad8b32b2.png)

![image21](../../assets/8edc94cd83bb44729827c49f051b6b19.png)

![image22](../../assets/9f441e3fe70540c7bac6880220ef1e37.png)

### 6.2.2 The explicit Trapezoid Method
![image23](../../assets/1994ef9cb9624cfcac9fc427b6590d59.png)

![image24](../../assets/ac0be0dd56c44d799c36081aff36ccb1.png)

![image25](../../assets/354447901f624663869f97a96335b5f1.png)

![image26](../../assets/288a8fdfa53b49fd9d6be03ce669f9b5.png)

![image27](../../assets/d012c964f75040f6bc6d65157cc2ccf8.png)

![image28](../../assets/fc2807a6b28f41d2b39e0195271c8259.png)
### 6.2.3 Taylor Methods
![image29](../../assets/f3624c13f3ff4730b8fee554f079733b.png)
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image30](../../assets/302a4f903a91445793ac3f6ed948d0dc.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

![image31](../../assets/18122393c5004328988852c65c96c3c4.png)
------------------------------------------------------------------------------------------------------

![image32](../../assets/db688bf4cc4747ee8a120f73550bb34b.png)

![image33](../../assets/f46603cd1e7243148efe218f84f8b892.png)

## 6.3 SYSTEMS OF ORDINARY DIFFERENTIAL EQUATIONS
微分方程的阶数是指在该方程中出现的最高阶导数。一阶系统具有这样的形式
![image34](../../assets/8b920bfa37044a9dab186ca62432195e.png)

![image35](../../assets/6a90457681724d62b99d7b194f6bdb76.png)

6.3.1 Higher order equations

6.3.1 Higher order equations
![image36](../../assets/8ebdc4a488b64f4380ee39ee4ea17c8d.png)

![image37](../../assets/1a83079c62ec46efa29ebbf44af3973c.png)

![image38](../../assets/04f1bb8ffd5d4d7bad3968a66c5906a9.png)

![image39](../../assets/0d8c03d6bd464f1f9a75bb95bfcbe672.png)
6.3.2 Computer simulation: the pendulum
6.3.3 Computer simulation: orbital mechanics

## 6.4 Runge-Kutta Methods and applications
### 6.4.1 The Runge–Kutta family
![image40](../../assets/eb956ce1538148ba854dac11afc7aa3b.png)

![image41](../../assets/f9ce91427fe34b949bee5c42df50bab4.png)

![image42](../../assets/f61159c37271481d8b02438615dcd219.png)

![image43](../../assets/e8410f11aec94121937150398fae5188.png)

6.5 VARIABLE STEP-SIZE METHODS
## 6.6 Implicit Methods and Stiff Equations

![image44](../../assets/fe9dc198152e4772a32bf9d0c53cb4f5.png)

![image45](../../assets/e980adf60e0f4f5c8afcba610c56c648.png)

![image46](../../assets/436899c8edea457ea5b06413ca8792a0.png)

![image47](../../assets/aa12faf8488f4acaa094ad8173215c9c.png)

![image48](../../assets/490ad1471eb343eebda815d53558a90a.png)

![image49](../../assets/443d17de77eb45cd832189d93804fd7d.png)

![image50](../../assets/4c7c285a295b4166bb23d74e68c6cfe6.png)

