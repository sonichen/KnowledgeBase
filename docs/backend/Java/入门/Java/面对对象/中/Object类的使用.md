---
title: Object类的使用
updated: 2020-08-09T10:56:13.0000000+08:00
created: 2020-08-07T16:19:29.0000000+08:00
---

##  一、Object类
java.lang.Object类
1.Object类是所有Java类的根父类
2.如果在类的声明中未使用extends关键字指明其父类，则默认父类为java.lang.Object类
3.Object类中的功能(属性、方法)就具有通用性。属性：无
方法：equals() / toString() / getClass() /hashCode() / clone() / finalize()/wait() 、 notify()、notifyAll()
4\. Object类只声明了一个空参的构造器

## 二、equals
面试题： == 和 equals() 区别
### 1、 == 的使用：
== ：运算符
（1） 可以使用在基本数据类型变量和引用数据类型变量中
（2） 如果比较的是基本数据类型变量：比较两个变量保存的数据是否相等。（不一定类型要相同）
如果比较的是引用数据类型变量：比较两个对象的地址值是否相同.即两个引用是否指向同一个对象实体
补充： == 符号使用时，必须保证符号左右两边的变量类型一致。

### 2、equals()方法的使用：
（1） 是一个方法，而非运算符
（2） 只能适用于引用数据类型
（3） Object类中equals()的定义：
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>public boolean equals(Object obj) {</p>
<blockquote>
<p>return (this == obj);</p>
<p>}</p>
</blockquote></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
说明：Object类中定义的equals()和==的作用是相同的：比较两个对象的地址值是否相同.即两个引用是否指向同一个对象实体
4\. 像String、Date、File、包装类等都重写了Object类中的equals()方法。重写以后，比较的不是
两个引用的地址是否相同，而是比较两个对象的"实体内容"是否相同。
5\. 通常情况下，我们自定义的类如果使用equals()的话，也通常是比较两个对象的"实体内容"是否相同。
就需要对Object类中的equals()进行重写.
重写的原则：比较两个对象的实体内容是否相同.
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>public class EqualsTest {</p>
<p>public static void main(String[] args) {</p>
<p></p>
<p>//基本数据类型</p>
<p>int i = 10;</p>
<p>int j = 10;</p>
<p>double d = 10.0;</p>
<p>System.out.println(i == j);//true</p>
<p>System.out.println(i == d);//true</p>
<p></p>
<p>boolean b = true;</p>
<p>//System.out.println(i == b);</p>
<p></p>
<p>char c = 10;</p>
<p>System.out.println(i == c);//true</p>
<p></p>
<p>char c1 = 'A';</p>
<p>char c2 = 65;</p>
<p>System.out.println(c1 == c2);//true</p>
<p></p>
<p>//引用类型：</p>
<p>Customer cust1 = new Customer("Tom",21);</p>
<p>Customer cust2 = new Customer("Tom",21);</p>
<p>System.out.println(cust1 == cust2);//false</p>
<p></p>
<p>String str1 = new String("atguigu");</p>
<p>String str2 = new String("atguigu");</p>
<p>System.out.println(str1 == str2);//false</p>
<p>System.out.println("****************************");</p>
<p>System.out.println(cust1.equals(cust2));//false---&gt;true</p>
<p>System.out.println(str1.equals(str2));//true</p>
<p></p>
<p>Date date1 = new Date(32432525324L);</p>
<p>Date date2 = new Date(32432525324L);</p>
<p>System.out.println(date1.equals(date2));//true</p>
<p></p>
<p></p>
<p>}</p>
<p>}</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>package com.atguigu.java1;</p>
<p></p>
<p>public class Customer {</p>
<p></p>
<p>private String name;</p>
<p>private int age;</p>
<p>public String getName() {</p>
<p>return name;</p>
<p>}</p>
<p>public void setName(String name) {</p>
<p>this.name = name;</p>
<p>}</p>
<p>public int getAge() {</p>
<p>return age;</p>
<p>}</p>
<p>public void setAge(int age) {</p>
<p>this.age = age;</p>
<p>}</p>
<p>public Customer() {</p>
<p>super();</p>
<p>}</p>
<p>public Customer(String name, int age) {</p>
<p>super();</p>
<p>this.name = name;</p>
<p>this.age = age;</p>
<p>}</p>
<p></p>
<p>//自动生成的equals()</p>
<p>@Override</p>
<p>public boolean equals(Object obj) {</p>
<p>if (this == obj)</p>
<p>return true;</p>
<p>if (obj == null)</p>
<p>return false;</p>
<p>if (getClass() != obj.getClass())</p>
<p>return false;</p>
<p>Customer other = (Customer) obj;</p>
<p>if (age != other.age)</p>
<p>return false;</p>
<p>if (name == null) {</p>
<p>if (other.name != null)</p>
<p>return false;</p>
<p>} else if (!name.equals(other.name))</p>
<p>return false;</p>
<p>return true;</p>
<p>}</p>
<p></p>
<p></p>
<p></p>
<p>//重写的原则：比较两个对象的实体内容(即：name和age)是否相同</p>
<p>//手动实现equals()的重写</p>
<p>//@Override</p>
<p>//public boolean equals(Object obj) {</p>
<p>//</p>
<p>////System.out.println("Customer equals()....");</p>
<p>//if (this == obj) {</p>
<p>// return true;</p>
<p>// }</p>
<p>//</p>
<p>//if(obj instanceof Customer){</p>
<p>//Customer cust = (Customer)obj;</p>
<p>////比较两个对象的每个属性是否都相同</p>
<p>////if(this.age == cust.age &amp;&amp; this.name.equals(cust.name)){</p>
<p>////return true;</p>
<p>////}else{</p>
<p>////return false;</p>
<p>////}</p>
<p>//</p>
<p>////或</p>
<p>//return this.age == cust.age &amp;&amp; this.name.equals(cust.name);</p>
<p>//}else{</p>
<p>//return false;</p>
<p>//</p>
<p>//}</p>
<p>//</p>
<p>//}</p>
<p>//手动实现</p>
<p>//@Override</p>
<p>//public String toString() {</p>
<p>//return "Customer[name = " + name + ",age = " + age + "]";</p>
<p>//}</p>
<p>//自动实现</p>
<p>@Override</p>
<p>public String toString() {</p>
<p>return "Customer [name=" + name + ", age=" + age + "]";</p>
<p>}</p>
<p>}</p>
<p></p></td>
</tr>
</tbody>
</table>

## 三、toString()
1\. 当我们输出一个对象的引用时，实际上就是调用当前对象toString()
2\. Object类中toString()的定义：
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>public String toString() {</p>
<p>return getClass().getName() + "@" + Integer.toHexString(hashCode());</p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
3\. 像String、Date、File、包装类等都重写了Object类中的toString()方法。
使得在调用对象的toString()时，返回"实体内容"信息
4\. 自定义类也可以重写toString()方法，当调用此方法时，返回对象的"实体内容"
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>public class ToStringTest {</p>
<p>public static void main(String[] args) {</p>
<p></p>
<p>Customer cust1 = new Customer("Tom",21);</p>
<p>System.out.println(cust1.toString());//com.atguigu.java1.Customer@15db9742--&gt;Customer[name = Tom,age = 21]</p>
<p>System.out.println(cust1);//com.atguigu.java1.Customer@15db9742--&gt;Customer[name = Tom,age = 21]</p>
<p></p>
<p>String str = new String("MM");</p>
<p>System.out.println(str);//MM</p>
<p>}</p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## 四、clone方法
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>package com.atguigu.java1;</p>
<p></p>
<p>//Object类的clone()的使用</p>
<p>public class CloneTest {</p>
<p>public static void main(String[] args) {</p>
<p>Animal a1 = new Animal("花花");</p>
<p>try {</p>
<p>Animal a2 = (Animal) a1.clone();</p>
<p>System.out.println("原始对象：" + a1);</p>
<p>a2.setName("毛毛");</p>
<p>System.out.println("clone之后的对象：" + a2);</p>
<p>} catch (CloneNotSupportedException e) {</p>
<p>e.printStackTrace();</p>
<p>}</p>
<p>}</p>
<p>}</p>
<p></p>
<p>class Animal implements Cloneable{</p>
<p>private String name;</p>
<p></p>
<p>public Animal() {</p>
<p>super();</p>
<p>}</p>
<p></p>
<p>public Animal(String name) {</p>
<p>super();</p>
<p>this.name = name;</p>
<p>}</p>
<p></p>
<p>public String getName() {</p>
<p>return name;</p>
<p>}</p>
<p></p>
<p>public void setName(String name) {</p>
<p>this.name = name;</p>
<p>}</p>
<p></p>
<p>@Override</p>
<p>public String toString() {</p>
<p>return "Animal [name=" + name + "]";</p>
<p>}</p>
<p></p>
<p>@Override</p>
<p>protected Object clone() throws CloneNotSupportedException {</p>
<p>// TODO Auto-generated method stub</p>
<p>return super.clone();</p>
<p>}</p>
<p></p>
<p>}</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
## 五、finalize方法
在对象释放之前被调用
