---
title: Java比较器
updated: 2020-09-08T07:54:48.0000000+08:00
created: 2020-09-07T13:19:37.0000000+08:00
---

一、说明：Java中的对象，正常情况下，只能进行比较：== 或 != 。不能使用 \> 或 \< 的

但是在开发场景中，我们需要对多个对象进行排序，言外之意，就需要比较对象的大小。

如何实现？使用两个接口中的任何一个：Comparable 或 Comparator

二、Comparable接口与Comparator的使用的对比：
Comparable接口的方式一旦一定，保证Comparable接口实现类的对象在任何位置都可以比较大小。
Comparator接口属于临时性的比较。
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>package java1;</p>
<p></p>
<p>public class Goods implements Comparable{</p>
<p>private String name;</p>
<p>private double price;</p>
<p>public Goods(String name,double price){</p>
<p>this.name=name;</p>
<p>this.price=price;</p>
<p>}</p>
<p></p>
<p>public double getPrice() {</p>
<p>return price;</p>
<p>}</p>
<p></p>
<p>public void setName(String name) {</p>
<p>this.name = name;</p>
<p>}</p>
<p>public String getName(){</p>
<p>return name;</p>
<p>}</p>
<p>public void setPrice(double price){</p>
<p>this.price=price;</p>
<p>}</p>
<p>public String toString(){</p>
<p>return name+": "+price;</p>
<p>}</p>
<p>public int compareTo(Object obj){</p>
<p>if(obj instanceof Goods){</p>
<p>Goods goods=(Goods)obj;</p>
<p>if (this.price&gt;goods.price){</p>
<p>return 1;</p>
<p>}else if(this.price&lt;goods.price){</p>
<p>return -1;</p>
<p>}else{</p>
<p>return this.name.compareTo(goods.name);</p>
<p>}</p>
<p>// return Double.compare(this.price,goods.price);</p>
<p>}</p>
<p>// return 0;</p>
<p>throw new RuntimeException("传入的数据类型不一致");</p>
<p></p>
<p>}</p>
<p>}</p></th>
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
<th><p>package java1;</p>
<p></p>
<p>import org.junit.Test;</p>
<p></p>
<p>import java.util.Arrays;</p>
<p>import java.util.Comparator;</p>
<p></p>
<p>public class CompareTest {</p>
<p>/**</p>
<p>* Comparable接口的使用举例： 自然排序</p>
<p>* 1.像String、包装类等实现了Comparable接口，重写了compareTo(obj)方法，给出了比较两个对象大小的方式。</p>
<p>* 2.像String、包装类重写compareTo()方法以后，进行了从小到大的排列</p>
<p>* 3. 重写compareTo(obj)的规则：</p>
<p>* 如果当前对象this大于形参对象obj，则返回正整数，</p>
<p>* 如果当前对象this小于形参对象obj，则返回负整数，</p>
<p>* 如果当前对象this等于形参对象obj，则返回零。</p>
<p>* 4. 对于自定义类来说，如果需要排序，我们可以让自定义类实现Comparable接口，重写compareTo(obj)方法。</p>
<p>* 在compareTo(obj)方法中指明如何排序</p>
<p>*/</p>
<p>@Test</p>
<p>public void test1(){</p>
<p>String[] arr = new String[]{"AA","CC","KK","MM","GG","JJ","DD"};</p>
<p>Arrays.sort(arr);</p>
<p>System.out.println(Arrays.toString(arr));</p>
<p>//[AA, CC, DD, GG, JJ, KK, MM]</p>
<p>}</p>
<p>@Test</p>
<p>public void test2(){</p>
<p>Goods[] arr = new Goods[5];</p>
<p>arr[0] = new Goods("lenovoMouse",34);</p>
<p>arr[1] = new Goods("dellMouse",43);</p>
<p>arr[2] = new Goods("xiaomiMouse",12);</p>
<p>arr[3] = new Goods("huaweiMouse",65);</p>
<p>arr[4] = new Goods("microsoftMouse",43);</p>
<p>Arrays.sort(arr);</p>
<p>System.out.println(Arrays.toString(arr));</p>
<p>//[xiaomiMouse: 12.0, lenovoMouse: 34.0, dellMouse: 43.0, microsoftMouse: 43.0, huaweiMouse: 65.0]</p>
<p>}</p>
<p>/**</p>
<p>*</p>
<p>* Comparator接口的使用：定制排序</p>
<p>* 1.背景：</p>
<p>* 当元素的类型没有实现java.lang.Comparable接口而又不方便修改代码，</p>
<p>* 或者实现了java.lang.Comparable接口的排序规则不适合当前的操作，</p>
<p>* 那么可以考虑使用 Comparator 的对象来排序</p>
<p>* 2.重写compare(Object o1,Object o2)方法，比较o1和o2的大小：</p>
<p>* 如果方法返回正整数，则表示o1大于o2；</p>
<p>* 如果返回0，表示相等；</p>
<p>* 返回负整数，表示o1小于o2。</p>
<p>*/</p>
<p>@Test</p>
<p>public void test3(){</p>
<p>String[] arr = new String[]{"AA","CC","KK","MM","GG","JJ","DD"};</p>
<p>Arrays.sort(arr,new Comparator(){</p>
<p>@Override</p>
<p>public int compare(Object o1, Object o2) {</p>
<p>if(o1 instanceof String &amp;&amp;o2 instanceof String){</p>
<p>String s1=(String)o1;</p>
<p>String s2=(String)o2;</p>
<p>return -s1.compareTo(s2);</p>
<p>}</p>
<p>// return 0;</p>
<p>throw new RuntimeException("输入的数据类型不一致");</p>
<p>}</p>
<p></p>
<p>});</p>
<p>System.out.println(Arrays.toString(arr));</p>
<p>// [MM, KK, JJ, GG, DD, CC, AA]</p>
<p>}</p>
<p>@Test</p>
<p>public void test4(){</p>
<p>Goods[] arr = new Goods[6];</p>
<p>arr[0] = new Goods("lenovoMouse",34);</p>
<p>arr[1] = new Goods("dellMouse",43);</p>
<p>arr[2] = new Goods("xiaomiMouse",12);</p>
<p>arr[3] = new Goods("huaweiMouse",65);</p>
<p>arr[4] = new Goods("huaweiMouse",224);</p>
<p>arr[5] = new Goods("microsoftMouse",43);</p>
<p>Arrays.sort(arr,new Comparator(){</p>
<p>//指明商品比较大小的方式:按照产品名称从低到高排序,再按照价格从高到低排序</p>
<p>@Override</p>
<p>public int compare(Object o1, Object o2) {</p>
<p>if(o1 instanceof Goods&amp;&amp;o2 instanceof Goods){</p>
<p>Goods goods1=(Goods)o1;</p>
<p>Goods goods2=(Goods)o2;</p>
<p>if(goods1.getName().equals(goods1.getName())){</p>
<p>return -Double.compare(goods1.getPrice(),goods2.getPrice());</p>
<p>}else{</p>
<p>return goods1.getName().compareTo(goods2.getName());</p>
<p>}</p>
<p>}</p>
<p>throw new RuntimeException("输入的数据类型不一致");</p>
<p>}</p>
<p>});</p>
<p>System.out.println(Arrays.toString(arr));</p>
<p>//[huaweiMouse: 224.0, huaweiMouse: 65.0, dellMouse: 43.0, microsoftMouse: 43.0, lenovoMouse: 34.0, xiaomiMouse: 12.0]</p>
<p>}</p>
<p>}</p>
<p></p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
