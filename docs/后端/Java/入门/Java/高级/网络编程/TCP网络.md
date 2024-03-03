---
title: TCP网络
updated: 2020-09-22T09:31:55.0000000+08:00
created: 2020-09-18T19:23:08.0000000+08:00
---

一，基于Socket的TCP编程

Java语言的基于套接字编程分为服务端编程和客户端编程
Ø 传输完毕，需释放已建立的连接，效率低
![image1](../../../assets/475c0d9b0199422797c9b9bb57b69866.png)

![image2](../../../assets/4f62f79536dd439c99592f101863f698.png)

## 二，基于Socket的TCP编程
1， **客户端**Socket的工作过程包含以下四个基本的步骤：
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>1，<strong>创建 Socket</strong>：根据指定服务端的 IP 地址或端口号构造 Socket 类对象。若服务器端响应，则建立客户端到服务器的通信线路。若连接失败，会出现异常。</p>
<p>客户端程序可以使用Socket类创建对象，创建的同时会自动向服务器方发起连接。</p>
<p>Socket的构造器是：</p>
<table>
<colgroup>
<col style="width: 55%" />
<col style="width: 44%" />
</colgroup>
<thead>
<tr class="header">
<th>Socket(String host,int port)throws UnknownHostException,IOException：</th>
<th>向服务器(域名是 host。端口号为port)发起TCP连接，若成功，则创建Socket对象，否则抛出异常。</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Socket(InetAddress address,int port)throws IOException：</td>
<td>根据InetAddress对象所表示的 IP地址以及端口号port发起连接。</td>
</tr>
</tbody>
</table>
<p></p>
<p>2，<strong>打开连接到 Socket 的输入/出流</strong>： 使用 getInputStream()方法获得输入流，使用 getOutputStream()方法获得输出流，进行数据传输</p>
<p>3，<strong>按照一定的协议对 Socket 进行读/写操作</strong>：通过输入流读取服务器放入线路的信息</p>
<p>（但不能读取自己放入线路的信息），通过输出流将信息写入线程。,</p>
<p>4，<strong>关闭 Socket</strong>：断开客户端到服务器的连接，释放线路</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

2，**服务器**程序的工作过程包含以下四个基本的步骤
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>服务器必须事先建立一个等待客户请求建立套接字 连接的ServerSocket对象。</strong></p>
<p>1，<strong>调用 ServerSocket(int port)</strong> ：创建一个服务器端套接字，并绑定到指定端口 上。用于监听客户端的请求。</p>
<p>2，<strong>调用 accept()</strong>：监听连接请求，如果客户端请求连接，则接受连接，返回通信 套接字对象。</p>
<p>3，<strong>调用 该Socket类对象的 getOutputStream() 和 getInputStream ()：获取输出 流和输入流，开始网络数据的发送和接收</strong>。</p>
<p>4，<strong>关闭ServerSocket和Socket对象</strong>：客户端访问结束，关闭通信套接字。,</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

二/
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>package java02;</strong></p>
<p></p>
<p><strong>import org.junit.Test;</strong></p>
<p></p>
<p><strong>import java.io.ByteArrayOutputStream;</strong></p>
<p><strong>import java.io.IOException;</strong></p>
<p><strong>import java.io.InputStream;</strong></p>
<p><strong>import java.io.OutputStream;</strong></p>
<p><strong>import java.net.InetAddress;</strong></p>
<p><strong>import java.net.ServerSocket;</strong></p>
<p><strong>import java.net.Socket;</strong></p>
<p></p>
<p><strong>/**</strong></p>
<p><strong>* * 实现TCP的网络编程</strong></p>
<p><strong>* * 例子1：客户端发送信息给服务端，服务端将数据显示在控制台上</strong></p>
<p><strong>*/</strong></p>
<p><strong>//服務器</strong></p>
<p><strong>public class TCPTest1 {</strong></p>
<p><strong>@Test</strong></p>
<p><strong>public void server() throws IOException {</strong></p>
<p><strong>ServerSocket ss= null;</strong></p>
<p><strong>Socket socket = null;</strong></p>
<p><strong>InputStream inputStream = null;</strong></p>
<p><strong>ByteArrayOutputStream baos= null;</strong></p>
<p><strong>try {</strong></p>
<p><strong>//1.创建服务器端的ServerSocket，指明自己的端口号</strong></p>
<p><strong>ss = new ServerSocket(9090);</strong></p>
<p><strong>//2.调用accept()表示接收来自于客户端的socket</strong></p>
<p><strong>socket = ss.accept();</strong></p>
<p><strong>//3.获取输入流</strong></p>
<p><strong>inputStream = socket.getInputStream();</strong></p>
<p><strong>//4.读取输入流中的数据</strong></p>
<p><strong>baos = new ByteArrayOutputStream();//防止乱码</strong></p>
<p><strong>byte[]buffer=new byte[5];</strong></p>
<p><strong>int len=0;</strong></p>
<p><strong></strong></p>
<p><strong>while((len=inputStream.read(buffer))!=-1){</strong></p>
<p><strong>baos.write(buffer,0,len);</strong></p>
<p><strong>}</strong></p>
<p><strong>//顯示data到console上</strong></p>
<p><strong>System.out.println(baos.toString());</strong></p>
<p><strong>System.out.println("receive"+socket.getInetAddress().getHostAddress()+" \'s message");</strong></p>
<p><strong>} catch (IOException e) {</strong></p>
<p><strong>e.printStackTrace();</strong></p>
<p><strong>} finally {</strong></p>
<p><strong>//5.关闭资源</strong></p>
<p><strong>if(ss!=null){</strong></p>
<p><strong>try {</strong></p>
<p><strong>ss.close();</strong></p>
<p><strong>} catch (IOException e) {</strong></p>
<p><strong>e.printStackTrace();</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p>
<p><strong>if(socket!=null){</strong></p>
<p><strong>try {</strong></p>
<p><strong>socket.close();</strong></p>
<p><strong>} catch (IOException e) {</strong></p>
<p><strong>e.printStackTrace();</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p>
<p><strong>if(inputStream!=null){</strong></p>
<p><strong>try {</strong></p>
<p><strong>inputStream.close();</strong></p>
<p><strong>} catch (IOException e) {</strong></p>
<p><strong>e.printStackTrace();</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p>
<p><strong>if(baos!=null){</strong></p>
<p><strong>try {</strong></p>
<p><strong>baos.close();</strong></p>
<p><strong>} catch (IOException e) {</strong></p>
<p><strong>e.printStackTrace();</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p>
<p></p>
<p></p>
<p><strong>}</strong></p>
<p><strong>//客戶端</strong></p>
<p><strong>@Test</strong></p>
<p><strong>public void client() throws IOException {</strong></p>
<p><strong>Socket socket= null;</strong></p>
<p><strong>OutputStream os= null;</strong></p>
<p><strong>try {</strong></p>
<p><strong>//1.创建Socket对象，指明服务器端的ip和端口号</strong></p>
<p><strong>InetAddress inet=InetAddress.getByName("192.168.56.1");</strong></p>
<p><strong>socket = new Socket(inet,9090);</strong></p>
<p><strong>//2.获取一个输出流，用于输出数据</strong></p>
<p><strong>os = socket.getOutputStream();</strong></p>
<p><strong>//3.写出数据的操作</strong></p>
<p><strong>os.write("你好，我是客戶端".getBytes());</strong></p>
<p><strong>} catch (IOException e) {</strong></p>
<p><strong>e.printStackTrace();</strong></p>
<p><strong>} finally {</strong></p>
<p><strong>//4.资源的关闭</strong></p>
<p><strong>if (os!=null) {</strong></p>
<p><strong>try {</strong></p>
<p><strong>os.close();</strong></p>
<p><strong>} catch (IOException e) {</strong></p>
<p><strong>e.printStackTrace();</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p>
<p><strong>if (socket!=null) {</strong></p>
<p><strong>try {</strong></p>
<p><strong>socket.close();</strong></p>
<p><strong>} catch (IOException e) {</strong></p>
<p><strong>e.printStackTrace();</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p>
<p><strong></strong></p>
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

