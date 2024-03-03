---
title: 关键字final
updated: 2020-08-11T12:06:54.0000000+08:00
created: 2020-08-11T09:11:47.0000000+08:00
---

# 关键字final
2020年8月11日
9:11

## 一、关键字final
1\. final可以用来修饰的结构：**类、方法、变量**
2\. final 用来修饰一个类:**此类不能被其他类所继承**。比如：String类、System类、StringBuffer类
3\. final 用来修饰方法：表明此方法不可以被重写。比如：Object类中getClass();
4\. final 用来修饰变量：此时的"变量"就称为是一个**常量**
--final修饰属性：可以考虑赋值的位置有：**显式初始化、代码块中初始化、构造器中初始化**

--final修饰局部变量：尤其是使用final修饰形参时，表明此形参是一个常量。当我们调用此方法时，给常量形参赋一个实参。一旦赋值以后，就只能在方法体内使用此形参，但不能进行重新赋值。
5.static final 用来修饰属性：全局常量

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>public class FinalTest {</p>
<p></p>
<p>final int WIDTH = 0;</p>
<p>final int LEFT;</p>
<p>final int RIGHT;</p>
<p>//final int DOWN;</p>
<p></p>
<p>{</p>
<p>LEFT = 1;</p>
<p>}</p>
<p></p>
<p>public FinalTest(){</p>
<p>RIGHT = 2;</p>
<p>}</p>
<p></p>
<p>public FinalTest(int n){</p>
<p>RIGHT = n;</p>
<p>}</p>
<p></p>
<p>//public void setDown(int down){</p>
<p>//this.DOWN = down;</p>
<p>//}</p>
<p></p>
<p></p>
<p>public void doWidth(){</p>
<p>//width = 20;</p>
<p>}</p>
<p></p>
<p></p>
<p>public void show(){</p>
<p>final int NUM = 10;//常量</p>
<p>//NUM += 20;</p>
<p>}</p>
<p></p>
<p>public void show(final int num){</p>
<p>//num = 20;//编译不通过</p>
<p>System.out.println(num);</p>
<p>}</p>
<p></p>
<p></p>
<p>public static void main(String[] args) {</p>
<p></p>
<p>int num = 10;</p>
<p></p>
<p>num = num + 5;</p>
<p></p>
<p>FinalTest test = new FinalTest();</p>
<p>//test.setDown(3);</p>
<p></p>
<p>test.show(10);</p>
<p>}</p>
<p>}</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>package basic.day14;</p>
<p></p>
<p>public class Test {</p>
<p></p>
<p>public static void main(String[] args) {</p>
<p>// TODO Auto-generated method stub</p>
<p>new Leaf();</p>
<p>System.out.println();</p>
<p>new Leaf();</p>
<p>}</p>
<p></p>
<p>}</p>
<p>class Root{</p>
<p>static{</p>
<p>System.out.println("Root的静态初始化块");</p>
<p>}</p>
<p>{</p>
<p>System.out.println("Root的普通初始化块");</p>
<p>}</p>
<p>public Root(){</p>
<p>super();</p>
<p>System.out.println("Root的无参数的构造器");</p>
<p>}</p>
<p>}</p>
<p>class Mid extends Root{</p>
<p>static{</p>
<p>System.out.println("Mid的静态初始化块");</p>
<p>}</p>
<p>{</p>
<p>System.out.println("Mid的普通初始化块");</p>
<p>}</p>
<p>public Mid(){</p>
<p>super();</p>
<p>System.out.println("Mid的无参数的构造器");</p>
<p>}</p>
<p>public Mid(String msg){</p>
<p>//通过this调用同一类中重载的构造器</p>
<p>this();</p>
<p>System.out.println("Mid的带参数构造器，其参数值："</p>
<p>+ msg);</p>
<p>}</p>
<p>}</p>
<p>class Leaf extends Mid{</p>
<p>static{</p>
<p>System.out.println("Leaf的静态初始化块");</p>
<p>}</p>
<p>{</p>
<p>System.out.println("Leaf的普通初始化块");</p>
<p>}</p>
<p>public Leaf(){</p>
<p>//通过super调用父类中有一个字符串参数的构造器</p>
<p>super("尚硅谷");</p>
<p>System.out.println("Leaf的构造器");</p>
<p>}</p>
<p>}</p>
<p></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Root的静态初始化块</p>
<p>Mid的静态初始化块</p>
<p>Leaf的静态初始化块</p>
<p>Root的普通初始化块</p>
<p>Root的无参数的构造器</p>
<p>Mid的普通初始化块</p>
<p>Mid的无参数的构造器</p>
<p>Mid的带参数构造器，其参数值：尚硅谷</p>
<p>Leaf的普通初始化块</p>
<p>Leaf的构造器</p>
<p></p>
<p>Root的普通初始化块</p>
<p>Root的无参数的构造器</p>
<p>Mid的普通初始化块</p>
<p>Mid的无参数的构造器</p>
<p>Mid的带参数构造器，其参数值：尚硅谷</p>
<p>Leaf的普通初始化块</p>
<p>Leaf的构造器</p></td>
</tr>
</tbody>
</table>
