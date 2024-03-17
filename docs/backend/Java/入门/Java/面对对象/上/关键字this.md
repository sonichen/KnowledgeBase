---
title: 关键字this
updated: 2020-08-07T17:59:48.0000000+08:00
created: 2020-08-04T14:09:22.0000000+08:00
---

## 关键字this
### 一、关键字this
1.this可以用来修饰、调用：属性、方法、构造器
2.this修饰属性和方法：
this理解为：当前对象 或 当前正在创建的对象
2.1 **在类的方法中**，我们可以使用"this.属性"或"this.方法"的方式，调用当前对象属性或方法。但是， 通常情况下，我们都选择省略"this."。特殊情况下，如果方法的形参和类的属性同名时，我们必须显式的使用"this.变量"的方式，表明此变量是属性，而非形参。
2.2 在**类的构造器**中，我们可以使用"this.属性"或"this.方法"的方式，调用当前正在创建的对象属性或方法。
但是，通常情况下，我们都选择省略"this."。特殊情况下，如果构造器的形参和类的属性同名时，我们必须显式使用"this.变量"的方式，表明此变量是属性，而非形参。
3\. this调用构造器
① 我们在类的构造器中，可以显式的使用"this(形参列表)"方式，调用本类中指定的其他构造器
② 构造器中不能通过"this(形参列表)"方式调用自己
③ 如果一个类中有n个构造器，则最多有 n - 1构造器中使用了"this(形参列表)"
④ 规定："this(形参列表)"必须声明在当前构造器的首行
⑤ 构造器内部，最多只能声明一个"this(形参列表)"，用来调用其他的构造器
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>class Person{</p>
<p></p>
<p>private String name;</p>
<p>private int age;</p>
<p></p>
<p></p>
<p>public Person(){</p>
<p></p>
<p>//this.eat();</p>
<p>String info = "Person初始化时，需要考虑如下的1,2,3,4...(共40行代码)";</p>
<p>System.out.println(info);</p>
<p>}</p>
<p></p>
<p>public Person(String name){</p>
<p>this();</p>
<p>this.name = name;</p>
<p></p>
<p>}</p>
<p></p>
<p>public Person(int age){</p>
<p>this();</p>
<p>this.age = age;</p>
<p></p>
<p>}</p>
<p></p>
<p>public Person(String name,int age){</p>
<p>this(age);</p>
<p>this.name = name;</p>
<p>//this.age = age;</p>
<p>//Person初始化时，需要考虑如下的1,2,3,4...(共40行代码)</p>
<p>}</p>
<p></p>
<p>public void setName(String name){</p>
<p>this.name = name;</p>
<p>}</p>
<p>public String getName(){</p>
<p>return this.name;</p>
<p>}</p>
<p>public void setAge(int age){</p>
<p>this.age = age;</p>
<p>}</p>
<p>public int getAge(){</p>
<p>return this.age;</p>
<p>}</p>
<p></p>
<p>public void eat(){</p>
<p>System.out.println("人吃饭");</p>
<p>this.study();</p>
<p>}</p>
<p>public void study(){</p>
<p>System.out.println("人学习");</p>
<p>}</p>
<p></p>
<p>}</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

