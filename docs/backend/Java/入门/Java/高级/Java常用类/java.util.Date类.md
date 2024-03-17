---
title: java.util.Date类
updated: 2020-09-05T23:09:22.0000000+08:00
created: 2020-09-05T17:27:59.0000000+08:00
---

java.util.Date类
\|---java.sql.Date类

1.两个构造器的使用
\>构造器一：Date()：创建一个对应当前时间的Date对象
\>构造器二：创建指定毫秒数的Date对象
2.两个方法的使用
\>toString():显示当前的年、月、日、时、分、秒
\>getTime():获取当前Date对象对应的毫秒数。（时间戳）

3\. java.sql.Date对应着数据库中的日期类型的变量
\>如何实例化
\>如何将java.util.Date对象转换为java.sql.Date对象
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>@Test</p>
<p>public void test2(){</p>
<p>//构造器一：Date()：创建一个对应当前时间的Date对象</p>
<p>Date date1 = new Date();</p>
<p>System.out.println(date1.toString());//Sat Feb 16 16:35:31 GMT+08:00 2019</p>
<p></p>
<p>System.out.println(date1.getTime());//1550306204104</p>
<p></p>
<p>//构造器二：创建指定毫秒数的Date对象</p>
<p>Date date2 = new Date(155030620410L);</p>
<p>System.out.println(date2.toString());</p>
<p></p>
<p>//创建java.sql.Date对象</p>
<p>java.sql.Date date3 = new java.sql.Date(35235325345L);</p>
<p>System.out.println(date3);//1971-02-13</p>
<p></p>
<p>//如何将java.util.Date对象转换为java.sql.Date对象</p>
<p>//情况一：</p>
<p>// Date date4 = new java.sql.Date(2343243242323L);</p>
<p>// java.sql.Date date5 = (java.sql.Date) date4;</p>
<p>//情况二：</p>
<p>Date date6 = new Date();</p>
<p>java.sql.Date date7 = new java.sql.Date(date6.getTime());</p>
<p></p>
<p></p>
<p>}</p>
<p></p>
<p>//1.System类中的currentTimeMillis()</p>
<p>@Test</p>
<p>public void test1(){</p>
<p>long time = System.currentTimeMillis();</p>
<p>//返回当前时间与1970年1月1日0时0分0秒之间以毫秒为单位的时间差。</p>
<p>//称为时间戳</p>
<p>System.out.println(time）；</p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
