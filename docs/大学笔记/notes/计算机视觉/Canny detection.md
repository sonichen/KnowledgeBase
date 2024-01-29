---
title: Canny detection
updated: 2022-12-22T12:00:29.0000000+08:00
created: 2022-12-20T15:41:12.0000000+08:00
---

Canny detection步骤
1.去噪（**Noise reduction**）：用高斯滤波器减少图像中的噪声
2.梯度计算（**Gradient computation**）：计算每个像素的梯度大小和方向（可以用sobel算子）
3.非极大值抑制（**Non-maximum suppression**）：抑制不属于边缘的像素（将每个像素的大小与其八领域内的像素大小进行对比，如果是局部最大值，就保留，反之置为0）
4.双重阈值处理（**Double thresholding**）：设置两个阈值，高阈值和低阈值。如果像素的梯度大小高于高阈值，则认为是强边缘，如果像素梯度大小小于低阈值，则置为0。如果像素梯度大小介于二者中间，则认为是弱边缘
5.连接边缘（**Edge tracking by hysteresis**）：遍历每一个强边缘，将其八领域内的弱边缘与之连接，形成一组连续的曲线

Canny边缘检测被认为是最优的，因为它被设计为最小化检测到的假边缘的数量，同时最大化检测到的真边缘的数量。它通过使用高斯平滑、梯度计算、非最大抑制和迟滞阈值的组合来实现这一点。这些步骤共同作用于抑制噪声和像素强度的微小变化，同时保留图像中的强边缘。

<table>
<colgroup>
<col style="width: 51%" />
<col style="width: 48%" />
</colgroup>
<thead>
<tr class="header">
<th><p>2020-J-2c</p>
<p>Outline the steps involved in the Canny edge detection process.</p>
<p>In what sense in Canny edge detection optimal</p></th>
<th><p>2019-J-3c</p>
<p>（类似）List and explain the four steps involved in the Canny edge</p>
<p>detector. In terms of edge detection, what trade-off does the</p>
<p>detector try to optimize?</p>
<p></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1. 用高斯的导数过滤图像</p>
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
<p></p></td>
<td><p>1. Filter image with derivative of Gaussian</p>
<p>2. Find magnitude and orientation of gradient</p>
<p>3. Non-maximum suppression:</p>
<blockquote>
<p>• Thin wide “ridges” down to single pixel width</p>
</blockquote>
<p>4. Linking and thresholding (hysteresis):</p>
<blockquote>
<p>• Define two thresholds: low and high</p>
<p>• Use the high threshold to start edge curves and the low threshold to continue them</p>
</blockquote></td>
</tr>
<tr class="even">
<td><p>Canny edge detection is considered to be optimal because it is <strong>designed to minimize the number of false edges detected while simultaneously maximizing the number of true edges detected.</strong></p>
<p>These steps work together to <strong>suppress noise and small variations in pixel intensity, while simultaneously preserving the strong edges in the image.</strong></p></td>
<td>Canny边缘检测被认为是最优的，因为它被设计为最小化检测到的假边缘的数量，同时最大化检测到的真边缘的数量。它通过使用高斯平滑、梯度计算、非最大抑制和迟滞阈值的组合来实现这一点。这些步骤共同作用于抑制噪声和像素强度的微小变化，同时保留图像中的强边缘。</td>
</tr>
<tr class="odd">
<td><p>The Canny edge detection process consists of the following steps:</p>
<p></p>
<p><strong>Noise reduction:</strong> <strong>Reduce noise</strong> in the image using a Gaussian filter.</p>
<p></p>
<p><strong>Gradient computation:</strong> The gradient of the image is computed <strong>using a Sobel operator</strong> or similar method. This step calculates <strong>the magnitude and direction of the gradient at each pixel,</strong> which provides information about the edges in the image.</p>
<p></p>
<p><strong>Non-maximum suppression:</strong> After the gradient has been computed, the algorithm applies non-maximum <strong>suppression to suppress any pixels that are not part of an edge.</strong> This step involves comparing the gradient magnitude at each pixel to the gradient magnitudes of its neighbors and setting the pixel to zero if it is not a local maximum.</p>
<p></p>
<p><strong>Double thresholding:</strong> In this step, the algorithm applies <strong>two thresholds</strong> to the gradient magnitude image. <strong>Pixels with a gradient magnitude above the higher threshold are considered to be strong edges, while pixels with a gradient magnitude between the two thresholds are considered to be weak edges. Pixels with a gradient magnitude below the lower threshold are set to zero.</strong></p>
<p></p>
<p><strong>Edge tracking by hysteresis:</strong> Finally, the algorithm <strong>tracks the strong edges and connects them to the weak edges that are connected to them</strong>, resulting in a set of continuous edge curves. This step is known as hysteresis thresholding.</p></td>
<td><p>Canny边缘检测过程包括以下步骤。</p>
<p></p>
<p>降噪。 使用高斯滤波器减少图像中的噪声。</p>
<p></p>
<p>梯度计算。使用Sobel算子或类似方法计算图像的梯度。这一步计算每个像素的梯度的大小和方向，从而提供关于图像中的边缘的信息。</p>
<p></p>
<p>非最大限度的压制。在计算出梯度后，该算法应用非最大抑制法来抑制不属于边缘的任何像素。这一步包括将每个像素的梯度大小与它的邻居的梯度大小进行比较，如果该像素不是局部最大值，则将其设置为零。</p>
<p></p>
<p>双重阈值处理。在这一步，算法对梯度图像应用两个阈值。梯度大小高于高阈值的像素被认为是强边缘，而梯度大小在两个阈值之间的像素被认为是弱边缘。梯度大小低于低阈值的像素被设置为零。</p>
<p></p>
<p>通过滞后进行边缘跟踪。最后，该算法追踪强边缘，并将它们与与之相连的弱边缘连接起来，从而形成一组连续的边缘曲线。这个步骤被称为滞后阈值处理。</p></td>
</tr>
</tbody>
</table>

