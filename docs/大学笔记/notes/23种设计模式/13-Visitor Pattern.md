---
title: 13-Visitor Pattern
updated: 2024-01-29T12:57:15.0000000+08:00
created: 2021-12-13T10:07:48.0000000+08:00
---

## 1，定义
| 官方的 | 表示一个作用于某对象结构中的各元素的操作。它使你可以在不改变各元素的类的前提下==定义作用于这些元素的新操作。== |
|--------|--------------------------------------------------------------------------------------------------------------------------------------|
| 通俗的 | 针对不同对象做一些不同的操作，则可以使用访问者模式。                                                                                 |
## 2，各类含义，UML
![image1](../../assets/db8dd1e9a69c4c24909b28d793467cfc.png)
我们将创建一个定义接受操作的 ComputerPart 接口。
Keyboard、Mouse、Monitor 和 Computer 是实现了 ComputerPart 接口的实体类。
我们将定义另一个接口 ComputerPartVisitor，它定义了访问者类的操作。Computer 使用实体访问者来执行相应的动作。

VisitorPatternDemo，我们的演示类使用 Computer、ComputerPartVisitor 类来演示访问者模式的用法。

## 3，代码
例子1
![image2](../../assets/7e095a25557447cc8ccd16e61fdce33a.png)

![image3](../../assets/9d217d7cf95943d1a6db895f289b3bba.png)

![image4](../../assets/43ab89e3959946d6997683ac0afa86d6.png)

![image5](../../assets/12d611df057543c1a80d4e84e5f6d33c.png)

![image6](../../assets/47631ab9a5c9417482d25810ca9741d1.png)

例子2
![image7](../../assets/06e70185c1b441608484125ac72892f0.png)

![image8](../../assets/492edd4f62294cc8b23aa810c580a53a.png)

![image9](../../assets/b31fee98c8294c4193dd7ae1a7cd078e.png)

![image10](../../assets/872111c7e0df4697a930e9d6155fc1e7.png)

![image11](../../assets/f20803bf209e429094e6b2f9895fed96.png)

## 4，优缺点
优点：
1、符合单一职责原则。
2、优秀的扩展性。
3、灵活性。

缺点：
1、具体元素对访问者公布细节，违反了迪米特原则。
2、具体元素变更比较困难。
3、违反了依赖倒置原则，依赖了具体类，没有依赖抽象。

## 5，适用场景
XML文档解析器设计
编译器设计
复杂集合对象的处理

![image12](../../assets/6f494d545a504a34a2931daf59fd5954.png)

