---
title: 4-角点检测Harris corner detection
updated: 2024-01-29T12:37:14.0000000+08:00
created: 2022-12-06T11:27:28.0000000+08:00
---

是一种检测图像中拐角的方法。它所依据的理念是，图像中的==角应该在所有方向上都有高度的强度变化==。该算法的工作原理是==计算每个像素在各个方向上的强度变化，并将那些具有高度变化的像素识别为角。==
## 
## 
## 一、角点检测
角点是什么：
![image1](../../assets/fc2202f976634ec9a58d95fee1cf4fc1.png)
角点通常被定义为**两条边的交点**，更严格地说法是，**角点的局部邻域应该具有两个不同区域的不同方向的边界**。

图像特征类型可以被分为如下三种：
- 边缘
- 角点（感兴趣关键点）
- 斑点（Blobs）（感兴趣区域）
角点检测算法
当前的图像处理邻域，角点检测算法可归纳为以下三类
- **基于灰度图像的角点检测**
- 基于二值图像的角点检测
- 基于轮廓曲线的角点检测

角点的作用：通过角点来定位，角点包含大量的位置信息，指向信息

计算机怎么识别角点？---角点检测算法

角点的特征是什么：
![image2](../../assets/43bce8e8a3324348ae0fca713739e078.png)

灰度化后
边的变化不明显（亮度
但是角的变化很大，与周围对比，一边白一边红
要看角的周围的窗口区域，在各个方向上的变化
![image3](../../assets/70d7e08b90c1412f83d63bc5b157ea8b.png)

二、公式推导
![image4](../../assets/ca1c34a5a71040d3ad9605a3d2d02bdd.png)
高斯：考虑了领域的贡献，距离中心点越远，影响越小
w代表权值
E(u,v)：向竖直方向移动u个单位，再向水平方向移动v个单位

这个式子是把窗口内移动后的数字和移动前的数字相减，平方，表达了窗口移动的变化，反应了图片的亮度变化

要找角点，在各个方向变化明显

u,v任意值，希望式子很大

![image5](../../assets/c23c536becc142f89d34035092a366e9.png)

带入泰勒展开

![image6](../../assets/a50150ffbd4b40ab9dc5d0178b8051b1.png)

![image7](../../assets/a110a87a126c4e208bae1d5ffd568c3f.png)

目的：让让大1让大2同时很大
![image8](../../assets/892e48487fc5436996aab9bd75ee4719.png)

![image9](../../assets/7fc291c828c24d0bbee516752d0a140d.png)

只有一个很大：是边
两个都很小：平坦区域
两个都很大：角
![image10](../../assets/21615662ac9f48e8928248cd2a4aeeac.png)
## 二、伪代码
输出得分，得分大于这个阈值我就认为你是角点
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>高级别的伪代码</p>
<p>1 . 将原图转为灰度图</p>
<p>2. 应用高斯滤波器来平滑噪音</p>
<p>3. 应用Sobel operator，找出灰度图像中每个像素的x和y梯度值</p>
<p>4. 对于灰度图像中的每个像素p，考虑它周围的3×3窗口并计算corner strength function。将其称为Harris value。</p>
<p>5. 找到所有超过某个阈值的像素，并且是某个窗口内的局部最大值（以防止多余的重复特征）。</p>
<p>6. 对于符合第5条标准的每个像素，计算出一个特征描述符</p>
<p></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>High-level pseudocode</p>
<p>1. Take the grayscale of the original image</p>
<p>2. Apply a Gaussian filter to smooth out any noise</p>
<p></p>
<p>3. Apply Sobel operator to find the x and y gradient values for every pixel in the grayscale image</p>
<p></p>
<p>4. For each pixel p in the grayscale image, consider a 3×3 window around it and compute the corner strength function. Call this its Harris value.</p>
<p></p>
<p>5. Find all pixels that exceed a certain threshold and are the local maxima within a certain window (to prevent redundant dupes of features)</p>
<p></p>
<p>6. For each pixel that meets the criteria in 5, compute a feature descriptor.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p>参考资料：</p>
<p>[1] <a href="https://medium.com/data-breach/introduction-to-harris-corner-detector-32a88850b3f6">https://medium.com/data-breach/introduction-to-harris-corner-detector-32a88850b3f6</a></p></td>
</tr>
</tbody>
</table>
