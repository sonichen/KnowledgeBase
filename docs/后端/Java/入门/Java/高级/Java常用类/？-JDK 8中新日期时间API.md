---
title: ？-JDK 8中新日期时间API
updated: 2020-09-08T13:06:11.0000000+08:00
created: 2020-09-07T13:20:57.0000000+08:00
---

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>package com.atguigu.java;</p>
<p></p>
<p>import org.junit.Test;</p>
<p></p>
<p>import java.time.*;</p>
<p>import java.time.format.DateTimeFormatter;</p>
<p>import java.time.format.FormatStyle;</p>
<p>import java.time.temporal.TemporalAccessor;</p>
<p>import java.util.Date;</p>
<p></p>
<p>/**</p>
<p>* jdk 8中日期时间API的测试</p>
<p>*</p>
<p>* @author shkstart</p>
<p>* @create 2019 下午 2:44</p>
<p>*/</p>
<p>public class JDK8DateTimeTest {</p>
<p></p>
<p>@Test</p>
<p>public void testDate(){</p>
<p>//偏移量</p>
<p>Date date1 = new Date(2020 - 1900,9 - 1,8);</p>
<p>System.out.println(date1);//Tue Sep 08 00:00:00 GMT+08:00 2020</p>
<p>}</p>
<p></p>
<p>/*</p>
<p>LocalDate、LocalTime、LocalDateTime 的使用</p>
<p>说明：</p>
<p>1.LocalDateTime相较于LocalDate、LocalTime，使用频率要高</p>
<p>2.类似于Calendar</p>
<p>*/</p>
<p>@Test</p>
<p>public void test1(){</p>
<p>//now():获取当前的日期、时间、日期+时间</p>
<p>LocalDate localDate = LocalDate.now();</p>
<p>LocalTime localTime = LocalTime.now();</p>
<p>LocalDateTime localDateTime = LocalDateTime.now();</p>
<p></p>
<p>System.out.println(localDate);</p>
<p>System.out.println(localTime);</p>
<p>System.out.println(localDateTime);</p>
<p></p>
<p>//of():设置指定的年、月、日、时、分、秒。没有偏移量</p>
<p>LocalDateTime localDateTime1 = LocalDateTime.of(2020, 10, 6, 13, 23, 43);</p>
<p>System.out.println(localDateTime1);</p>
<p></p>
<p></p>
<p>//getXxx()：获取相关的属性</p>
<p>System.out.println(localDateTime.getDayOfMonth());</p>
<p>System.out.println(localDateTime.getDayOfWeek());</p>
<p>System.out.println(localDateTime.getMonth());</p>
<p>System.out.println(localDateTime.getMonthValue());</p>
<p>System.out.println(localDateTime.getMinute());</p>
<p></p>
<p>//体现不可变性</p>
<p>//withXxx():设置相关的属性</p>
<p>LocalDate localDate1 = localDate.withDayOfMonth(22);</p>
<p>System.out.println(localDate);</p>
<p>System.out.println(localDate1);</p>
<p></p>
<p></p>
<p>LocalDateTime localDateTime2 = localDateTime.withHour(4);</p>
<p>System.out.println(localDateTime);</p>
<p>System.out.println(localDateTime2);</p>
<p></p>
<p>//不可变性</p>
<p>LocalDateTime localDateTime3 = localDateTime.plusMonths(3);</p>
<p>System.out.println(localDateTime);</p>
<p>System.out.println(localDateTime3);</p>
<p></p>
<p>LocalDateTime localDateTime4 = localDateTime.minusDays(6);</p>
<p>System.out.println(localDateTime);</p>
<p>System.out.println(localDateTime4);</p>
<p>}</p>
<p></p>
<p>/*</p>
<p>Instant的使用</p>
<p>类似于 java.util.Date类</p>
<p></p>
<p>*/</p>
<p>@Test</p>
<p>public void test2(){</p>
<p>//now():获取本初子午线对应的标准时间</p>
<p>Instant instant = Instant.now();</p>
<p>System.out.println(instant);//2019-02-18T07:29:41.719Z</p>
<p></p>
<p>//添加时间的偏移量</p>
<p>OffsetDateTime offsetDateTime = instant.atOffset(ZoneOffset.ofHours(8));</p>
<p>System.out.println(offsetDateTime);//2019-02-18T15:32:50.611+08:00</p>
<p></p>
<p>//toEpochMilli():获取自1970年1月1日0时0分0秒（UTC）开始的毫秒数 ---&gt; Date类的getTime()</p>
<p>long milli = instant.toEpochMilli();</p>
<p>System.out.println(milli);</p>
<p></p>
<p>//ofEpochMilli():通过给定的毫秒数，获取Instant实例 --&gt;Date(long millis)</p>
<p>Instant instant1 = Instant.ofEpochMilli(1550475314878L);</p>
<p>System.out.println(instant1);</p>
<p>}</p>
<p></p>
<p>/*</p>
<p>DateTimeFormatter:格式化或解析日期、时间</p>
<p>类似于SimpleDateFormat</p>
<p></p>
<p>*/</p>
<p></p>
<p>@Test</p>
<p>public void test3(){</p>
<p>// 方式一：预定义的标准格式。如：ISO_LOCAL_DATE_TIME;ISO_LOCAL_DATE;ISO_LOCAL_TIME</p>
<p>DateTimeFormatter formatter = DateTimeFormatter.ISO_LOCAL_DATE_TIME;</p>
<p>//格式化:日期--&gt;字符串</p>
<p>LocalDateTime localDateTime = LocalDateTime.now();</p>
<p>String str1 = formatter.format(localDateTime);</p>
<p>System.out.println(localDateTime);</p>
<p>System.out.println(str1);//2019-02-18T15:42:18.797</p>
<p></p>
<p>//解析：字符串 --&gt;日期</p>
<p>TemporalAccessor parse = formatter.parse("2019-02-18T15:42:18.797");</p>
<p>System.out.println(parse);</p>
<p></p>
<p>// 方式二：</p>
<p>// 本地化相关的格式。如：ofLocalizedDateTime()</p>
<p>// FormatStyle.LONG / FormatStyle.MEDIUM / FormatStyle.SHORT :适用于LocalDateTime</p>
<p>DateTimeFormatter formatter1 = DateTimeFormatter.ofLocalizedDateTime(FormatStyle.LONG);</p>
<p>//格式化</p>
<p>String str2 = formatter1.format(localDateTime);</p>
<p>System.out.println(str2);//2019年2月18日 下午03时47分16秒</p>
<p></p>
<p></p>
<p>// 本地化相关的格式。如：ofLocalizedDate()</p>
<p>// FormatStyle.FULL / FormatStyle.LONG / FormatStyle.MEDIUM / FormatStyle.SHORT : 适用于LocalDate</p>
<p>DateTimeFormatter formatter2 = DateTimeFormatter.ofLocalizedDate(FormatStyle.MEDIUM);</p>
<p>//格式化</p>
<p>String str3 = formatter2.format(LocalDate.now());</p>
<p>System.out.println(str3);//2019-2-18</p>
<p></p>
<p></p>
<p>// 重点： 方式三：自定义的格式。如：ofPattern(“yyyy-MM-dd hh:mm:ss”)</p>
<p>DateTimeFormatter formatter3 = DateTimeFormatter.ofPattern("yyyy-MM-dd hh:mm:ss");</p>
<p>//格式化</p>
<p>String str4 = formatter3.format(LocalDateTime.now());</p>
<p>System.out.println(str4);//2019-02-18 03:52:09</p>
<p></p>
<p>//解析</p>
<p>TemporalAccessor accessor = formatter3.parse("2019-02-18 03:52:09");</p>
<p>System.out.println(accessor);</p>
<p></p>
<p>}</p>
<p></p>
<p>}</p>
<p></p>
<p>111</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
