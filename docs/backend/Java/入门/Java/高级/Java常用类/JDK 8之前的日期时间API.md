---
title: JDK 8之前的日期时间API
updated: 2020-09-08T12:59:19.0000000+08:00
created: 2020-09-07T13:20:43.0000000+08:00
---

1\. java.lang.System类
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>/**</p>
<p>* 1. java.lang.System类</p>
<p>* System类提供的public static long currentTimeMillis()用来返回当前时间与1970年1月1日0时0分0秒之间以毫秒为单位的时间差。</p>
<p>* 此方法适于计算时间差。</p>
<p>*/</p>
<p>@Test</p>
<p>public void test1(){</p>
<p>Long time=System.currentTimeMillis();</p>
<p>System.out.println(time);//1599524637840</p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

2， java.util.Date类
![image1](../../../assets/cfac21e2ed3b4ba28187fb4c29c523a3.png)

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>/**</p>
<p>* java.util.Date类</p>
<p>* |---java.sql.Date类</p>
<p>*</p>
<p>* 1.两个构造器的使用</p>
<p>* &gt;构造器一：Date()：创建一个对应当前时间的Date对象</p>
<p>* &gt;构造器二：创建指定毫秒数的Date对象</p>
<p>* 2.两个方法的使用</p>
<p>* &gt;toString():显示当前的年、月、日、时、分、秒</p>
<p>* &gt;getTime():获取当前Date对象对应的毫秒数。（时间戳）</p>
<p>*</p>
<p>* 3. java.sql.Date对应着数据库中的日期类型的变量</p>
<p>* &gt;如何实例化</p>
<p>* &gt;如何将java.util.Date对象转换为java.sql.Date对象</p>
<p>*/</p>
<p>@Test</p>
<p>public void test2(){</p>
<p>//构造器一：Date()：创建一个对应当前时间的Date对象</p>
<p>Date date1=new Date();</p>
<p>System.out.println(date1.toString());</p>
<p>//Tue Sep 08 08:27:23 CST 2020</p>
<p>//构造器二：创建指定毫秒数的Date对象</p>
<p>Date date2=new Date(1599524637840L);</p>
<p>System.out.println(date2.toString());</p>
<p>//Tue Sep 08 08:23:57 CST 2020</p>
<p>//创建java.sql.Date对象</p>
<p>java.sql.Date date3=new java.sql.Date(34567891234L);</p>
<p>System.out.println(date3);//1971-02-05</p>
<p>//如何将java.util.Date对象转换为java.sql.Date对象</p>
<p>// 情况一</p>
<p>Date date4=new java.sql.Date(34567891234L);</p>
<p>java.sql.Date date5=(java.sql.Date)date4;</p>
<p>// 情况二</p>
<p>Date date6=new Date();</p>
<p>java.sql.Date date7=new java.sql.Date(date6.getTime());</p>
<p>}</p>
<p></p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

3， java.text.SimpleDateFormat类

![image2](../../../assets/69deeafa75b24094a71334332a8941f4.png)
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>/**</p>
<p>* SimpleDateFormat的使用：SimpleDateFormat对日期Date类的格式化和解析</p>
<p>*</p>
<p>* 1.两个操作：</p>
<p>* 1.1 格式化：日期 ---&gt;字符串</p>
<p>* 1.2 解析：格式化的逆过程，字符串 ---&gt; 日期</p>
<p>*</p>
<p>* 2.SimpleDateFormat的实例化</p>
<p>*/</p>
<p>@Test</p>
<p>public void test3() throws ParseException {</p>
<p>// 实例化</p>
<p>SimpleDateFormat sdf=new SimpleDateFormat();</p>
<p>// 格式化：日期--》字符串</p>
<p>Date date=new Date();</p>
<p>System.out.println(date);</p>
<p>//Tue Sep 08 08:42:52 CST 2020</p>
<p></p>
<p>String format=sdf.format(date);</p>
<p>System.out.println(date);</p>
<p>//Tue Sep 08 08:42:52 CST 2020</p>
<p></p>
<p>// 解析：格式化的逆过程，字符串--》日期</p>
<p>String str="20-09-08 上午08:45";</p>
<p>Date date1=sdf.parse(str);</p>
<p>System.out.println(date1);</p>
<p>//Tue Sep 08 08:45:00 CST 2020</p>
<p>// SimpleDateFormat sdf1=new SimpleDateFormat("yyyy.MMMMM.dd.GGG hh:mm aaa");GG是公元</p>
<p>SimpleDateFormat sdf1=new SimpleDateFormat("yyyy-MM-dd hh:mm:ss");</p>
<p>//格式化</p>
<p>String format1=sdf1.format(date);</p>
<p>System.out.println(format1);// 2020-09-08 09:00:09</p>
<p>//解析：要求字符串必须是符合SimpleDateFormat识别的格式（通过构造器参数体现）</p>
<p>//否则，抛出异常</p>
<p>Date date2=sdf1.parse("2020-09-08 09:00:09");</p>
<p>System.out.println(date2);//Tue Sep 08 09:00:09 CST 2020</p>
<p></p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

![image3](../../../assets/ec26eb9baaeb493ab8337f5d7730b968.png)
4， java.util.Calendar(日历)类
![image4](../../../assets/42aa093a0a9b46e682d99902f63c477d.png)
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>@Test</p>
<p>public void test4(){</p>
<p>// 1.实例化</p>
<p>// 方式一：创建其子类（GregorianCalendar）的对象</p>
<p>// 方式二：调用其静态方法</p>
<p>Calendar calendar=Calendar.getInstance();</p>
<p>System.out.println(calendar.getClass());</p>
<p>// class java.util.GregorianCalendar</p>
<p></p>
<p>// 常用方法</p>
<p>// get()</p>
<p>int days=calendar.get(Calendar.DAY_OF_MONTH);</p>
<p>System.out.println(days);//8</p>
<p>System.out.println(calendar.get(Calendar.DAY_OF_YEAR));//252</p>
<p></p>
<p>// set()--&gt;calendar的可变性</p>
<p>calendar.set(Calendar.DAY_OF_YEAR,22);</p>
<p>System.out.println(calendar.get(Calendar.DAY_OF_YEAR));//22</p>
<p>// add()</p>
<p>calendar.add(Calendar.DAY_OF_MONTH,-3);</p>
<p>System.out.println(calendar.get(Calendar.DAY_OF_MONTH));//19</p>
<p></p>
<p>// getTime()日历类---&gt;Date</p>
<p>Date date=calendar.getTime();</p>
<p>System.out.println(date);//Sun Jan 19 12:51:42 CST 2020</p>
<p>// setTime():Date--&gt;日历类</p>
<p>Date date1=new Date();</p>
<p>calendar.setTime(date1);</p>
<p>System.out.println(calendar.get(Calendar.DAY_OF_MONTH));//8</p>
<p>}</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
