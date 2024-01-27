---
title: 9-recursion
updated: 2021-01-08T17:27:54.0000000+08:00
created: 2020-12-28T09:51:55.0000000+08:00
---

9-recursion
2020年12月28日
9:51

<table>
<colgroup>
<col style="width: 9%" />
<col style="width: 28%" />
<col style="width: 62%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>iterate</th>
<th>recursion</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>优点</td>
<td>速度快，结构简单，效率高</td>
<td>代码更简洁清晰，可读性更好。</td>
</tr>
<tr class="even">
<td>缺点</td>
<td><p>1，不容易 理解 ，编写复杂问题时困难。</p>
<p>2，并不能解决所有的问题</p></td>
<td>由于递归需要系统堆栈，所以空间消耗要比非递归代码要大很多。而且，如果递归深度太大，可能系统撑不住。</td>
</tr>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 9%" />
<col style="width: 36%" />
<col style="width: 53%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Iterative</th>
<th>recursion</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>优点</td>
<td>It has fast speed, simple structure and high efficiency.</td>
<td>The code is cleaner and more readable.</td>
</tr>
<tr class="even">
<td>缺点</td>
<td><p>1. It is not easy to understand and it is difficult to solve complex problems.</p>
<p>2. It cannot solve all the problems</p></td>
<td>Because recursion requires a system stack, space consumption is much larger than for non-recursive code. Also, if the recursion depth is too deep, the system may not hold.</td>
</tr>
</tbody>
</table>

一、Recursion
1，定义
Recursion is when a method calls itself
• The method keeps calling itself until it reaches the base
case and then it filters back up

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>• The characteristics of a recursive method are</p>
<blockquote>
<p>• It calls itself</p>
<p>• When it calls itself, it does so to solve a smaller problem</p>
<p>• There’s some version of the problem that is simple enough that the routine can solve it and return without calling itself</p>
</blockquote></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

2，递归程序必须有base case【让递归结束的判断】，否则程序无法停止

二、案例
1，triangular numbers
![image1](../../assets/2350e17896d0424f9a9feec9fc752215.png)

<table>
<colgroup>
<col style="width: 44%" />
<col style="width: 55%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image2](../../assets/ca8471dce8204fc484b15a6ef4d34579.png)</p>
<p></p></th>
<th>![image3](../../assets/c10ad3d4ec5948b582740047e7225410.png)</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

2，Fibonacci Series
1）The Fibonacci series is as follows: 1, 1, 2, 3, 5, 8, 13…

<table>
<colgroup>
<col style="width: 65%" />
<col style="width: 34%" />
</colgroup>
<thead>
<tr class="header">
<th>![image4](../../assets/baec26f11490457680202b7aa197b6ad.png)</th>
<th><p>public static void test(int n) {</p>
<blockquote>
<p>int f1=1;</p>
<p>int f2=1;</p>
<p>int current=0;</p>
<p>if(n==1||n==2) {</p>
<p>System.out.println(1);</p>
<p>return;</p>
<p>}</p>
<p>for(int i=2;i&lt;n;i++) {</p>
<p>current=f1+f2;</p>
<p>int temp=f2;</p>
<p>f2=current;</p>
<p>f1=temp;</p>
<p>}</p>
<p>System.out.println(current);</p>
<p></p>
</blockquote>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

数较小的时候用递归较好，数较大的时候用递归需要等待很久
Lesson: recursion can simplify code **but is not always more efficient**
![image5](../../assets/47842bf99ed64b72a52bfac1580b5e3c.png)

| Bottom-Up solution for Fibonacci Series                                                                                                                                                                                                                                                             | Top-Down recursive approach                                                                                                                                                                                                                                                               |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ![image6](../../assets/ee5bba00d1b8401592ff42d1db115073.png) | ![image7](../../assets/4619b89727694f40b69ff124a16a2316.png) |

2）The efficiency of recursion
![image8](../../assets/bc4ba40fd2fe4393b4756d3e5b411352.png)

2，检查是否回文palindrome
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th>检查是否回文palindrome</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>public static boolean isPalindrome(String s) {</p>
<p>if(s.length()&lt;=1) {</p>
<p>return true;</p>
<p>}else {</p>
<p>char first=s.charAt(0);</p>
<p>char last=s.charAt(s.length()-1);</p>
<p>if(first!=last) {</p>
<p>return false;</p>
<p>}else {</p>
<p>return isPalindrome(s.substring(1,s.length()-1));</p>
<p>}</p>
<p>}</p>
<p>}</p></td>
</tr>
</tbody>
</table>

3，Raising to a power
![image9](../../assets/62582625bf8f46d9a774a4e2be8f1c76.png)

<table>
<colgroup>
<col style="width: 76%" />
<col style="width: 23%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image10](../../assets/66331e607066411d9341f0f89846d7bc.png)</p>
<p></p></th>
<th><p>In the previous example, the power was always even, so could be</p>
<p>easily divided by two</p>
<p>• If the power happens to be odd then we need to subtract one</p>
<p>from the power, solve that, and then multiply it again to account</p>
<p>for the power we subtracted</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

三、动态规划 dynamic programming
1**，Dynamic programming** (dynamic optimization) is a method for solving a complex problem by breaking it down into a collection of simpler subproblems, solving each of those subproblems just once, and storing their solutions
把大问题分成小问题，让多个重复的小问题不重复解决，将解决过的问题存储起来，直接使用
![image11](../../assets/b81d7342a51b49798baf9eb00867f634.png)

注意
1\. The problem involves overlapping sub-problems that need to be solved again and again.
In dynamic programming we solve these sub problems **only once** and **store it for future** use

2\. If a big problem can be solved by using the solutions of the sub problems then we say that problem also has an optimal substructure property

四、分治算法
Divide and Conquer
1，
The big problem is **divided into two smaller problems** and each one is solved separately
These are then divided into even smaller problems etc。The process continues until you get to the base case
which can be solved easily with no further division

2，案例
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>1--Binary Search</p>
<p>![image12](../../assets/bebbaf3d1ac447d794962c051cf018a6.png)</p>
<p></p>
<table>
<colgroup>
<col style="width: 58%" />
<col style="width: 41%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image13](../../assets/d0873eafb3c34585b1dc389bbcca64dd.png)</p>
<p></p></th>
<th><p>private static int binarySearch(int[] arr, int target) {</p>
<blockquote>
<p>int left=0;</p>
<p>int right=arr.length-1;</p>
<p>while(left&lt;=right) {</p>
<p>int mid=(left+right)/2;</p>
<p>if(target==arr[mid]) {</p>
<p>return mid;</p>
<p>}else if(target&lt;arr[mid]) {</p>
<p>right=mid-1;</p>
<p>}else {</p>
<p>left=mid+1;</p>
<p>}</p>
<p>}</p>
<p>return -1;</p>
</blockquote>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>2--汉诺塔Towers of Hanoi</p>
<p></p>
<p>1，问T</p>
<table>
<colgroup>
<col style="width: 51%" />
<col style="width: 48%" />
</colgroup>
<thead>
<tr class="header">
<th>![image14](../../assets/17fc6fdddd094eb3ae1d7a9ad8640bff.png)</th>
<th>![image15](../../assets/db38f411b6974e84a1b1222498ad3076.png)</th>
</tr>
</thead>
<tbody>
</tbody>
</table>
<p></p>
<p>古代的做法</p>
<p>![image16](../../assets/50df8827b26f463db6e088d3dcc251cf.png)</p>
<p></p>
<p>2，算法</p>
<table>
<colgroup>
<col style="width: 43%" />
<col style="width: 41%" />
<col style="width: 15%" />
</colgroup>
<thead>
<tr class="header">
<th><p>• Assuming there are n disks, the algorithm is</p>
<blockquote>
<p>• 1. Move the subtree of the top n-1 disks from source rod to</p>
<p>intermediate rod</p>
<p>• 2. Move the remaining largest disk from source rod to</p>
<p>destination rod</p>
<p>• 3. Now solve moving the subtree from intermediate rod to</p>
<p>destination rod</p>
</blockquote>
<p>![image17](../../assets/717efb3d64d24a6ab8cc12c6b36e619b.png)</p></th>
<th><p>![image18](../../assets/7369c0b9575243e4840c2b331cd6b391.png)</p>
<blockquote>
<p></p>
</blockquote></th>
<th><p>![image19](../../assets/c4232777057e4dfdaefd8b6441fe6793.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table></td>
</tr>
<tr class="even">
<td><p>3--Mergesort</p>
<table>
<colgroup>
<col style="width: 60%" />
<col style="width: 39%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image20](../../assets/b6c9c02062f24711aa667a76a793cc49.png)</p>
<p></p>
<p>![image21](../../assets/92d376c7eb554f1da5609dee388444e7.png)</p>
<p></p></th>
<th>![image22](../../assets/fc04be111ec14188940e417e6b7de1c4.png)</th>
</tr>
</thead>
<tbody>
</tbody>
</table>
<p></p>
<p>1,思路</p>
<p><strong>divide an array in half and sort each half</strong></p>
<p>![image23](../../assets/48a4360d28f4459eb2e696110795232c.png)</p>
<p><strong>1）merge</strong></p>
<p>• So, if we want to marge any two lists s1 and s2,</p>
<p>we need at most <strong>s1.length() + s2.length() steps</strong></p>
<table>
<colgroup>
<col style="width: 59%" />
<col style="width: 40%" />
</colgroup>
<thead>
<tr class="header">
<th>![image24](../../assets/a078eec7405f4f2db7c9333f3296c6ec.png)</th>
<th>![image25](../../assets/59c0376f727d453d8a493717f696ece0.png)</th>
</tr>
</thead>
<tbody>
</tbody>
</table>
<p></p>
<table>
<colgroup>
<col style="width: 47%" />
<col style="width: 52%" />
</colgroup>
<thead>
<tr class="header">
<th>![image26](../../assets/4113221ff274424491236f8c4678c1dc.png)</th>
<th>![image27](../../assets/f03e760f10a44bb294f3e4d11cfd9456.png)</th>
</tr>
</thead>
<tbody>
</tbody>
</table>
<p></p>
<p>2)分开</p>
<table>
<colgroup>
<col style="width: 55%" />
<col style="width: 44%" />
</colgroup>
<thead>
<tr class="header">
<th>![image28](../../assets/b752b9f8e88c4811b71146fa3634f723.png)</th>
<th><p>![image29](../../assets/bea673e4fa7d4c90931d6d2cb57fe37f.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
<p></p>
<p>用循环来解</p>
<table>
<colgroup>
<col style="width: 49%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image30](../../assets/606799aac826447eb48494d6cb721561.png)</p>
<p></p></th>
<th>![image31](../../assets/8a7ea5c7ceae4247ae85727632af11b1.png)</th>
</tr>
</thead>
<tbody>
</tbody>
</table>
<p></p>
<p>3)Copies and Comparisons</p>
<p>![image32](../../assets/c854e0ee6ae1479b8459f7cc553c7eb0.png)</p>
<p></p>
<p>2,分析</p>
<p>![image33](../../assets/03422a73957b4cb1b29cd0244f739ae0.png)</p>
<p>![image34](../../assets/9a1fd4e9fff547afbb46468fdfaa14ba.png)</p>
<p></p>
<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 49%" />
</colgroup>
<thead>
<tr class="header">
<th>![image35](../../assets/e890b6b555ab446db79a7af8c17bb4af.png)</th>
<th>![image36](../../assets/acbaed6b7ca34dcb82b0e88bc5c929e0.png)</th>
</tr>
</thead>
<tbody>
</tbody>
</table></td>
</tr>
</tbody>
</table>

[时间复杂度分析](https://blog.csdn.net/qq_32534441/article/details/95098059)
![image37](../../assets/fced7022d5c74025ad5b4a6ca685c36f.png)

![image38](../../assets/7367ac9f7d0c41b9985903733b331cdd.png)

![image39](../../assets/dbe104744ac9429698033970c39d3748.png)

![image40](../../assets/59916804df7c4d8c91b8c943b57c4863.png)
![image41](../../assets/db842b055a5a47688ccfb45b94801fc2.png)

