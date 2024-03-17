---
title: For each
updated: 2020-09-14T18:36:07.0000000+08:00
created: 2020-09-10T14:35:04.0000000+08:00
---

用于遍历集合和数组，但是无法对数据进行操作
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>package java01;</strong></p>
<p></p>
<p><strong>import java.util.ArrayList;</strong></p>
<p><strong>import java.util.Arrays;</strong></p>
<p><strong>import java.util.Collection;</strong></p>
<p></p>
<p><strong>public class foreachTest {</strong></p>
<p><strong>public static void main(String[] args) {</strong></p>
<p><strong>Collection coll = new ArrayList();</strong></p>
<p><strong>coll.add(123);</strong></p>
<p><strong>coll.add(456);</strong></p>
<p><strong>coll.add(new Person("Jerry",20));</strong></p>
<p><strong>coll.add(new String("Tom"));</strong></p>
<p><strong>coll.add(false);</strong></p>
<p><strong>//for(集合元素的类型 局部变量 : 集合对象)</strong></p>
<p><strong>//内部仍然调用了迭代器。</strong></p>
<p><strong>for(Object obj:coll){</strong></p>
<p><strong>System.out.println(obj);</strong></p>
<p><strong>}</strong></p>
<p><strong>// 不能实现赋值操作</strong></p>
<p><strong>String[] arr = new String[]{"MM","MM","MM"};</strong></p>
<p></p>
<p><strong>//增强for循环</strong></p>
<p><strong>for(String s : arr){</strong></p>
<p><strong>s = "GG";</strong></p>
<p><strong>}</strong></p>
<p></p>
<p><strong>System.out.println(Arrays.toString(arr));//[MM, MM, MM]</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
