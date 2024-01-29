---
title: 12-Bridge Pattern
updated: 2024-01-29T12:56:47.0000000+08:00
created: 2021-12-13T10:08:56.0000000+08:00
---

## 1，定义
| 官方的 |                                                                                 |
|--------|----------------------------------------------------------------------------------|
| 通俗的 | 将抽象部分与它的实现部分分离，使它们都可以独立的变化。而不会直接影响到其他部分。 |

![image1](../../assets/242afbf15ab84eada4b2c29fad9013d0.png)

![image2](../../assets/78569b5fd4404f3fb1cf288875d251cb.png)

桥接模式解决了多层继承的结构，处理多维度变化的场景，将各个维度设计成独立的继承结构。使各个维度可以独立的扩展在抽象层建立联系。

最终类图如下：
![image3](../../assets/d02c828be16c49d782f887d2e7f7e7d0.png)

## 2，各类含义，UML

## 3，代码

<table>
<colgroup>
<col style="width: 43%" />
<col style="width: 56%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image4](../../assets/570cdd2891ca433d8696b34578f6ded7.png)</p>
<p></p></th>
<th><p>![image5](../../assets/df5671f85966407890d3e5c06768e31e.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
![image6](../../assets/76ec15bf63b541c88d009c4be7507814.png)

![image7](../../assets/d9c7bde23b3644e28b6d5608d6136da6.png)
例子2
![image8](../../assets/5145a3a9f00c4d1c8e8f08494c4a2845.png)

例子3
![image9](../../assets/96346ece8c3f420a9f69356819281ed7.png)

![image10](../../assets/aed2689fc084458dac62aaa0740b9974.png)

![image11](../../assets/10e41d59d7a64d0f860ab438c8ca8e1b.png)

![image12](../../assets/0895e31eef7c4a89aad2bcc2af25f6a9.png)

## 4，优缺点
优点： 1、抽象和实现的分离。 2、优秀的扩展能力。 3、实现细节对客户透明。

缺点：桥接模式的引入会增加系统的理解与设计难度，由于聚合关联关系建立在抽象层，要求开发者针对抽象进行设计与编程。

## 5，适用场景
![image13](../../assets/11fd25155dea47c5a76992c1aa751697.png)

![image14](../../assets/0ed47c403b0d4d4da4d9d711935ee573.png)

