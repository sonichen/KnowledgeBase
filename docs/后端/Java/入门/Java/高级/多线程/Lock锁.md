---
title: Lock锁
updated: 2020-11-20T10:58:37.0000000+08:00
created: 2020-09-04T10:49:40.0000000+08:00
---

## 一、Lock
解决线程安全问题的方式三：Lock锁 --- JDK5.0新增
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>class A{</p>
<p><mark>private final ReentrantLock lock = new ReenTrantLock();</mark></p>
<blockquote>
<p>public void m(){</p>
<p><mark>lock.lock();</mark></p>
<p>try{</p>
<p>//保证线程安全的代码;</p>
<p>} finally{</p>
<p><mark>lock.unlock();</mark></p>
<p>}</p>
<p>}</p>
</blockquote>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

1\. 面试题：synchronized 与 Lock的异同？
相同：二者都可以解决线程安全问题
不同：**synchronized机制在执行完相应的同步代码以后，自动的释放同步监视器**
Lock需要手动的启动同步（lock()），同时结束同步也需要**手动的实现**（unlock()）
2.优先使用顺序：
| **Lock à 同步代码块（已经进入了方法体，分配了相应资源） à 同步方法（在方法体之外）** |
|--------------------------------------------------------------------------------------|
面试题：如何解决线程安全问题？有几种方式--3种

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>package day02.java1;</p>
<p></p>
<p>import java.util.concurrent.locks.ReentrantLock;</p>
<p></p>
<p>public class ThreadTest {</p>
<p>public static void main(String[] args) {</p>
<p>Window w=new Window();</p>
<p>Thread t1=new Thread(w);</p>
<p>Thread t2=new Thread(w);</p>
<p>Thread t3=new Thread(w);</p>
<p>t1.setName("窗口1");</p>
<p>t2.setName("窗口2");</p>
<p>t3.setName("窗口3");</p>
<p>t1.start();</p>
<p>t2.start();</p>
<p>t3.start();</p>
<p></p>
<p>}</p>
<p>}</p>
<p>class Window implements Runnable{</p>
<p>private int ticket=100;</p>
<p><mark>private ReentrantLock lock=new ReentrantLock();</mark></p>
<p>@Override</p>
<p>public void run() {</p>
<p>while(true){</p>
<p>try{</p>
<p>lock.lock();</p>
<p>if(ticket&gt;0){</p>
<p>System.out.println(Thread.currentThread().getName()+"售票，排号"+ticket);</p>
<p>ticket--;</p>
<p>}else{</p>
<p>break;</p>
<p>}</p>
<p>}finally {</p>
<p>lock.unlock();</p>
<p>}</p>
<p>}</p>
<p>}</p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
