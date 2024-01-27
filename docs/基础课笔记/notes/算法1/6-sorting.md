---
title: 6-sorting
updated: 2021-01-09T15:33:08.0000000+08:00
created: 2020-12-22T21:14:44.0000000+08:00
---

**Part A-search**
![image1](../../assets/b3d18d42c03c418ab24cec5006d77584.png)

**Part B-sorting**
Comparison based sort
![image2](../../assets/01acdcf0302c430db69072061432badc.png)

**1，Bubble Sort**
思路
<table>
<colgroup>
<col style="width: 45%" />
<col style="width: 54%" />
</colgroup>
<thead>
<tr class="header">
<th>![image3](../../assets/fdd03ec538d94296b3946cd264c5b4dc.png)</th>
<th><p>![image4](../../assets/ae6215000f3048ae9291c4fa96ddbae0.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

![image5](../../assets/1be2f9f88ee94227a2325732bf6ea847.png)

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>代码</p>
<p>public static void bubbleSort(int arr[]) {</p>
<blockquote>
<p>for(int i=0;i&lt;arr.length-1;i++) {</p>
<p>for(int j=0;j&lt;arr.length-1-i;j++) {</p>
<p>if(arr[j]&gt;arr[j+1]) {</p>
<p>int temp=arr[j];</p>
<p>arr[j]=arr[j+1];</p>
<p>arr[j+1]=temp;</p>
<p>}</p>
<p>}</p>
<p>}</p>
</blockquote>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

**2，selection sort**
一直把最小的放在前面
<table>
<colgroup>
<col style="width: 53%" />
<col style="width: 46%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image6](../../assets/e90d833166c34f45a1e5e0d8df7748e1.png)</p>
<p></p></th>
<th><p>![image7](../../assets/49f2093998954ab0ab1a7c1070422808.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

![image8](../../assets/03568a6d77fd4db4a0ea0fd0cf7ece48.png)

**3，insertion sort**
![image9](../../assets/7bd2e946a8044587bd6fdd16d55abf2f.png)

<table>
<colgroup>
<col style="width: 51%" />
<col style="width: 48%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image10](../../assets/54856f6dea48440fb679165fe1e06ef6.png)</p>
<p></p></th>
<th><p></p>
<p>![image11](../../assets/de8af8b29e7a409e97bca1b59b4eb03a.png)</p>
<p></p></th>
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
<th><p><strong>public static void InsertSort(int arr[1]) {</strong></p>
<p><strong>int insertVal=0;</strong></p>
<p><strong>int insertIndex=0;</strong></p>
<p><strong>for(int i=1;i&lt;arr.length;i++) {</strong></p>
<p><strong>//定义待插入的数</strong></p>
<p><strong>insertVal=arr[i];</strong></p>
<p><strong>insertIndex=i-1;//前一个数的下标</strong></p>
<p><strong></strong></p>
<p><strong>// 给 insertVal 找到插入的位置</strong></p>
<p><strong>// 说明</strong></p>
<p><strong>//1.insertIndex&gt;=0 保证在给 insertVal 找插入位置，不越界</strong></p>
<p><strong>//2.insertVal&lt;arr[insertIndex] 待插入的数，还没有找到插入位置</strong></p>
<p><strong>//3. 就需要将 arr[insertIndex] 后移</strong></p>
<p><strong>while(insertIndex&gt;=0&amp;&amp;insertVal&lt;arr[insertIndex]) {</strong></p>
<p><strong>arr[insertIndex+1]=arr[insertIndex];</strong></p>
<p><strong>insertIndex--;</strong></p>
<p><strong>}</strong></p>
<p><strong>// 当退出 while 循环时，说明插入的位置找到,insertIndex+1</strong></p>
<p><strong>//这里我们判断是否需要赋值</strong></p>
<p><strong>if(insertIndex+1!=i) {</strong></p>
<p><strong>arr[insertIndex+1]=insertVal;</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

4，Quick sort

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image12](../../assets/549964efcfb54d978e3af5d0f2266544.png)</p>
<p><strong>public static void QuickSortDemo(int []arr,int left,int right) {</strong></p>
<p><strong>int l=left;//左下标</strong></p>
<p><strong>int r=right;//右下标</strong></p>
<p><strong>int temp=0;</strong></p>
<p><strong>int pivot=arr[(left+right)/2];//选取它，其他数和它比较分类</strong></p>
<p><strong>//while 循环的目的是让比 pivot 值小放到左边 ，比 pivot 值大放到右边</strong></p>
<p><strong>while(l&lt;r) {</strong></p>
<p><strong>//在 pivot 的左边一直找,找到大于等于 pivot 值,才退出</strong></p>
<p><strong>while(arr[l]&lt;pivot) {</strong></p>
<p><strong>l+=1;</strong></p>
<p><strong>}</strong></p>
<p><strong>//在 pivot 的右边一直找,找到大于等于 pivot 值,才退出</strong></p>
<p><strong>while(arr[r]&gt;pivot) {</strong></p>
<p><strong>r-=1;</strong></p>
<p><strong>}</strong></p>
<p><strong>//如果 l&gt;=r 说明 pivot 的左右两的值，已经按照左边全部是</strong></p>
<p><strong>//小于等于 pivot 值，右边全部是大于等于 pivot 值</strong></p>
<p><strong>if(l&gt;=r) {</strong></p>
<p><strong>break;</strong></p>
<p><strong>}</strong></p>
<p><strong></strong></p>
<p><strong>//交换</strong></p>
<p><strong>temp=arr[l];</strong></p>
<p><strong>arr[l]=arr[r];</strong></p>
<p><strong>arr[r]=temp;</strong></p>
<p><strong></strong></p>
<p><strong>//如果交换完后，发现这个 arr[l]==pivot 值 相等 r--， 前移</strong></p>
<p><strong>//可以理解为：指定的pivot，里面有一个数和它相等，假如左边卡住，无法移动，右边退一步来推动查询</strong></p>
<p><strong>if(arr[l]==pivot) {</strong></p>
<p><strong>r-=1;</strong></p>
<p><strong>}</strong></p>
<p><strong>//如果交换完后，发现这个 arr[r]==pivot 值 相等 l++， 后移</strong></p>
<p><strong>if(arr[r]==pivot) {</strong></p>
<p><strong>l+=1;</strong></p>
<p><strong>}</strong></p>
<p><strong></strong></p>
<p><strong>}</strong></p>
<p><strong>// 如果 l==r, 必须 l++,r--, 否则为出现栈溢出</strong></p>
<p><strong>if(l==r) {</strong></p>
<p><strong>l+=1;</strong></p>
<p><strong>r-=1;</strong></p>
<p><strong>}</strong></p>
<p><strong>if(left&lt;r) {</strong></p>
<p><strong>QuickSortDemo(arr,left,r);</strong></p>
<p><strong>}</strong></p>
<p><strong>if(right&gt;l) {</strong></p>
<p><strong>QuickSortDemo(arr, l, right);</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

**5，Merge sort**\[no code\]
Divide and Conquer Approach
![image13](../../assets/3d7ef70876b549f999e0f769e000a5a1.png)

![image14](../../assets/26989a4e35554fccbf3c16b45ff740f9.png)
![image15](../../assets/ddb45399b7c1485b9c75522db95a8762.png)

| Stable/unstable      | A stable sorting algorithm is any sorting algorithm that preserves the relative ordering of items with equal values. |
|----------------------|----------------------------------------------------------------------------------------------------------------------|
| In-place / Out-place | an in-place algorithm is an algorithm which transforms input using no auxiliary data structure.                      |
![image16](../../assets/70e66109ffff4b5182c2ad9456733e6c.png)

![image17](../../assets/fbc245f0279841f3b9a516bfd30891bd.png)

总结
<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 49%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image18](../../assets/cabf1ea219e1441bb55046edfa16aa5a.png)</p>
<p></p></th>
<th><p>![image19](../../assets/0330d07905214a1a852bf67a1ad5f3a3.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

**Non-comparison**
1,counting sort(类似桶排序)
<table>
<colgroup>
<col style="width: 14%" />
<col style="width: 85%" />
</colgroup>
<thead>
<tr class="header">
<th><p></p>
<p></p>
<p></p></th>
<th><p>![image20](../../assets/024aedb9f92c45c99843142adbe9f43b.png)</p>
<p></p>
<p>![image21](../../assets/d93035963c974950b87a218a58011e7c.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

2，bucket sort【stable】

<table>
<colgroup>
<col style="width: 44%" />
<col style="width: 55%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image22](../../assets/3ebb2436b1ab43a9b4d9d2f930624308.png)</p>
<p></p></th>
<th><p></p>
<p>![image23](../../assets/26cbdf9aa9da4fad81056b4ba88e9b91.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

3，Radix Sort【从右到左】
<table>
<colgroup>
<col style="width: 97%" />
<col style="width: 2%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image24](../../assets/fb1ae3638af440afbe0bf7ebbeaea7a6.png)</p>
<p></p></th>
<th></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

