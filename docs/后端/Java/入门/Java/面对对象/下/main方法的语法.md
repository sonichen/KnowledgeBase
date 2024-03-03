---
title: main方法的语法
updated: 2020-08-11T10:27:05.0000000+08:00
created: 2020-08-11T09:11:31.0000000+08:00
---

# main方法的语法
2020年8月11日
9:11

## 一、main()方法的使用说明：
1\. main()方法作为程序的入口
2\. main()方法也是一个普通的静态方法

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>public class MainTest {</p>
<p></p>
<p></p>
<p>public static void main(String[] args) {//入口</p>
<p></p>
<p>Main.main(new String[100]);</p>
<p></p>
<p>MainTest test = new MainTest();</p>
<p>test.show();</p>
<p></p>
<p>}</p>
<p>public void show(){</p>
<p></p>
<p>}</p>
<p>}</p>
<p></p>
<p></p>
<p>class Main{</p>
<p></p>
<p>public static void main(String[] args) {</p>
<p></p>
<p>for(int i = 0;i &lt; args.length;i++){</p>
<p>args[i] = "args_" + i;</p>
<p>System.out.println(args[i]);</p>
<p>}</p>
<p></p>
<p>}</p>
<p></p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

3\. main()方法可以作为我们与控制台交互的方式。（之前：使用Scanner）
-在eclipse中
1，先运行一次，生成字节码

2，

![image1](../../assets/cbe3cf3e65f5419785813017974c97f8.png)

3，

![image2](../../assets/e8630582bf09478ca51232348fc63155.png)

4，

![image3](../../assets/c176731520c94cae889a6feca377c8bc.png)
-命令行（记得去掉包名）
![image4](../../assets/9ef484c963c8421093c31c26196c6e6a.png)

