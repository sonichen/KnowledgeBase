---
title: System类
updated: 2020-09-08T08:08:27.0000000+08:00
created: 2020-09-07T13:19:51.0000000+08:00
---

1， System类代表系统，系统级的很多属性和控制方法都放置在该类的内部。 该类位于java.lang包,
2，由于该类的构造器是private的，所以**无法创建该类的对象**。
3，成员变量
Ø System类内部包含in、out和err三个成员变量，分别代表标准输入流 (键盘输入)，标准输出流(显示器)和标准错误输出流(显示器)。
4， 成员方法
Ø native long currentTimeMillis()： 该方法的作用是返回当前的计算机时间，时间的表达格式为当前计算机时 间和GMT时间(格林威治时间)1970年1月1号0时0分0秒所差的毫秒数。
Ø void exit(int status)： 该方法的作用是退出程序。其中status的值为**0代表正常退出，非零代表 异常退出**。使用该方法可以在图形界面编程中实现程序的退出功能等。
Ø void gc()： 该方法的作用是请求系统进行垃圾回收。至于系统是否立刻回收，则 取决于系统中垃圾回收算法的实现以及系统执行时的情况
Ø String getProperty(String key)： 该方法的作用是获得系统中属性名为key的属性对应的值。系统中常见 的属性名以及属性的作用如下表所示：

![image1](../../../assets/9a044db4140e45ba91c61dde49b29128.png)

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>public void test2(){</p>
<p>String javaVersion = System.getProperty("java.version");</p>
<p>System.out.println("java的version:" + javaVersion);</p>
<p>// java的version:1.8.0_221</p>
<p>String javaHome = System.getProperty("java.home");</p>
<p>System.out.println("java的home:" + javaHome);</p>
<p>// java的home:C:\Program Files\Java\jdk1.8.0_221\jre</p>
<p>String osName = System.getProperty("os.name");</p>
<p>System.out.println("os的name:" + osName);</p>
<p>// os的name:Windows 10</p>
<p>String osVersion = System.getProperty("os.version");</p>
<p>System.out.println("os的version:" + osVersion);</p>
<p>// os的version:10.0</p>
<p>String userName = System.getProperty("user.name");</p>
<p>System.out.println("user的name:" + userName);</p>
<p>// user的name:LENOVO</p>
<p>String userHome = System.getProperty("user.home");</p>
<p>System.out.println("user的home:" + userHome);</p>
<p>// user的home:C:\Users\LENOVO</p>
<p>String userDir = System.getProperty("user.dir");</p>
<p>System.out.println("user的dir:" + userDir);</p>
<p>// user的dir:D:\idea_workplace\workplace1\JavaSenior\day04</p>
<p>}</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

