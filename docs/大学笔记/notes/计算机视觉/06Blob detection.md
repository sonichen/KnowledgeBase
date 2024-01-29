---
title: 06Blob detection
updated: 2022-12-18T10:30:22.0000000+08:00
created: 2022-12-16T11:26:44.0000000+08:00
---

不考了尺度，远近，大小，都能检测出来
![image1](../../assets/1742c84662b84e3b93d89ccb94f8c420.png)
## 1、一维的角度
**目标：在同一图像的缩放版本中独立检测相应的区域**
需要尺度选择机制来寻找与图像变换协变的特征区域大小
![image2](../../assets/c29f5a85653141068f72fc3544a56c03.png)

高斯二阶导（拉普拉斯是二阶导）
二阶过零点代表突变
![image3](../../assets/4481184d16c9434aaa7432a3f8b20e5a.png)

高斯一阶导要制定几个参数：一般指定σ就好，窗宽（经验公式3σ+1）

![image4](../../assets/7b5a02a6b0de45129e3b7183f6ee9c58.png)
空间选择：如果拉普拉斯响应的尺度与斑点最大源S“匹配”，拉普拉斯响应的大小将在斑点的中心达到最大值。

当信号和二阶导的模板能够匹配上的时候，一定能产生一个最大值
那怎么找模板，一个个上去试试吗（σ=1，2，3，4，5，6？
我们希望通过将其与多个尺度上的拉普拉斯函数进行卷积并寻找最大响应来找到斑点的特征尺度
问题产生：然而，拉普拉斯式的响应随着尺度的增加而衰减：
![image5](../../assets/39d16366eac34bdca9caa6f672132ef5.png)

![image6](../../assets/78346bb91a544522a23cd1a41e1c1202.png)

高斯滤波器对完美阶跃边的响应随着σ的增加而减小
为了保持响应相同（尺度不变），必须将高斯导数乘以σ
拉普拉斯算子是二阶高斯导数，所以它必须乘以σ2
![image7](../../assets/4410d8487bec457da537ec7702616a71.png)

尺度归一化后（用乘以σ2）
用不同σ去卷，找到对于σ
![image8](../../assets/6c980f81a81e4048ac746b3a45579df2.png)

## 2、二维角度

![image9](../../assets/eec1bc1fbf224680b638a298c40818c7.png)
左图，大部分在0下
尺度归一化后
![image10](../../assets/7b242e4cae2649d095efeb7df2d70e83.png)
拉普拉斯矩阵在什么尺度上达到了对半径为r的二元圆的最大响应？（尺度σ和圆半径的关系）
![image11](../../assets/011c83b510be42cab10bdd2146925380.png)

![image12](../../assets/cc265b8923134bb9925ebc3a36c2bbd6.png)

![image13](../../assets/02928ef424bd42669d85733792349a03.png)

## 3、尺度选择特性
我们将一个斑点的特征尺度定义为在斑点中心产生拉普拉斯反应峰值的尺度
![image14](../../assets/a7242c33b9834873b2accf55995f4c7b.png)

Scale-space blob detector

<table>
<colgroup>
<col style="width: 42%" />
<col style="width: 57%" />
</colgroup>
<thead>
<tr class="header">
<th><p>1、在多个尺度上用尺度归一化拉普拉斯矩阵卷积图像</p>
<p>2、求出尺度空间中平方拉普拉斯响应的极大值</p></th>
<th><p>1、Convolve image with scale-normalized Laplacian at several scales</p>
<p>2、Find maxima of squared Laplacian response in scale-space</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
</tr>
</tbody>
</table>

![image15](../../assets/ed8bcd4fa9514587acd16a24c3106d03.png)
<table>
<colgroup>
<col style="width: 34%" />
<col style="width: 33%" />
<col style="width: 32%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image16](../../assets/4ff255c03f154a33ba452dc445df15db.png)</p>
<p></p></th>
<th>![image17](../../assets/6a6439aefdd947489a9a74567ebf07ea.png)</th>
<th>![image18](../../assets/113a11473b8c4a4aa646c7696c408e0e.png)</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

改进
![image19](../../assets/1830e2c12d8c4d1ea288a00549b7fd04.png)
- Harris+拉普拉斯
- SIFT

