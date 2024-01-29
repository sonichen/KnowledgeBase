---
title: 4-Boundary Value Testing 边界测试
updated: 2021-06-09T15:18:50.0000000+08:00
created: 2020-09-25T09:13:53.0000000+08:00
---

# 4-Boundary Value Testing 边界测试
## 一，基础知识

1，问题

定义域定义模糊，存在漏洞，under-defined processing.；
自相矛盾the over-defined processing.

![image1](../../assets/702f979fddda4afe8a29f7dc8fac5a17.png)

2，Boundary Value Testing
许多缺陷隐藏在边界处

## 二，步骤

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>1，根据题目，确定input和output的个数，写出input的取值范围和output的所有可能性</p>
<p>2，<strong>取值范围的边界值</strong>作为测试案例，列出test case【可以先列出各种范围，易于找到边界】</p>
<p>3,写出Test data，在这里边界值作为测试数据</p>
<p>注意：先列出合法的案例，覆盖所有可能性</p>
<p>非法的放在最后一起测试，</p>
<p>4，测试</p>
<p>5，修改</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>


案例
![image2](assets\58a868c7143f48f0b070f0dc72114aac.png)

1，根据题目，确定input和output的个数，写出input的取值范围和output的所有可能性
![image3](assets\72d85e2ccf5e444baa3f6474ad461efa.png)

2，取值范围的边界值作为测试案例，列出test case【可以先列出各种范围，易于找到边界】
![image4](assets\6f32bc7063274eccbbdb1727d398b34d.png)

3,写出Test data，在这里边界值作为测试数据

![image5](assets\98f6759119b64f12b8e26c3b4f02ef82.png)

4，测试
![image6](assets\2a2bfb7a5a2b4e5d8478cd5bd87d5355.png)
5，修改错误


案例2
![image7](assets\532becee022f42bc80fe8df88fd5e0df.png)
1，根据题目，确定input和output的个数，写出input的取值范围和output的所有可能性

![image8](assets\f0b08c546ca549ff992307e05340effa.png)

2，取值范围的边界值作为测试案例，列出test case【可以先列出各种范围，易于找到边界】
3,写出Test data，在这里边界值作为测试数据

![image9](assets\af15220ece37452b9d2523bd70dcf8a1.png)

3，测试
![image10](assets\c201d83aedc94ef8b367bc2bc8be89fc.png)

4，根据错误的测试案例找到错误
![image11](assets\cfabf0c9b29c4074ad35f40f9634cf13.png)

5，修改
![image12](assets\69e0f1fe0bb14960a87a9c148588eaed.png)





## 三，补充

1，“Create test cases for each boundary value by choosing one point on the boundary, one point just below the boundary, and one point just above the boundary.”
要判断断点的前或后，对其测试

2，对极限的数，会循环回开头

![image13](../../assets/4a79cb84475146fbaa5992c30fefe754.png)
3， Need to cover all the equivalence classes

5，常见的边界值问题
![image14](../../assets/5a9f80be575c4c3ca60b9e8f5f3f39e4.png)
经常发生！

