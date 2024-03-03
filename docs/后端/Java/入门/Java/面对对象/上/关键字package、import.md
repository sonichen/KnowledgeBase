---
title: 关键字package、import
updated: 2020-08-07T18:04:42.0000000+08:00
created: 2020-08-04T14:09:28.0000000+08:00
---

## 关键字package、import
### 一、关键字package
1、package语句作为**Java源文件的第一条语句**，指明该文件中定义的类所在的包
它的格式为：
| package 顶层包名.子包名 ; |
|---------------------------|
2、包，属于标识符，遵循标识符的命名规则、规范(xxxyyyzzz)、“见名知意”
3、每"."一次，就代表一层文件目录。
补充：同一个包下，不能命名同名的接口、类；不同的包下，可以命名同名的接口、类。
4、JDK中主要的包介绍
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>1. java.lang----包含一些Java语言的核心类，如String、Math、Integer、 System和 Thread，提供常用功能</p>
<p>2. java.net----包含执行与网络相关的操作的类和接口。</p>
<p>3. java.io ----包含能提供多种输入/输出功能的类。</p>
<p>4. java.util----包含一些实用工具类，如定义系统特性、接口的集合框架类、使用与日 期日历相关的函数。</p>
<p>5. java.text----包含了一些java格式化相关的类</p>
<p>6. java.sql----包含了java进行JDBC数据库编程的相关类/接口 7. java.awt----包含了构成抽象窗口工具集（abstract window toolkits）的多个类，这 些类被用来构建和管理应用程序的图形用户界面(GUI)。 B/S C/S</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
### 二、关键字import
1、为使用定义在不同包中的Java类，需用import语句来引入指定包层次下所需要的类 或全部类(.\*)。
import语句告诉编译器到哪里去寻找类。
2、语法格式：
| import 包名. 类名; |
|--------------------|
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>import pack1.pack2.Test;</p>
<p>//import pack1.pack2.*;表示引入pack1.pack2包中的所有结构</p>
<p>public class PackTest{</p>
<p>public static void main(String args[]){</p>
<p>Test t = new Test(); //Test类在pack1.pack2包中定义</p>
<p>t.display();</p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
3、注意
1\. 在源文件中显式的使用import结构导入指定包下的类、接口
2\. 声明在包的声明和类的声明之间
3\. 如果需要导入多个结构，则并列写出即可
4\. 可以使用"xxx.\*"的方式，表示可以导入xxx包下的所有结构
5\. 如果使用的类或接口是java.lang包下定义的，则可以省略import结构
6\. 如果使用的类或接口是本包下定义的，则可以省略import结构
7\. 如果在源文件中，使用了不同包下的同名的类，则必须至少有一个类需要以全类名的方式显示。
8\. 使用"xxx.\*"方式表明可以调用xxx包下的所有结构。但是如果使用的是xxx子包下的结构，则仍需要显式导入
9\. import static:导入指定类或接口中的静态结构:属性或方法。
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>public class PackageImportTest {</p>
<p>public static void main(String[] args) {</p>
<p></p>
<p>String info = Arrays.toString(new int[]{1,2,3});</p>
<p>//全类名的方式显示</p>
<p><mark>com.atguigu.exer3.Account acct1 = new com.atguigu.exer3.Account(1000,2000,0.0123);</mark></p>
<p></p>
<p>Date date = new Date();</p>
<p>java.sql.Date date1 = new java.sql.Date(5243523532535L);</p>
<p></p>
<p>Dog dog = new Dog();</p>
<p></p>
<p>Field field = null;</p>
<p></p>
<p>out.println("hello");</p>
<p></p>
<p>long num = round(123.434);</p>
<p>}</p>
<p>}</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
