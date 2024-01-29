---
title: 03边缘检测canny detection
updated: 2022-12-16T11:20:06.0000000+08:00
created: 2022-12-15T14:00:03.0000000+08:00
---

总结：
什么是边缘：向量突变的地方
为什么要检测边缘：边缘能够更紧凑地表达图像信息
边缘应该怎么计算：用求导的方法，在图像里面
在真实工程里面发型不好用：需要先平滑，再求导
Canny detection：
非最大化抑制：留下最大（留下轮廓

两阶段门限：高门限找出强边，低门限连上边，延续边
## 1、边缘检测
不连续的就是边
希望用边来紧凑地表达图像，表达图像的含义

目标：识别图像中的突然变化（不连续性）
直观地说，图像中的大多数语义和形状信息都可以编码在边缘

比像素更紧凑
理想：艺术家的线条画（但艺术家也在使用对象级的知识）
![image1](../../assets/be244ed6a2d34c2f8dc217c054b9206c.png)

边有几种？
![image2](../../assets/4d9b808862ff4ba4b474a5b35e48b95e.png)
对于不同物品，关注的边类型不一样

怎么提取边？
边缘特征
边缘是图像强度函数中快速变化的一个地方
![image3](../../assets/28e41e103ecc4e729fc9235f4c6ef2c5.png)
数学中怎么找信号突变？==》导数突变的地方，找极值
![image4](../../assets/66601054030548fc9987a80273ea0225.png)

导数，近似
我的导数是我右边这个哥们减我的结果
![image5](../../assets/f294537c23de433d8b74b88139d2afa3.png)

图像的偏导数
![image6](../../assets/af26768999b34fffabe6911d2152a32a.png)
sobel：先高斯，再提取边缘
![image7](../../assets/fc50d8b494884014a1fff1e6ef4cf6f3.png)

![image8](../../assets/243f1bac8c024118a7f20b914cf2a548.png)
## 2、梯度Image gradient
点的梯度：
![image9](../../assets/2611cbd699e74cbe9c25d5abc4f372b0.png)

![image10](../../assets/c573c7c81952434ba141768ff2119e8a.png)
梯度点指向强度增加最快的方向
![image11](../../assets/ed61ccbc26bf46b2b719ffcfee68d36e.png)
梯度方向和边垂直

![image12](../../assets/fd02b846b2ef4cf19c9e3d545564a402.png)

----------------==--不太懂---==---------------------------------------------------------------------------------------------------------------------
![image13](../../assets/ac04254e6e174357be29503e26a8c26b.png)

![image14](../../assets/84b35d6dc6bc43609d8c1ef98d333e3a.png)

![image15](../../assets/61af15eac59d48b4b5b8e503480807a0.png)

![image16](../../assets/b81df3e57098460d9782879b354b5cab.png)

---------------------------------------------------------------------------------------------------------------------------------------------------------------
![image17](../../assets/dfb2807a1171483294efce97ef008551.png)

一阶导需要哪些参数：窗宽，标准差σ
高斯一阶导越大，

<table>
<colgroup>
<col style="width: 65%" />
<col style="width: 34%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Smoothing vs. derivative filters</p>
<p>平滑化滤波器</p>
<blockquote>
<p>- 高斯：去除 "高频率 "成分。"低通 "滤波器</p>
<p>- 平滑滤波器的值不可以是负数</p>
<p>- 这些值的总和应该是1</p>
<p>– One: constant regions are not affected by the filter</p>
</blockquote></th>
<th><p>![image18](../../assets/180cda44adb1455698f480949293547c.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>高斯偏导核</p>
<blockquote>
<p>- 高斯的导数</p>
<p>- 衍生滤波器的值可以是负数</p>
<p>- 这些值的总和应该是0</p>
<p>– Zero: no response in constant regions</p>
<p>- 在高对比度的地方有高的绝对值</p>
</blockquote>
<p></p></td>
<td><p>![image19](../../assets/be475d436ed14583a1bacdd6bf558630.png)</p>
<p></p></td>
</tr>
</tbody>
</table>

## 3、Canny detection（重点）
![image20](../../assets/aaff7998dad94544b94c9bdbcd43840b.png)

**方法：设置阈值**
设置门槛过滤不符合条件的数据
<table>
<colgroup>
<col style="width: 60%" />
<col style="width: 39%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image21](../../assets/1f6ccbcc39b046cfb89d7ea23f052c02.png)</p>
<p></p></th>
<th><p>![image22](../../assets/7b1bda9716e5414cb7fe10a23ccbc377.png)</p>
<p>设置“门限”</p>
<p>去噪了一下</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

![image23](../../assets/c74a53321c0841199a4f8a93b57d31cd.png)

**方法：Non-maximum suppression非最大化抑制**
和左右邻居对比梯度值是否最大，如果是，则他们不存在，我就是最大的
![image24](../../assets/806ae1728382458292d9525c26501fe3.png)

<table>
<colgroup>
<col style="width: 49%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>前</th>
<th>后</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>![image25](../../assets/0124aac2aeee499585ed00d2ea8318a4.png)</p>
<p></p></td>
<td><p>![image26](../../assets/1cf26f8816f84666bbb0a1398f856d78.png)</p>
<p></p></td>
</tr>
</tbody>
</table>

存在的问题：线断了，为什么，门限太高了
但是如果门限太低，假边就留下了
![image27](../../assets/db4727ab99604fa697b84d335cd1d877.png)

怎么办
Canny detection对门限进行改下
![image28](../../assets/5a5e562fda7c45f0b486dfc54cf7be95.png)
双门限法
先用高门限，把粗狂的边检测出来（噪声可能性小）
再降低门限，继续检测
噪声边和强边缘联系小

![image29](../../assets/922fc46f9c7d45fbacb23d8bd24aae58.png)

Canny detection算法步骤
<table>
<colgroup>
<col style="width: 45%" />
<col style="width: 54%" />
</colgroup>
<thead>
<tr class="header">
<th><p>1. 用高斯的导数过滤图像</p>
<p>2. 找到梯度的大小和方向</p>
<p>3. 非最大限度的压制。</p>
<blockquote>
<p>- Thin wide “ridges” down to single pixel width</p>
</blockquote>
<p>4. 连接和阈值处理（hysteresis）。</p>
<blockquote>
<p>- 定义两个阈值：低和高</p>
</blockquote>
<ul>
<li><p>使用高阈值来找出强边缘线，使用低阈值来延续它们。（把有连接关系的边找回来）</p></li>
</ul>
<p></p></th>
<th><p>1. Filter image with derivative of Gaussian</p>
<p>2. Find magnitude and orientation of gradient</p>
<p>3. Non-maximum suppression:</p>
<blockquote>
<p>• Thin wide “ridges” down to single pixel width</p>
</blockquote>
<p>4. Linking and thresholding (hysteresis):</p>
<blockquote>
<p>• Define two thresholds: low and high</p>
<p>• Use the high threshold to start edge curves and the low threshold to continue them</p>
</blockquote></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

![image30](../../assets/2f1879c4f3d64a7899f424cba960486c.png)
