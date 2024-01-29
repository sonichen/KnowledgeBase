---
title: 05Harris角点检测
updated: 2024-01-29T12:31:11.0000000+08:00
created: 2022-12-16T11:19:28.0000000+08:00
---

局部特征
## 1、全景拍照
常应用：全景拍照（拍很多照片，连起来，形成全景）
怎么拼起来？（要解决的问题

怎么办
1.提取特征
2.匹配特征
3.拼接图片
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th>![image1](../../assets/2735d64a96c5485ead6df6fdd2f44010.png)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>![image2](../../assets/1557eff1daa04224abed6739bb66648a.png)</p>
<p></p></td>
</tr>
<tr class="even">
<td>![image3](../../assets/c666fe1f8a4d4153a2242653ee4ba4be.png)</td>
</tr>
<tr class="odd">
<td>![image4](../../assets/46c2dd6ec9e04c3c9ca3cc15e290464f.png)</td>
</tr>
</tbody>
</table>

好的特征
- 重复性:两个图形的重复部分要多
- 显著性：特征要有意义
- 计算起来要高效
- 局部性

总结，要干什么
1.找特征，有特定的点
2.找匹配关系
3.拼接图像

![image5](../../assets/3ab18cbed8e34a828b0e4cc4ebb4fd64.png)

## 2、角点检测
什么是角点：在两个及以上的方向有变化的点
角落是可重复的和独特的

怎么识别角点
我们应该可以很容易地识别要点，向任何方向移动窗口都会有很大的强度变化

看窗体里面的内容变不变
![image6](../../assets/3e9858daf992426596afe58e45fd895b.png)

![image7](../../assets/1c6b6b3ff0b045aa8234ff4e1c60c601.png)

![image8](../../assets/910258eec4094cb29a169189b4a18997.png)

![image9](../../assets/5e3bb08a62ff417493e5cdd74686f899.png)
转换，为了找E(u,v)与u,v关联
![image10](../../assets/00d9fc61ab884e32b11dcf2ae79062e3.png)

![image11](../../assets/64808711c8bb4aa9825117971848e647.png)

![image12](../../assets/a8ca4af6765a4a9bb6d65eb61d00128e.png)
==过程听不太懂不理解==
![image13](../../assets/7b198fa6394348bfb8d98dac1643edb6.png)

结论
![image14](../../assets/ae3f46bcae834188a4ca295571ac9b2b.png)
更简洁的
![image15](../../assets/d6827ee096f147158c8514a8fb6d5054.png)
<table>
<colgroup>
<col style="width: 32%" />
<col style="width: 67%" />
</colgroup>
<thead>
<tr class="header">
<th><p>1.计算每个像素的高斯偏导</p>
<p>2.计算每一个像素的二阶矩矩阵</p>
<p>3.计算R值</p>
<p>4.门限R</p>
<p>5.非极大值抑制</p></th>
<th><p>Harris detector: Steps</p>
<p>1. Compute Gaussian derivatives at each pixel</p>
<p>2. Compute second moment matrix M in a Gaussian window around each pixel</p>
<p>3. Compute corner response function R</p>
<p>4. Threshold R</p>
<p>5. Find local maxima of response function</p>
<p>(nonmaximum suppression)</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

![image16](../../assets/16ab63a69ae4412ea2d9baabfad2ed8a.png)

![image17](../../assets/8df1ee18b6284dcab173a6055c17594f.png)

\- 我们希望角落的位置对光度测量的不变性 变化和几何变化的协变性。
\- 不变性：图像被转换后，角的位置不会改变

\- 协变性：如果我们有同一图像的两个转换版本。特征应该在相应的位置被检测到

==Affine intensity change==（后续未看
