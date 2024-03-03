---
title: URL网络编程
updated: 2020-09-22T09:14:14.0000000+08:00
created: 2020-09-18T19:23:19.0000000+08:00
---

URL网络编程
1.URL:统一资源定位符，对应着互联网的某一资源地址
2.格式：
<http://localhost:8080/examples/beauty.jpg?username=Tom>
协议 主机名 端口号 资源地址 参数列表

3，
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>package java02;</strong></p>
<p></p>
<p><strong>import java.net.MalformedURLException;</strong></p>
<p><strong>import java.net.URL;</strong></p>
<p></p>
<p><strong>public class URLTest1 {</strong></p>
<p><strong>public static void main(String[] args) {</strong></p>
<p><strong>try {</strong></p>
<p></p>
<p><strong>URL url = new URL("http://sonicottage.com/");</strong></p>
<p></p>
<p><strong>// public String getProtocol( ) 获取该URL的协议名</strong></p>
<p><strong>System.out.println(url.getProtocol());</strong></p>
<p><strong>// public String getHost( ) 获取该URL的主机名</strong></p>
<p><strong>System.out.println(url.getHost());</strong></p>
<p><strong>// public String getPort( ) 获取该URL的端口号</strong></p>
<p><strong>System.out.println(url.getPort());</strong></p>
<p><strong>// public String getPath( ) 获取该URL的文件路径</strong></p>
<p><strong>System.out.println(url.getPath());</strong></p>
<p><strong>// public String getFile( ) 获取该URL的文件名</strong></p>
<p><strong>System.out.println(url.getFile());</strong></p>
<p><strong>// public String getQuery( ) 获取该URL的查询名</strong></p>
<p><strong>System.out.println(url.getQuery());</strong></p>
<p></p>
<p><strong>} catch (MalformedURLException e) {</strong></p>
<p><strong>e.printStackTrace();</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p></th>
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
<th><p><strong>package com.atguigu.java1;</strong></p>
<p></p>
<p><strong>import java.io.FileOutputStream;</strong></p>
<p><strong>import java.io.IOException;</strong></p>
<p><strong>import java.io.InputStream;</strong></p>
<p><strong>import java.net.HttpURLConnection;</strong></p>
<p><strong>import java.net.URL;</strong></p>
<p></p>
<p><strong>/**</strong></p>
<p><strong>* @author shkstart</strong></p>
<p><strong>* @create 2019 下午 4:54</strong></p>
<p><strong>*/</strong></p>
<p><strong>public class URLTest1 {</strong></p>
<p></p>
<p><strong>public static void main(String[] args) {</strong></p>
<p></p>
<p><strong>HttpURLConnection urlConnection = null;</strong></p>
<p><strong>InputStream is = null;</strong></p>
<p><strong>FileOutputStream fos = null;</strong></p>
<p><strong>try {</strong></p>
<p><strong>URL url = new URL("http://localhost:8080/examples/beauty.jpg");</strong></p>
<p></p>
<p><strong>urlConnection = (HttpURLConnection) url.openConnection();</strong></p>
<p></p>
<p><strong>urlConnection.connect();</strong></p>
<p></p>
<p><strong>is = urlConnection.getInputStream();</strong></p>
<p><strong>fos = new FileOutputStream("day10\\beauty3.jpg");</strong></p>
<p></p>
<p><strong>byte[] buffer = new byte[1024];</strong></p>
<p><strong>int len;</strong></p>
<p><strong>while((len = is.read(buffer)) != -1){</strong></p>
<p><strong>fos.write(buffer,0,len);</strong></p>
<p><strong>}</strong></p>
<p></p>
<p><strong>System.out.println("下载完成");</strong></p>
<p><strong>} catch (IOException e) {</strong></p>
<p><strong>e.printStackTrace();</strong></p>
<p><strong>} finally {</strong></p>
<p><strong>//关闭资源</strong></p>
<p><strong>if(is != null){</strong></p>
<p><strong>try {</strong></p>
<p><strong>is.close();</strong></p>
<p><strong>} catch (IOException e) {</strong></p>
<p><strong>e.printStackTrace();</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p>
<p><strong>if(fos != null){</strong></p>
<p><strong>try {</strong></p>
<p><strong>fos.close();</strong></p>
<p><strong>} catch (IOException e) {</strong></p>
<p><strong>e.printStackTrace();</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p>
<p><strong>if(urlConnection != null){</strong></p>
<p><strong>urlConnection.disconnect();</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p>
<p></p>
<p></p>
<p></p>
<p></p>
<p></p>
<p></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
