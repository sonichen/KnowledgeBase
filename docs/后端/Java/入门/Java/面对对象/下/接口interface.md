---
title: 接口interface
updated: 2020-09-23T20:38:54.0000000+08:00
created: 2020-08-11T09:12:13.0000000+08:00
---

接口interface
2020年8月11日
9:12

interface:接口
接口（英文：Interface），在JAVA编程语言中是一个抽象类型，是抽象方法的集合，接口通常以interface来声明。一个类通过继承接口的方式，从而来继承接口的抽象方法。
接口并不是类，编写接口的方式和类很相似，但是它们属于不同的概念。类描述对象的属性和方法。接口则包含类要实现的方法。
**除非实现接口的类是抽象类，否则该类要定义接口中的所有方法。**
接口无法被实例化，但是可以被实现。一个实现接口的类，必须实现接口内所描述的所有方法，否则就必须声明为抽象类。另外，在 Java 中，接口类型可用来声明一个变量，他们可以成为一个空指针，或是被绑定在一个以此接口实现的对象。
**

1.使用说明：
1.接口使用interface来定义
\* 2.Java中，接口和类是并列的两个结构
\* 3.如何定义接口：定义接口中的成员
\* 
\* 3.1 JDK7及以前：只能定义全局常量和抽象方法
\* \>全局常量：**public static final**的.但是书写时，可以省略不写
\* \>抽象方法：public abstract的
\* 
\* 3.2 JDK8：除了定义全局常量和抽象方法之外，还可以定义静态方法、默认方法（略
\*
\* 4. **接口中不能定义构造器的！意味着接口不可以实例化**
\*
\* 5. Java开发中，接口通过让类去实现(implements)的方式来使用.
\* 如果实现类覆盖了接口中的所抽象方法，则此实现类就可以实例化
\* 如果实现类没覆盖接口中所的抽象方法，则此实现类仍为一个抽象类
\*
\* 6. Java类可以实现多个接口 ---\>弥补了Java单继承性的局限性
\* 格式：class AA extends BB implements CC,DD,EE
\*
\* 7. 接口与接口之间可以继承，而且可以多继承
\*
\* \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*
\* 8. 接口的具体使用，体现多态性
\* 9. 接口，实际上可以看做是一种规范

2.举例：
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p></p>
<p>class Computer{</p>
<blockquote>
<p></p>
<p>public void transferData(USB usb){//USB usb = new Flash();</p>
<p>usb.start();</p>
<p></p>
<p>System.out.println("具体传输数据的细节");</p>
<p></p>
<p>usb.stop();</p>
<p>}</p>
<p></p>
<p></p>
</blockquote>
<p>}</p>
<p></p>
<p>interface USB{</p>
<blockquote>
<p>//常量：定义了长、宽、最大最小的传输速度等</p>
<p></p>
<p>void start();</p>
<p></p>
<p>void stop();</p>
<p></p>
</blockquote>
<p>}</p>
<p></p>
<p>class Flash implements USB{</p>
<p></p>
<blockquote>
<p>@Override</p>
<p>public void start() {</p>
<p>System.out.println("U盘开启工作");</p>
<p>}</p>
</blockquote>
<p></p>
<blockquote>
<p>@Override</p>
<p>public void stop() {</p>
<p>System.out.println("U盘结束工作");</p>
<p>}</p>
<p></p>
</blockquote>
<p>}</p>
<p></p>
<p>class Printer implements USB{</p>
<blockquote>
<p>@Override</p>
<p>public void start() {</p>
<p>System.out.println("打印机开启工作");</p>
<p>}</p>
</blockquote>
<p></p>
<blockquote>
<p>@Override</p>
<p>public void stop() {</p>
<p>System.out.println("打印机结束工作");</p>
<p>}</p>
<p></p>
</blockquote>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
体会：
\* 1.接口使用上也满足多态性
\* 2.接口，实际上就是定义了一种规范
\* 3.开发中，体会面向接口编程！
3.体会面向接口编程的思想

面向接口编程：我们在应用程序中，调用的结构都是JDBC中定义的接口，不会出现具体某一个
数据库厂商的API。
4.Java8中关于接口的新规范
//知识点1：接口中定义的静态方法，只能通过接口来调用。

//知识点2：通过实现类的对象，可以调用接口中的默认方法。
//如果实现类重写了接口中的默认方法，调用时，仍然调用的是重写以后的方法

//知识点3：如果子类(或实现类)继承的父类和实现的接口中声明了同名同参数的默认方法，那么子类在没重写此方法的情况下，默认调用的是父类中的同名同参数的方法。--\>类优先原则
//知识点4：如果实现类实现了多个接口，而这多个接口中定义了同名同参数的默认方法，
//那么在实现类没重写此方法的情况下，报错。--\>接口冲突。
//这就需要我们必须在实现类中重写此方法
//知识点5：如何在子类(或实现类)的方法中调用父类、接口中被重写的方法
public void myMethod(){

method3();//调用自己定义的重写的方法

super.method3();//调用的是父类中声明的

//调用接口中的默认方法

CompareA.super.method3();

CompareB.super.method3();

}
5.面试题：
抽象类和接口的异同？
相同点：不能实例化；都可以包含抽象方法的。
不同点：
1）把抽象类和接口(java7,java8,java9)的定义、内部结构解释说明
2）类：单继承性 接口：多继承
类与接口：多实现
