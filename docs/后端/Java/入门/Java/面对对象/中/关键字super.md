---
title: 关键字super
updated: 2020-08-07T22:51:13.0000000+08:00
created: 2020-08-07T16:19:12.0000000+08:00
---

## 关键字super
### 一、关键字super
1、 super关键字的使用
super理解为：父类的
super可以用来调用：属性、方法、构造器
super的使用：调用属性和方法
2、注意
在子类的方法或构造器中。通过使用"super.属性"或"super.方法"的方式，显式的调用父类中声明的属性或方法。但是，通常情况下，我们习惯省略"super."
特殊情况：当**子类和父类**中定义了**同名的属性**时，我们要想在**子类中调用父类中声明的属性**，则必须显式的使用"**super.属性**"的方式，表明调用的是父类中声明的属性。
特殊情况：当子类重写了父类中的方法以后，我们想在子类的方法中调用父类中被重写的方法时，则必须显式的使用"super.方法"的
3、this和super的区别
![image1](../../assets/190f6fddf4524084bb48474bb4398216.png)
4、super调用构造器
我们可以在子类的构造器中显式的使用"super(形参列表)"的方式，调用父类中声明的指定的构造器
**"super(形参列表)"的使用，必须声明在子类构造器的首行！**
在类的构造器中，针对于**"this(形参列表)"或"super(形参列表)"只能二选一，不能同时出现**
在构造器的首行，没有显式的声明"this(形参列表)"或"super(形参列表)"，则**默认调用的是父类中空参的构造器：super()**
在类的多个构造器中，**至少有一个类的构造器中使用了"super(形参列表)"，调用父类中的构造器**

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>package com.atguigu.java3;</p>
<p></p>
<p>public class Person {</p>
<p>String name;</p>
<p>int age;</p>
<p>int id = 1001;//身份证号</p>
<p></p>
<p>public Person(){</p>
<p>System.out.println("我无处不在！");</p>
<p>}</p>
<p></p>
<p>public Person(String name){</p>
<p>this.name = name;</p>
<p>}</p>
<p></p>
<p>public Person(String name,int age){</p>
<p>this(name);</p>
<p>this.age = age;</p>
<p>}</p>
<p></p>
<p>public void eat(){</p>
<p>System.out.println("人：吃饭");</p>
<p>}</p>
<p>public void walk(){</p>
<p>System.out.println("人：走路");</p>
<p>}</p>
<p>}</p>
<p></p>
<p>public class Student extends Person{</p>
<p></p>
<p>String major;</p>
<p>int id = 1002;//学号</p>
<p></p>
<p>public Student(){</p>
<p>super();</p>
<p>}</p>
<p>public Student(String major){</p>
<p>super();</p>
<p>this.major = major;</p>
<p>}</p>
<p></p>
<p>public Student(String name,int age,String major){</p>
<p>//this.name = name;</p>
<p>//this.age = age;</p>
<p>super(name,age);</p>
<p>this.major = major;</p>
<p>}</p>
<p></p>
<p>@Override</p>
<p>public void eat() {</p>
<p>System.out.println("学生：多吃有营养的食物");</p>
<p>}</p>
<p></p>
<p>public void study(){</p>
<p>System.out.println("学生：学习知识");</p>
<p>this.eat();</p>
<p>super.eat();</p>
<p>walk();</p>
<p>}</p>
<p></p>
<p>public void show(){</p>
<p>System.out.println("name = " + name + ", age = " + age);</p>
<p>System.out.println("id = " + this.id);</p>
<p>System.out.println("id = " + super.id);</p>
<p>}</p>
<p>}</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
