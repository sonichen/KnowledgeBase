---
title: 2-Systems of Equations课件
updated: 2023-01-01T20:33:02.0000000+08:00
created: 2022-11-29T10:19:39.0000000+08:00
---

目的：求解线性方程组

1、高斯消元 Gaussian Elimination【变化对象：(A：b)】
思路：把线性方程A通过行变换，变成上三角矩阵，根据上三角矩阵列出方程求解
例题：
![image1](../../assets/313c7cfa13c344b68d944cf82f782e06.png)

2、LU Factorization【变化对象：(A)】
（1）找A矩阵的LU分解
![image2](../../assets/b8146cf3993040e1a46de1def2a73162.png)

例题：找A矩阵的LU分解
![image3](../../assets/9fb81ddf40804132a75b2776f65ccaa3.png)
例题：找A矩阵的LU分解
![image4](../../assets/5f5cb82ac5cc4b4291f8d934cd4535e7.png)

（2）通过LU factorization解决线性方程组
步骤：
![image5](../../assets/46c014d137374bd4a951178a1b7be4bd.png)
例题
![image6](../../assets/574ec5ef94b940f786c0c9d9cb35aab0.png)

（4）何时可以使用LU分解
**==能用lu的时候主对角元素不能为0==**

3、Source of Errors（不想看）

4、Partial Pivoting 部分主元消元\[【变化对象：(A:b)】
思路：每次通过**行变换把**该区域的列的**绝对值最大**的行放在左上角，消除下面的元素，然后依次对下面区域进行重复操作
![image7](../../assets/0f36128bffd04dfb8c68c39a754aed3d.png)
例题
![image8](../../assets/bf852fd2d6d94b159fe2ded23a3f0868.png)

![image9](../../assets/b0d5f4d691db4e798b94c820b6267529.png)

![image10](../../assets/a3af122cb1dc4290b2a3d44645d07a33.png)

![image11](../../assets/62abfdd9f49f4e4089e23d402f4f4c3b.png)

5、PA=LU Factorization【变化对象：(A)】部分旋转高斯消去
（1）Permutation Matrices排列矩阵
【理解为单位矩阵，每次进行行变化时，排列矩阵也变换】
（2）PA=LU Factorization求解线性方程组
PA=LU分解是部分旋转高斯消去的矩阵公式，其中P代表置换矩阵，L和U代表下三角矩阵和上三角矩阵
![image12](../../assets/8467dd061a3841689ee1c20b7b64ed62.png)
例题
![image13](../../assets/639c73f263e345329817a6f13fc764a8.png)

![image14](../../assets/4d11f673ed8e43a3ac56b499521bc0c7.png)

5、 Iterative Methods
▶ Jacobi Method
雅可比方法是一个方程组的不动点迭代的一种形式。为了求解Ax = b，我们写了A = D + L + U，
其中D是A的对角矩阵，L是A的下三角部分，U是A的上三角部分。
![image15](../../assets/1724bcf6a090445f92b9c936e358a4b4.png)

![image16](../../assets/a75524074100428faf776f0c5fa8e979.png)
例题

![image17](../../assets/90f0c3b8ce32432191ec78deda3645a3.png)

▶ Gauss-Seidel Method
![image18](../../assets/dea73a9e1db749d29cd136a3f1a7806e.png)
例题
![image19](../../assets/e65d3c8e0a6a46399928b785803cda7a.png)

![image20](../../assets/5cde3baee55443b58eef0a1f63d0393a.png)

### 2.5.3 Convergence of iterative methods, 
**The Jacobi Method**
### 
### the Gauss–Seidel Method
![image21](../../assets/f8b6708464394ccaa781af7557932aca.png)
![image22](../../assets/f62c93716ad94cd1a318e8de234d3a6f.png)
Coverage
1，检查主对角线是否严格占优
如果不是，用2
2，
![image23](../../assets/5830a0daa1fc4604b52f5483742b6064.png)

![image24](../../assets/a5bc9ffd76104c78acabdff42ae27f04.png)
