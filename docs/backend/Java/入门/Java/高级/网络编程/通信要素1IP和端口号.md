---
title: 通信要素1：IP和端口号
updated: 2020-09-22T09:18:05.0000000+08:00
created: 2020-09-18T15:29:00.0000000+08:00
---

##  一、网络编程中有两个主要的问题
\* 1.如何准确地定位网络上一台或多台主机；定位主机上的特定的应用
\* 2.找到主机后如何可靠高效地进行数据传输
\*
## 二、网络编程中的两个要素
\* 1.对应问题一：IP和端口号
\* 2.对应问题二：提供网络通信协议：TCP/IP参考模型（应用层、传输层、网络层、物理+数据链路层）
\*
\*
## 三、通信要素一：IP和端口号
1\. **IP:唯一的标识 Internet 上的计算机（通信实体）**
2\. 在**Java中使用InetAddress类代表IP**
3\. IP分类：**IPv4** 和 IPv6 ; 万维网 和 局域网
4\. 域名: [www.baidu.com](http://www.baidu.com)
域名--》DNS解析成IP地址--》找到网络服务器
5\. 本地回路地址：127.0.0.1 对应着：localhost
6\. 如何实例化InetAddress:两个方法：
| getByName(String host)                  | 获取IP地址和域名       |
|-----------------------------------------|------------------------|
| getLocalHost()                          | 获取本地IP             |
| **getHostName()**                       | **获取域名**           |
| **getHostAddress()**                    | **获取IP地址**         |
| public boolean isReachable(int timeout) | 测试是否可以达到该地址 |
![image1](../../../assets/4d94555fe7a140caae3ceca5d8f7bc94.png)

7\. 端口号：正在计算机上运行的进程。
要求：不同的进程有不同的端口号
**范围：被规定为一个 16 位的整数 0~65535**。
**8. 端口号与IP地址的组合得出一个网络套接字：Socket**

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>package java02;</strong></p>
<p></p>
<p><strong>import java.net.InetAddress;</strong></p>
<p><strong>import java.net.UnknownHostException;</strong></p>
<p></p>
<p><strong>public class InetAddressTest {</strong></p>
<p><strong>public static void main(String[] args) {</strong></p>
<p><strong>try {</strong></p>
<p><strong>//File file = new File("hello.txt");</strong></p>
<p><strong><mark>InetAddress inet1 = InetAddress.getByName("192.168.10.14");</mark></strong></p>
<p><strong>//输出域名和IP地址</strong></p>
<p><strong>System.out.println(inet1);///192.168.10.14</strong></p>
<p><strong></strong></p>
<p><strong>InetAddress inet2 = InetAddress.getByName("sonicottage.com");</strong></p>
<p><strong>System.out.println(inet2);//sonicottage.com/139.162.126.124</strong></p>
<p></p>
<p><strong>InetAddress inet3 = InetAddress.getByName("127.0.0.1");</strong></p>
<p><strong>System.out.println(inet3);///127.0.0.1</strong></p>
<p></p>
<p><strong>//获取本地ip</strong></p>
<p><strong>InetAddress inet4 = InetAddress.getLocalHost();</strong></p>
<p><strong>System.out.println(inet4);//LAPTOP-BIR7PVN9/192.168.56.1</strong></p>
<p></p>
<p><strong>//getHostName()获取域名</strong></p>
<p><strong>System.out.println(inet2.getHostName());//sonicottage.com</strong></p>
<p><strong>//getHostAddress()获取IP地址</strong></p>
<p><strong>System.out.println(inet2.getHostAddress());//139.162.126.124</strong></p>
<p></p>
<p><strong>} catch (UnknownHostException e) {</strong></p>
<p><strong>e.printStackTrace();</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
