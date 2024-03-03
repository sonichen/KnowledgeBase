---
title: Thread类的有关方法
updated: 2020-11-20T10:38:05.0000000+08:00
created: 2020-09-03T22:02:03.0000000+08:00
---

## 一、Thread中的常用方法
| void start()                          | 启动当前线程；调用当前线程的run()                                                                                              |
|---------------------------------------|--------------------------------------------------------------------------------------------------------------------------------|
| run():                                | 通常需要重写Thread类中的此方法，将创建的线程要执行的操作声明在此方法中                                                         |
| static Thread currentThread()         | 返回执行当前代码的线程                                                                                                         |
| String getName()                      | 获取当前线程的名字                                                                                                             |
| void setName()                        | 设置当前线程的名字                                                                                                             |
| **static void yield()**               | **释放当前cpu的执行权;比如在A线程中设置yield，当yield触发时，释放A的执行权，（可能：A的执行权被B抢走）\[A等待执行，让B先？\]** |
| **join()**                            | **在线程a中调用线程b的join(),此时线程a就进入阻塞状态，直到线程b完全执行完以后，线程a才结束阻塞状态。**                         |
| stop()                                | 已过时。当执行此方法时，强制结束当前线程。                                                                                     |
| **static void sleep(long millitime)** | **让当前线程“睡眠”指定的millitime毫秒。在指定的millitime毫秒时间内，当前 线程是阻塞状态。抛出InterruptedException异常**        |
| **boolean isAlive()**                 | **判断当前线程是否存活**                                                                                                       |

优先级
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>（1）线程的优先级：</p>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>MAX_PRIORITY：10</p>
<p>MIN _PRIORITY：1</p>
<p>NORM_PRIORITY：5 --&gt;默认优先级</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
<p>（2）如何获取和设置当前线程的优先级：</p>
<p>getPriority()获取线程的优先级</p>
<p>setPriority(int p):设置线程的优先级</p>
<p>3，</p>
<p>线程创建时继承父线程的优先级</p>
<p>低优先级只是获得调度的概率低，并非一定是在高优先级线程之后才被调用</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## 二、案例
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>yield():释放当前cpu的执行权;比如在A线程中设置yield，当yield触发时，释放A的执行权，</strong></p>
<p><strong>（可能：A的执行权被B抢走）[A等待执行，让B先？]</strong></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>public class ThreadMethodTest {</p>
<p>public static void main(String[] args) {</p>
<p></p>
<p>HelloThread ht =new HelloThread();</p>
<p>ht.start();</p>
<p>for(int i=0;i&lt;100;i++){</p>
<p>if(i%2==0){</p>
<p>System.out.println(Thread.currentThread().getName()+":"+i);</p>
<p>}</p>
<p>}</p>
<p>}</p>
<p>}</p>
<p>class HelloThread extends Thread{</p>
<p>@Override</p>
<p>public void run() {</p>
<p>for(int i=0;i&lt;100;i++){</p>
<p>if(i%2==0){</p>
<p>System.out.println(Thread.currentThread().getName()+":"+i);</p>
<p>}</p>
<p>if(i%20==0){</p>
<p>yield();</p>
<p>}</p>
<p>}</p>
<p>}</p>
<p>}</p></td>
</tr>
<tr class="even">
<td>![image1](../../../assets/a691bab89f6643fa8937afdf464c3f12.png)</td>
</tr>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th>join():在线程a中调用线程b的join(),此时线程a就进入阻塞状态，直到线程b完全执行完以后，线程a才结束阻塞状态。</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>public class ThreadMethodTest {</p>
<p>public static void main(String[] args) {</p>
<p></p>
<p>HelloThread ht =new HelloThread();</p>
<p>ht.start();</p>
<p>for(int i=0;i&lt;100;i++){</p>
<p>if(i%2==0){</p>
<p>System.out.println(Thread.currentThread().getName()+":"+i);</p>
<p>}</p>
<p>if(i%20==0){</p>
<p>try{</p>
<p>ht.join();</p>
<p>}catch (InterruptedException e){</p>
<p>e.printStackTrace();</p>
<p>}</p>
<p>}</p>
<p>}</p>
<p>}</p>
<p>}</p>
<p>class HelloThread extends Thread{</p>
<p>@Override</p>
<p>public void run() {</p>
<p>for(int i=0;i&lt;100;i++){</p>
<p>if(i%2==0){</p>
<p>System.out.println(Thread.currentThread().getName()+":"+i);</p>
<p>}</p>
<p></p>
<p>}</p>
<p>}</p>
<p>}</p></td>
</tr>
<tr class="even">
<td><p>main:0促发了条件，等另一个线程执行完，该线程才执行</p>
<p>Thread-0:0</p>
<p>Thread-0:2</p>
<p>Thread-0:4</p>
<p>Thread-0:6</p>
<p>Thread-0:100</p>
<p>main:1</p>
<p>…</p>
<p></p>
<p></p></td>
</tr>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>sleep(long millitime):让当前线程“睡眠”指定的millitime毫秒。在指定的millitime毫秒时间内，当前线程是阻塞状态。</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>public class ThreadMethodTest {</p>
<p>public static void main(String[] args) {</p>
<p></p>
<p>HelloThread ht =new HelloThread();</p>
<p>ht.start();</p>
<p>for(int i=0;i&lt;100;i++){</p>
<p>if(i%2==0) {</p>
<p>System.out.println(Thread.currentThread().getName() + ":" + i);</p>
<p>}</p>
<p>}</p>
<p>}</p>
<p>}</p>
<p>class HelloThread extends Thread{</p>
<p>@Override</p>
<p>public void run() {</p>
<p>for(int i=0;i&lt;100;i++){</p>
<p>if(i%2==0){</p>
<p>try {</p>
<p>sleep(1000);</p>
<p>}catch (InterruptedException e){</p>
<p>e.printStackTrace();</p>
<p>}</p>
<p>System.out.println(Thread.currentThread().getName()+":"+i);</p>
<p>}</p>
<p></p>
<p>}</p>
<p>}</p>
<p>}</p></td>
</tr>
</tbody>
</table>
