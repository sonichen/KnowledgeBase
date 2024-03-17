---
title: 数组Array
updated: 2024-01-30T16:45:37.0000000+08:00
created: 2020-07-30T11:51:37.0000000+08:00
---

## 一、数组的概述
### 1、概述
是多个相同类型数据按一定顺序排列 的集合
### 2、特点
（1）数组是有序排列的
（2）数组本身是**引用数据类型**，而**数组中的元素可以是任何数据类型**，包括 基本数据类型和引用数据类型。
（3）创建数组对象会在内存中开辟一整块连续的空间，而数组名中引用的是 这块连续空间的首地址。
（4）**数组的长度一旦确定，就不能修改**。
### 3、分类
| 按照维度 | 按照元素的数据类型分   |
|----------|------------------------|
| 一维数组 | 基本数据类型元素的数组 |
| 二维数组 | 引用数据类型元素的数组 |
| …        |                       |

## 二、一维数组
### 1、 声明和初始化
Java中使用**关键字new**来创建数组
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>int[] ids;//声明</p>
<p>//1.1 静态初始化:数组的初始化和数组元素的赋值操作同时进行</p>
<p>ids = new int[]{1001,1002,1003,1004};</p>
<p>ids1 = {1001,1002,1003,1004};</p>
<p>//1.2动态初始化:数组的初始化和数组元素的赋值操作分开进行</p>
<p>String[] names = new String[5];</p>
<p>//总结：数组一旦初始化完成，其长度就确定了</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
### 2、调用数组的指定位置的元素
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>//2.如何调用数组的指定位置的元素:通过角标的方式调用。</p>
<p>//数组的角标（或索引）从0开始的，到数组的长度-1结束。</p>
<p>names[0] = "王铭";</p>
<p>names[1] = "王赫";</p>
<p>names[2] = "张学良";</p>
<p>names[3] = "孙居龙";</p>
<p>names[4] = "王宏志";</p>
<p>//names[5] = "周扬";//报错</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
### 3、数组的长度
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>//属性:length</p>
<p>System.out.println(names.length);//5</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
### 4、遍历
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>for(int i = 0;i &lt; names.length;i++){</p>
<p>System.out.println(names[i]);</p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
### 5、数组元素的默认初始化值 
| 整型         | 0                    |
|--------------|----------------------|
| 浮点型       | 0.0                  |
| char型       | 0或'\u0000'，而非'0' |
| Boolean      | false                |
| 引用数据类型 | null                 |
### 
### 6、数组的内存解析 
内存结构
![image1](../../assets/d9c92dd1207d44aa9eeea896a2f4597d.png)

![image2](../../assets/df3d697e9080451481ff03ce193d0219.png)

## 三、多维数组
### 1、概述
对于二维数组的理解，我们可以看成是一维数组array1又作为另一个一维数组array2的元素而存在。
其实，从数组底层的运行机制来看，其实没有多维数组。
### 2. 二维数组的使用
#### *①声明和初始化*
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>//1.二维数组的声明和初始化</p>
<p>int[] arr = new int[]{1,2,3};//一维数组</p>
<p>//静态初始化</p>
<p>int[][] arr1 = new int[][]{{1,2,3},{4,5},{6,7,8}};</p>
<p>//动态初始化1</p>
<p>String[][] arr2 = new String[3][2];</p>
<p>//动态初始化2</p>
<p>String[][] arr3 = new String[3][];//具体可以以后定</p>
<p>//也是正确的写法：</p>
<p>int[] arr4[] = new int[][]{{1,2,3},{4,5,9,10},{6,7,8}};</p>
<p>int[] arr5[]={{1,2,3},{4,5},{6,7,8}};</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
#### *② 调用数组的指定位置的元素*
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>//2.如何调用数组的指定位置的元素</p>
<p>System.out.println(arr1[0][1]);//2</p>
<p>System.out.println(arr2[1][1]);//null</p>
<p></p>
<p>arr3[1] = new String[4];</p>
<p>System.out.println(arr3[1][0]);//null</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
#### *③ 数组的长度*
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>System.out.println(arr4.length);//3</p>
<p>System.out.println(arr4[0].length);//3</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
#### *④遍历数组*
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>for(int i = 0;i &lt; arr4.length;i++){</p>
<p></p>
<p>for(int j = 0;j &lt; arr4[i].length;j++){</p>
<p>System.out.print(arr4[i][j] + " ");</p>
<p>}</p>
<p>System.out.println();</p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

#### *⑤ 数组元素的默认初始化值* 
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>针对于初始化方式一：比如：int[][] arr = new int[4][3];</p>
<p>外层元素的初始化值为：地址值</p>
<p>内层元素的初始化值为：与一维数组初始化情况相同</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>针对于初始化方式二：比如：int[][] arr = new int[4][];</p>
<p>外层元素的初始化值为：null</p>
<p>内层元素的初始化值为：不能调用，否则报错。</p></td>
</tr>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>int[][] arr = new int[4][3];</p>
<p>System.out.println(arr[0]);//[I@15db9742</p>
<p>// [-一维数组; I--int类型；</p>
<p>System.out.println(arr[0][0]);//0</p>
<p></p>
<p>System.out.println(arr);//[[I@6d06d69c</p>
<p></p>
<p>String[][] arr2 = new String[4][2];</p>
<p>System.out.println(arr2[1]);//地址值</p>
<p>System.out.println(arr2[1][1]);//null</p>
<p></p>
<p></p>
<p>double[][] arr3 = new double[4][];</p>
<p>System.out.println(arr3[1]);//null</p>
<p>System.out.println(arr3[1][0]);//报错</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
####  *⑥ 数组的内存解析* 
![image3](../../assets/f4f7d1afac5f4eed8041dba9484ba088.png)
## 
### 3、练习
（1）int\[\] x,y\[\]; //x是一维数组，y是二维数组
一维数组：int\[\] x 或者int x\[\] 二维数组：int\[\]\[\] y 或者 int\[\] y\[\] 或者 int y\[\]\[\]
（2）创建一个长度为6的int型数组，要求数组元素的值都在1-30之间，且是随机赋值。同时，要求 元素的值各不相
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>创建一个长度为6的int型数组，要求数组元素的值都在1-30之间，且是随机赋值。同时，要求 元素的值各不相同</p>
<p>[0,90) + 10 [10,100)</p>
<p>[10,99] (int)(Math.random() * 90 + 10)</p>
<p>package basic.arraydemo;</p>
<p></p>
<p>public class ArrayTestDemo {</p>
<p></p>
<p>public static void main(String[] args) {</p>
<p>// TODO Auto-generated method stub</p>
<p>//方法一</p>
<p>int []arr=new int[10];</p>
<p>for(int i=0;i&lt;arr.length;i++) {</p>
<p>arr[i]=(int)(Math.random()*30+1);</p>
<p>boolean flag=true;</p>
<p>while(true) {</p>
<p>for(int j=0;j&lt;i;j++) {</p>
<p>if(arr[i]==arr[j]) {</p>
<p>flag=true;</p>
<p>break;</p>
<p>}</p>
<p>}</p>
<p>if(flag) {</p>
<p>arr[i]=(int)(Math.random()*30+1);</p>
<p>flag=false;</p>
<p>continue;</p>
<p>}</p>
<p>break;</p>
<p>}</p>
<p>}</p>
<p>for (int i = 0; i &lt; arr.length; i++) {</p>
<p>System.out.print(arr[i]+" ");</p>
<p>}</p>
<p>// 方法二</p>
<p>int[] arr1 = new int[6];</p>
<p>for(int i=0;i&lt;arr1.length;i++) {</p>
<p>arr1[i]=(int)(Math.random()*30+1);</p>
<p>for(int j=0;j&lt;i;j++) {</p>
<p>if(arr[i]==arr[j]) {</p>
<p>i--;</p>
<p>break;</p>
<p>}</p>
<p>}</p>
<p>}</p>
<p>for (int i = 0; i &lt; arr1.length; i++) {</p>
<p>System.out.print(arr1[i]+" ");</p>
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
（3）
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p></p>
<p></p>
<p>package basic.arraydemo;</p>
<p></p>
<p>public class ArrayTestDemo1 {</p>
<p></p>
<p>public static void main(String[] args) {</p>
<p>// TODO Auto-generated method stub</p>
<p>int[] array1,array2;</p>
<p>array1 = new int[]{2,3,5,7,11,13,17,19};</p>
<p>//显示array1的内容</p>
<p>for(int i = 0;i &lt; array1.length;i++){</p>
<p>System.out.print(array1[i] + "\t");</p>
<p>}</p>
<p>//赋值array2变量等于array1</p>
<p>array2 = array1;</p>
<p>//修改array2中的偶索引元素，使其等于索引值(如array[0]=0,array[2]=2)</p>
<p>for(int i = 0;i &lt; array2.length;i++){</p>
<p>if(i % 2 == 0){</p>
<p>array2[i] = i;</p>
<p>}</p>
<p>}</p>
<p>System.out.println();</p>
<p>//打印出array1</p>
<p>for(int i = 0;i &lt; array1.length;i++){</p>
<p>System.out.print(array1[i] + "\t");</p>
<p>}</p>
<p>}</p>
<p></p>
<p>}</p>
<p>Console</p>
<p>2 3 5 7 11 13 17 19</p>
<p>0 3 2 7 4 13 6 19</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## 四、常见算法
### 1.数组元素的赋值(杨辉三角、回形数等)
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th>使用二维数组打印一个 10 行杨辉三角。</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1</p>
<p>11</p>
<p>121</p>
<p>1331</p>
<p>14641</p>
<p>15101051</p>
<p>1615201561</p>
<p>172135352171</p>
<p>18285670562881</p>
<p>193684126126843691</p></td>
</tr>
</tbody>
</table>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>package basic.arraydemo;</p>
<p></p>
<p>public class ArrayTestDemo {</p>
<p></p>
<p>public static void main(String[] args) {</p>
<p>// TODO Auto-generated method stub</p>
<p>int [][]yangHui=new int[10][];</p>
<p>for(int i=0;i&lt;yangHui.length;i++) {</p>
<p>yangHui[i]=new int[i+1];</p>
<p>//给首末元素赋值</p>
<p>yangHui[i][0]=yangHui[i][i]=1;</p>
<p>for(int j = 1;j &lt; yangHui[i].length - 1;j++){</p>
<p>yangHui[i][j] = yangHui[i-1][j-1] + yangHui[i-1][j];</p>
<p>}</p>
<p>}</p>
<p>for(int i=0;i&lt;yangHui.length;i++) {</p>
<p>for(int j=0;j&lt;yangHui[i].length;j++) {</p>
<p>System.out.print(yangHui[i][j]+"\t");</p>
<p>}</p>
<p>System.out.println();</p>
<p>}</p>
<p>}</p>
<p></p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
### 2. 求数值型数组中元素的最大值、最小值、平均数、总和等
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>package basic.arraydemo;</p>
<p></p>
<p>public class ArrayTestDemo1 {</p>
<p></p>
<p>public static void main(String[] args) {</p>
<p>// TODO Auto-generated method stub</p>
<p>int[] arr= new int[]{2,3,5,7,11,13,17,19};</p>
<p>for(int i=0;i&lt;arr.length;i++) {</p>
<p>System.out.print(arr[i]+" " );</p>
<p>}</p>
<p>System.out.println();</p>
<p>//最大值</p>
<p>int max=arr[0];</p>
<p>for(int i=1;i&lt;arr.length;i++) {</p>
<p>if(arr[i]&gt;max) {</p>
<p>max=arr[i];</p>
<p>}</p>
<p>}</p>
<p>System.out.println("Max: "+max );</p>
<p>//总和</p>
<p>int sum=0;</p>
<p>for(int i=0;i&lt;arr.length;i++) {</p>
<p>sum=sum+arr[0];</p>
<p>}</p>
<p>//平均数</p>
<p>double avg=(sum+0.0)/arr.length;</p>
<p>System.out.println("Sum: "+sum );</p>
<p>System.out.println("Avg: "+avg );</p>
<p>}</p>
<p></p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
### 3. 数组的复制、反转、查找(线性查找、二分法查找)
数组的复制、反转
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>package basic.arraydemo;</p>
<p></p>
<p>public class ArrayTestDemo2 {</p>
<p></p>
<p>public static void main(String[] args) {</p>
<p>// TODO Auto-generated method stub</p>
<p>//算法的考查：数组的复制、反转、查找(线性查找、二分法查找)</p>
<p>String[] arr = new String[]{"JJ","DD","MM","BB","GG","AA"};</p>
<p>//数组的复制(区别于数组变量的赋值：arr1 = arr)</p>
<p>String[] arr1 = new String[arr.length];</p>
<p>for(int i = 0;i &lt; arr1.length;i++){</p>
<p>arr1[i] = arr[i];</p>
<p>}</p>
<p>for(int i=0;i&lt;arr1.length;i++) {</p>
<p>System.out.print(arr1[i]+" " );</p>
<p>}</p>
<p>System.out.println("----------------------");</p>
<p>//反转</p>
<p>//方法一</p>
<p>for(int i=0;i&lt;arr.length/2;i++) {</p>
<p>String temp=arr[i];</p>
<p>arr[i]=arr[arr.length-1-i];</p>
<p>arr[arr.length-1-i]=temp;</p>
<p>}</p>
<p>//方法二</p>
<p>for(int i=0,j=arr.length-1;i&lt;j;j--,i++) {</p>
<p>String temp=arr[i];</p>
<p>arr[i]=arr[j];</p>
<p>arr[j]=temp;</p>
<p>}</p>
<p>System.out.println("反转后：");</p>
<p>for(int i=0;i&lt;arr.length;i++) {</p>
<p>System.out.print(arr[i]+" " );</p>
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
查找
线性查找
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>package basic.arraydemo;</p>
<p></p>
<p>public class ArrayTestDemo2 {</p>
<p></p>
<p>public static void main(String[] args) {</p>
<p></p>
<p>String[] arr = new String[]{"JJ","DD","MM","BB","GG","AA"};</p>
<p>//线性查找：</p>
<p>String key="BB";</p>
<p>boolean isFlag=true;</p>
<p>for(int i=0;i&lt;arr.length;i++) {</p>
<p>if(key.equals(arr[i])) {</p>
<p>System.out.println("找到了指定的元素，位置为：" + i);</p>
<p>isFlag = false;</p>
<p>break;</p>
<p>}</p>
<p>}</p>
<p>if(isFlag) {</p>
<p>System.out.println("没有找到");</p>
<p>}</p>
<p>}</p>
<p></p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
二分法查找
**前提：所要查找的数组必须有序**。

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>int[] arr2 = new int[]{-98,-34,2,34,54,66,75,105,210,333};</p>
<p>int key=75;</p>
<p>int head=0;</p>
<p>int end=arr2.length-1;</p>
<p>boolean isFlag=true;</p>
<p>while(head&lt;=end) {</p>
<p>int middle=(head+end)/2;</p>
<p>if(arr2[middle]==key) {</p>
<p>System.out.println("找到了指定的元素，位置为：" + middle);</p>
<p>isFlag = false;</p>
<p>break;</p>
<p>}else if(arr2[middle]&gt;key) {</p>
<p>end = middle - 1;</p>
<p>}else {</p>
<p>head = middle + 1;</p>
<p>}</p>
<p>}</p>
<p>if(isFlag){</p>
<p>System.out.println("很遗憾，没有找到的啦！");</p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
### 4. 数组元素的排序算法（冒泡）
![image4](../../assets/76aa8fbf691c4286840f3e673dafa539.png)

冒泡排序
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>public class BubbleSortTest {</p>
<p>public static void main(String[] args) {</p>
<p></p>
<p>int[] arr = new int[]{43,32,76,-98,0,64,33,-21,32,99};</p>
<p></p>
<p>//冒泡排序</p>
<p>for(int i = 0;i &lt; arr.length - 1;i++){</p>
<p>1</p>
<p>for(int j = 0;j &lt; arr.length - 1 - i;j++){</p>
<p></p>
<p>if(arr[j] &gt; arr[j + 1]){</p>
<p>int temp = arr[j];</p>
<p>arr[j] = arr[j + 1];</p>
<p>arr[j + 1] = temp;</p>
<p>}</p>
<p></p>
<p>}</p>
<p></p>
<p>}1</p>
<p></p>
<p></p>
<p></p>
<p></p>
<p>for(int i = 0;i &lt; arr.length;i++){</p>
<p>System.out.print(arr[i] + "\t");</p>
<p>}</p>
<p></p>
<p>}</p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

快速排序
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p></p>
<p>public class QuickSort {</p>
<p>private static void swap(int[] data, int i, int j) {</p>
<p>int temp = data[i];</p>
<p>data[i] = data[j];</p>
<p>data[j] = temp;</p>
<p>}</p>
<p></p>
<p>private static void subSort(int[] data, int start, int end) {</p>
<p>if (start &lt; end) {</p>
<p>int base = data[start];</p>
<p>int low = start;</p>
<p>int high = end + 1;</p>
<p>while (true) {</p>
<p>while (low &lt; end &amp;&amp; data[++low] - base &lt;= 0)</p>
<p>;</p>
<p>while (high &gt; start &amp;&amp; data[--high] - base &gt;= 0)</p>
<p>;</p>
<p>if (low &lt; high) {</p>
<p>swap(data, low, high);</p>
<p>} else {</p>
<p>break;</p>
<p>}</p>
<p>}</p>
<p>swap(data, start, high);</p>
<p>subSort(data, start, high - 1);//递归调用</p>
<p>subSort(data, high + 1, end);</p>
<p>}</p>
<p>}</p>
<p>public static void quickSort(int[] data){</p>
<p>subSort(data,0,data.length-1);</p>
<p>}</p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
## 五、Arrays工具类
java.util.Arrays:操作数组的工具类，里面定义了很多操作数组的方法
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>package basic.arraydemo;</p>
<p>import java.util.Arrays;</p>
<p>public class ArrayTestDemo3 {</p>
<p></p>
<p>public static void main(String[] args) {</p>
<p>// TODO Auto-generated method stub</p>
<p>//1.boolean equals(int[] a,int[] b):判断两个数组是否相等。</p>
<p>int[] arr1 = new int[]{1,2,3,4};</p>
<p>int[] arr2 = new int[]{1,3,2,4};</p>
<p>boolean isEquals = Arrays.equals(arr1, arr2);</p>
<p>System.out.println(isEquals);</p>
<p>//2.String toString(int[] a):输出数组信息。</p>
<p>System.out.println(Arrays.toString(arr1));</p>
<p>//3.void fill(int[] a,int val):将指定值填充到数组之中。</p>
<p>Arrays.fill(arr1, 10);</p>
<p>System.out.println(Arrays.toString(arr1));</p>
<p>//4.void sort(int[] a):对数组进行排序。</p>
<p>Arrays.sort(arr2);</p>
<p>System.out.println(Arrays.toString(arr2));</p>
<p>//5.int binarySearch(int[] a,int key)</p>
<p>int[] arr3 = new int[]{-98,-34,2,34,54,66,79,105,210,333};</p>
<p>int index = Arrays.binarySearch(arr3,-33);</p>
<p>if(index &gt;= 0){</p>
<p>System.out.println(index);</p>
<p>}else{</p>
<p>System.out.println(index);//-3==-2-1=-index-1</p>
<p>System.out.println("未找到");</p>
<p>}</p>
<p>}</p>
<p>}</p>
<p>Console</p>
<p>[10, 10, 10, 10]</p>
<p>[1, 2, 3, 4]</p>
<p>-3</p>
<p>未找到</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
Arrays.copyOf复制数组
## 六、常见异常
数组中的常见异常：
1\. 数组角标越界的异常：ArrayIndexOutOfBoundsExcetion
2\. 空指针异常：NullPointerException
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>public class ArrayExceptionTest {</p>
<p>public static void main(String[] args) {</p>
<p></p>
<p>//1. 数组角标越界的异常：ArrayIndexOutOfBoundsExcetion</p>
<p>int[] arr = new int[]{1,2,3,4,5};</p>
<p></p>
<p>//for(int i = 0;i &lt;= arr.length;i++){</p>
<p>//System.out.println(arr[i]);</p>
<p>//}</p>
<p></p>
<p>//System.out.println(arr[-2]);</p>
<p></p>
<p>//System.out.println("hello");</p>
<p></p>
<p>//2.2. 空指针异常：NullPointerException</p>
<p>//情况一：</p>
<p>//int[] arr1 = new int[]{1,2,3};</p>
<p>//arr1 = null;</p>
<p>//System.out.println(arr1[0]);</p>
<p></p>
<p>//情况二：</p>
<p>//int[][] arr2 = new int[4][];</p>
<p>//System.out.println(arr2[0][0]);</p>
<p></p>
<p>//情况三：</p>
<p>String[] arr3 = new String[]{"AA","BB","CC"};</p>
<p>arr3[0] = null;</p>
<p>System.out.println(arr3[0].toString());</p>
<p>}</p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
