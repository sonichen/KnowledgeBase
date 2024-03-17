---
title: UDP网络编程
updated: 2020-09-22T09:13:40.0000000+08:00
created: 2020-09-18T19:23:14.0000000+08:00
---

一、UDP网络通信
1，类 DatagramSocket 和 DatagramPacket 实现了基于 UDP 协议网络程序,
2，UDP数据报通过数据报套接字 DatagramSocket 发送和接收，系统不保证 UDP数据报一定能够安全送到目的地，也不能确定什么时候可以抵达。
3，DatagramPacket 对象封装了UDP数据报，在数据报中包含了发送端的IP 地址和端口号以及接收端的IP地址和端口号。
4，UDP协议中每个数据报都给出了完整的地址信息，因此无须建立发送方和 接收方的连接。如同发快递包裹一样。
二、方法
public DatagramSocket(int port)创建数据报套接字并将其绑定到本地主机上的指定端口。套接字将被 绑定到通配符地址，IP 地址由内核来选择。 l public DatagramSocket(int port,InetAddress laddr)创建数据报套接字，将其绑定到指定的本地地址。 本地端口必须在 0 到 65535 之间（包括两者）。如果 IP 地址为 0.0.0.0，套接字将被绑定到通配符地 址，IP 地址由内核选择。 l public void close()关闭此数据报套接字。 l public void send(DatagramPacket p)从此套接字发送数据报包。DatagramPacket 包含的信息指示：将 要发送的数据、其长度、远程主机的IP 地址和远程主机的端口号。 l public void receive(DatagramPacket p)从此套接字接收数据报包。当此方法返回时，DatagramPacket 的缓冲区填充了接收的数据。数据报包也包含发送方的 IP 地址和发送方机器上的端口号。 此方法 在接收到数据报前一直阻塞。数据报包对象的 length 字段包含所接收信息的长度。如果信息比包的 长度长，该信息将被截短。 l public InetAddress getLocalAddress()获取套接字绑定的本地地址。 l public int getLocalPort()返回此套接字绑定的本地主机上的端口号。 l public InetAddress getInetAddress()返回此套接字连接的地址。如果套接字未连接，则返回null。 l public int getPort()返回此套接字的端口。如果套接字未连接，则返回-1。

l public DatagramPacket(byte\[\] buf,int length)构造 DatagramPacket，用来接收长 度为 length 的数据包。 length 参数必须小于等于 buf.length。 l public DatagramPacket(byte\[\] buf,int length,InetAddress address,int port)构造数 据报包，用来将长度为 length 的包发送到指定主机上的指定端口号。length 参数必须小于等于 buf.length。 l public InetAddress getAddress()返回某台机器的 IP 地址，此数据报将要发往该 机器或者是从该机器接收到的。 l public int getPort()返回某台远程主机的端口号，此数据报将要发往该主机或 者是从该主机接收到的。 l public byte\[\] getData()返回数据缓冲区。接收到的或将要发送的数据从缓冲区 中的偏移量 offset 处开始，持续 length 长度。 l public int getLength()返回将要发送或接收到的数据的长度。

![image1](../../../assets/264a6ea4e0ef4a7880ce0ec28044f1c4.png)
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>package java02;</p>
<p></p>
<p>import org.junit.Test;</p>
<p></p>
<p>import java.io.IOException;</p>
<p>import java.net.*;</p>
<p></p>
<p>/*</p>
<p>UDPd协议的网络编程</p>
<p>*/</p>
<p>public class UCPTest {</p>
<p>@Test</p>
<p>public void sender() throws IOException {</p>
<p>// 1.DatagramSocket</p>
<p>DatagramSocket socket=new DatagramSocket();</p>
<p></p>
<p>String str="我是UDP发送的信息";</p>
<p>byte []data=str.getBytes();</p>
<p></p>
<p>InetAddress inet=InetAddress.getLocalHost();</p>
<p>// 3.建立数据包</p>
<p>DatagramPacket packet=new DatagramPacket(data,0,data.length,inet,9090);</p>
<p>// 4.调用Socket的发送方法</p>
<p>socket.send(packet);</p>
<p>// 5.关闭</p>
<p>socket.close();</p>
<p>}</p>
<p>@Test</p>
<p>public void receiver() throws IOException {</p>
<p>DatagramSocket socket=new DatagramSocket(9090);</p>
<p></p>
<p>byte [] buffer=new byte[1024];</p>
<p>DatagramPacket packet=new DatagramPacket(buffer,0,buffer.length);</p>
<p></p>
<p>socket.receive(packet);</p>
<p></p>
<p>System.out.println(new String(packet.getData(),0,packet.getLength()));</p>
<p></p>
<p>socket.close();</p>
<p>}</p>
<p></p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
