---
title: 9 Ransac
updated: 2022-12-21T14:47:13.0000000+08:00
created: 2022-12-11T09:11:03.0000000+08:00
---

# 9 Ransac
2022年12月11日
9:11

![image1](../../assets/32b15a077617410da5929e3f59165404.png)

算法步骤
![image2](../../assets/c69ab0c9ba514d25bf897a81b673557b.png)

举例子，直线
两点确定一条直线
1，从样本中随机拿两个点，画一条直线，得到模型参数
2，计算模型质量，计算所有的点到直线的距离，
设置阈值，
局内点会更多支持
3.重复

原理
1
![image3](../../assets/d0e98bf3c9434dea9aecc4c9bc277371.png)
不是一个好的模型的概率
![image4](../../assets/3bbe6b0c0f8b4307860fe67ebc823824.png)
迭代次数趋向于无限大的时候，好的模型的概率趋近于1（一定出现一个好的模型

### RANSAC计算单应性矩阵
应用
把这两个拼在一起
![image5](../../assets/bf145191ec974d2088a3fa6cf0535b62.png)

![image6](../../assets/b0fdd3a0b5744abba96c3a436a34735a.png)
黑边：旋转后超出边界

怎么拼一起？一张不动，一张做变换（RANSAC）

把一张图的坐标转到另一张图
![image7](../../assets/99e9a1d89d0d4992a42095ec0441c81f.png)

二维只能支持，旋转，坐标轴上比例变换，反射，错切

![image8](../../assets/071e6cb3abd346b9bc70b82bded1ba06.png)
三维的可以
![image9](../../assets/db446edbec8f464295e4c0ca40e76a7a.png)

![image10](../../assets/6e3f56b93a4b473fbb8428c691190cb5.png)

![image11](../../assets/5a7fa655b0aa4e1ab219bd42e63d8c74.png)

