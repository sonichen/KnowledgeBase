---
title: 07SIFT
updated: 2022-12-18T10:57:23.0000000+08:00
created: 2022-12-17T18:06:53.0000000+08:00
---

![image1](../../assets/d1e93b12a2cb4b0a89b8b55565266e6e.png)

拉普拉斯很好，但是太慢了，所以用高斯核
那sift做了什么来提升速度？
1、构造高斯差分空间
![image2](../../assets/834031d9168a45eca522dd149912fe0f.png)

![image3](../../assets/59c2d4c503ce47cfa4cc44f80778b5cc.png)

灰度变化会改变吗
![image4](../../assets/3b84a899256243cf8a7a2842604c560e.png)

对视角的变换不是不变的
要克服视角带来的问题
希望圆有自适应性

harris里面的公式
![image5](../../assets/a5be9bbd1c9f4c8482154d137d0fd283.png)

<table>
<colgroup>
<col style="width: 49%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image6](../../assets/936514bd576c491fa5317f7bf5757e26.png)</p>
<p></p></th>
<th><p>![image7](../../assets/548021f2cadd48d59ea7e5a58d90b0b1.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

![image8](../../assets/ed9e94bc76f541a7b731be509237a638.png)

![image9](../../assets/0511a28eeae44f77818a44c7d04fa644.png)

![image10](../../assets/6fc973acfa2e4d9cab80483a6a73c078.png)

![image11](../../assets/be1c370d62eb4d8c900fd170c5ee3dab.png)

![image12](../../assets/8398d04c3a2442caa066f5cf2586b7cb.png)

