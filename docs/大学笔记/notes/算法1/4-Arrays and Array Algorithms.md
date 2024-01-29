---
title: 4-Arrays and Array Algorithms
updated: 2021-01-05T17:19:29.0000000+08:00
created: 2020-12-22T19:50:04.0000000+08:00
---

一、重点
1，linear search
<table>
<colgroup>
<col style="width: 28%" />
<col style="width: 71%" />
</colgroup>
<thead>
<tr class="header">
<th><p>public int search(int[]arr, int key) {</p>
<blockquote>
<p>for(int i=0;i&lt;arr.length;i++) {</p>
<p>if(key==arr[i]) {</p>
<p>return i;</p>
<p>}</p>
<p>}</p>
<p>return -1;</p>
</blockquote>
<p>}</p></th>
<th><p>![image1](../../assets/49373d5a50544fa29efcbe593444d389.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

2，binary search
针对有序数组
<table>
<colgroup>
<col style="width: 23%" />
<col style="width: 76%" />
</colgroup>
<thead>
<tr class="header">
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
<th><p>![image2](../../assets/76c18edeb5314745991213b0a0d8db5a.png)</p>
<p></p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
![image3](../../assets/fc974085b70b42a7afded50c2547759f.png)

分析二分法
![image4](../../assets/62e203001d184cf9b6fb73684b01387e.png)

![image5](../../assets/4e1c488225f8425fb56d3c100294328a.png)

![image6](../../assets/c03b200365ea4a00aee699fa587b2a76.png)

![image7](../../assets/8d257dac3c804de984f81202c85eca1c.png)

![image8](../../assets/50ba44685fef4edd8f4b60452c500c32.png)
二、复习
1, Arrays

2, Random Numbers
![image9](../../assets/cbca215dca7647d5a50c38e244d69ead.png)

![image10](../../assets/8c18581f10b946528c75f52c7062af98.png)
3，Inserting an element
![image11](../../assets/7422228ca8f6439f96b7a2b162b3c28e.png)

Removing an Element
![image12](../../assets/2e3793fb0ec048b394fdb89c18789b56.png)

