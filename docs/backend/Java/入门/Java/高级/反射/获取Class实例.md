---
title: 获取Class实例
updated: 2020-09-23T21:11:53.0000000+08:00
created: 2020-09-23T21:09:28.0000000+08:00
---

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>@Test</p>
<p>public void test3() throws ClassNotFoundException {</p>
<p>//方式一：调用运行时类的属性：.class</p>
<p>Class clazz1=Person.class;</p>
<p>System.out.println(clazz1);</p>
<p>//方式二：通过运行时类的对象,调用getClass()</p>
<p>Person p1=new Person();</p>
<p>Class clazz2=p1.getClass();</p>
<p>System.out.println(clazz2);</p>
<p></p>
<p>//方式三：调用Class的静态方法：forName(String classPath)</p>
<p>Class clazz3=Class.forName("java01.Person");</p>
<p>System.out.println(clazz3);</p>
<p>//方式四：使用类的加载器：ClassLoader</p>
<p>ClassLoader classLoader=ReflectionTest.class.getClassLoader();</p>
<p>Class clazz4=classLoader.loadClass("java01.Person");</p>
<p>System.out.println(clazz4);</p>
<p></p>
<p>System.out.println(clazz1==clazz4);//true</p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
