---
title: RandomAccessFile
updated: 2020-09-18T15:18:20.0000000+08:00
created: 2020-09-18T13:58:11.0000000+08:00
---

/\*\*
\* RandomAccessFile的使用
\* 1.RandomAccessFile直接继承于java.lang.Object类，实现了DataInput和DataOutput接口
\* 2.RandomAccessFile既可以作为一个输入流，又可以作为一个输出流
\*
\* 3.如果RandomAccessFile作为输出流时，写出到的文件如果不存在，则在执行过程中自动创建。
\* 如果写出到的文件存在，则会对原有文件内容进行覆盖。（默认情况下，从头覆盖）
\*
\* 4. 可以通过相关的操作，实现RandomAccessFile“插入”数据的效果

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>package java01;</p>
<p></p>
<p>import org.junit.Test;</p>
<p></p>
<p>import java.io.File;</p>
<p>import java.io.FileNotFoundException;</p>
<p>import java.io.IOException;</p>
<p>import java.io.RandomAccessFile;</p>
<p></p>
<p>public class RandomAccessFileTest {</p>
<p>@Test</p>
<p>public void test1() throws FileNotFoundException {</p>
<p>RandomAccessFile raf1= null;</p>
<p>RandomAccessFile raf2= null;</p>
<p>try {</p>
<p>raf1 = new RandomAccessFile(new File("pic.jpg"),"r");</p>
<p>raf2 = new RandomAccessFile(new File("pic1.jpg"),"rw");</p>
<p></p>
<p>int len=0;</p>
<p>byte []buffer=new byte[1024];</p>
<p></p>
<p>while((len= raf1.read(buffer))!=-1){</p>
<p>raf2.write(buffer,0,len);</p>
<p>}</p>
<p>} catch (IOException e) {</p>
<p>e.printStackTrace();</p>
<p>} finally {</p>
<p>if(raf1!=null){</p>
<p>try {</p>
<p>raf1.close();</p>
<p>} catch (IOException e) {</p>
<p>e.printStackTrace();</p>
<p>}</p>
<p>}</p>
<p>if(raf2!=null){</p>
<p>try {</p>
<p>raf2.close();</p>
<p>} catch (IOException e) {</p>
<p>e.printStackTrace();</p>
<p>}</p>
<p>}</p>
<p>}</p>
<p>}</p>
<p>@Test</p>
<p>public void test2() throws IOException {</p>
<p></p>
<p>RandomAccessFile raf=new RandomAccessFile("hello.txt","rw");</p>
<p>raf.seek(3);</p>
<p>raf.write("xyz".getBytes());</p>
<p>raf.close();</p>
<p>//helloworld123--&gt;helxyzorld123</p>
<p>}</p>
<p>//使用RandomAccessFile实现数据的插入效果</p>
<p>//helloworld123--&gt;helxyzloworld123</p>
<p>@Test</p>
<p>public void test3() throws IOException {</p>
<p>RandomAccessFile raf= null;</p>
<p>try {</p>
<p>raf = new RandomAccessFile("hello.txt","rw");</p>
<p>raf.seek(3);//将指针调到角标为3的位置</p>
<p>//保存指针3后面的所有数据到StringBuilder中</p>
<p>StringBuilder sb=new StringBuilder((int)new File("hello.txt").length());</p>
<p>int len=0;</p>
<p>byte buffer[]=new byte[1024];</p>
<p>while ((len=raf.read(buffer))!=-1){</p>
<p>sb.append(new String(buffer,0,len));</p>
<p>}</p>
<p>//调回指针，写入“xyz”</p>
<p>raf.seek(3);</p>
<p>raf.write("xyz".getBytes());</p>
<p>//将StringBuilder中的数据写入到文件中</p>
<p>raf.write(sb.toString().getBytes());</p>
<p>} catch (IOException e) {</p>
<p>e.printStackTrace();</p>
<p>} finally {</p>
<p>try {</p>
<p>raf.close();</p>
<p>} catch (IOException e) {</p>
<p>e.printStackTrace();</p>
<p>}</p>
<p>}</p>
<p></p>
<p>}</p>
<p></p>
<p></p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
