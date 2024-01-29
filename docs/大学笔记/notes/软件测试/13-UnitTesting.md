---
title: 13-Unit Testing Object-Oriented Software
updated: 2024-01-27T20:36:12.0000000+08:00
created: 2020-12-18T09:20:51.0000000+08:00
---

## 一、内容

1，Object-oriented design is centered around the concepts of c**lasses,**
**inheritance, and messages.类、接口、方法**

| Classes     | objects preserve state; state control is typically distributed over an entire program. State control errors are likely to occur         |
|-------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| Inheritance | dynamic binding & complex inheritance structures are prone to faults.                                                                   |
| Message     | object-oriented programs typically have many small components and therefore more interfaces. Interface errors are more likely to occur. |

![image1](../../assets/072dc6dd72684c1699652fc393c06121.png)

## 二、步骤

1，列出input，output的范围
重叠的分区，但是根据规范，它们应该被视为独立的类。
2，组合test data
3，测试

## 三、案例

题目：
![image2](../../assets/6397384fe72f4668a78be6d8e55dea33.png)

源代码
![image3](../../assets/42711ba30c134781831d7d294cafe6d6.png)

1，列出input，output的范围
重叠的分区，但是根据规范，它们应该被视为独立的类。
Overlapped partitions, but based on the specification, they should be treated as separate classes.
![image4](../../assets/6f920eb5bbb040f9a2bcf4d5c7816571.png)

2，组合test data
![image5](../../assets/b65b78dfc9d346f181e6d93116270916.png)
3，测试
![image6](../../assets/f07bd9e1d13a4896b4412e77573d37fd.png)

## 四、Combinational Testing

用组合测试来处理该类问题
![image7](../../assets/ed70f678760c4013a59ee17fd69676e9.png)

![image8](../../assets/d5612c41e1a8400ea12d01fd3fa7adc8.png)

![image9](../../assets/86ff4d2d64b94db285c861dbb01ca676.png)

## 五、Summary

![image10](../../assets/f4bc924bf9e84d1e88737e72a950f180.png)

