---
title: Properties性质
updated: 2020-09-15T10:34:47.0000000+08:00
created: 2020-09-13T19:30:34.0000000+08:00
---

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>package java01;</strong></p>
<p></p>
<p><strong>import com.sun.org.glassfish.external.amx.AMXGlassfish;</strong></p>
<p></p>
<p><strong>import java.io.FileInputStream;</strong></p>
<p><strong>import java.io.IOException;</strong></p>
<p><strong>import java.util.Properties;</strong></p>
<p></p>
<p><strong>public class PropertiesTest {</strong></p>
<p><strong>//Properties:常用来处理配置文件。key和value都是String类型</strong></p>
<p><strong>FileInputStream fis=null;</strong></p>
<p><strong>public static void main(String[] args) {</strong></p>
<p><strong>try{</strong></p>
<p><strong><mark>Properties properties=new Properties();</mark></strong></p>
<p><strong>properties=new FileInputStream("jdbc.<mark>properties</mark>");</strong></p>
<p><strong><mark>properties.load(fis);//加载文件</mark></strong></p>
<p></p>
<p><strong>String name=properties.getProperty("name");</strong></p>
<p><strong>String password=properties.getProperty("password");</strong></p>
<p></p>
<p><strong>System.out.println("name="+name+" ,password="+password);</strong></p>
<p><strong>}catch (Exception e){</strong></p>
<p><strong>e.printStackTrace();</strong></p>
<p><strong>}finally {</strong></p>
<p><strong>if(fis!=null){</strong></p>
<p><strong>try{</strong></p>
<p><strong>fis.close();</strong></p>
<p><strong>}catch (IOException e){</strong></p>
<p><strong>e.printStackTrace();</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
