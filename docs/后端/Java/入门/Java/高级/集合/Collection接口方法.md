---
title: Collection接口方法
updated: 2020-09-14T18:07:43.0000000+08:00
created: 2020-09-09T18:23:08.0000000+08:00
---

一、方法的使用
1，Collection 接口是 List、Set 和 Queue 接口的父接口，该接口里定义的方法 既可用于操作 Set 集合，也可用于操作 List 和 Queue 集合。
2，**JDK不提供此接口的任何直接实现，而是提供更具体的子接口**(如：Set和List)
实现。
3，在 Java5 之前，Java 集合会丢失容器中所有对象的数据类型，把所有对象都 当成 Object 类型处理；
从 JDK 5.0 增加了泛型以后，Java 集合可以记住容器中对象的数据类型。

增加
| add(Object e)            | 将元素e添加到集合coll中               |
|--------------------------|---------------------------------------|
| addAll(Collection coll1) | 将coll1集合中的元素添加到当前的集合中 |
删除
| remove(Object obj)          | 从当前集合中移除obj元素。                 |
|-----------------------------|-------------------------------------------|
| removeAll(Collection coll1) | 差集--从当前集合中移除coll1中所有的元素。 |
| clear()                     | 清空集合元素                              |
改
| retainAll(Collection coll1) | 交集--获取当前集合和coll1集合的交集，并返回给当前集合 |
|-----------------------------|-------------------------------------------------------|

查
<table>
<colgroup>
<col style="width: 31%" />
<col style="width: 68%" />
</colgroup>
<thead>
<tr class="header">
<th>size()</th>
<th>获取添加的元素的个数</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>isEmpty()</td>
<td>判断当前集合是否为空</td>
</tr>
<tr class="even">
<td>contains(Object obj)</td>
<td>判断当前集合中是否包含obj。我们在判断时会调用obj对象所在类的equals()。</td>
</tr>
<tr class="odd">
<td>containsAll(Collection coll1)</td>
<td>判断形参coll1中的所有元素是否都存在于当前集合中。</td>
</tr>
<tr class="even">
<td>equals(Object obj)</td>
<td>要想返回true，需要当前集合和形参集合的元素都相同。</td>
</tr>
<tr class="odd">
<td>hashCode()</td>
<td>返回当前对象的哈希值</td>
</tr>
<tr class="even">
<td><strong>数组和集合的转换</strong></td>
<td><p>集合 ---&gt;数组：toArray()</p>
<p>Object[] arr = coll.toArray();</p>
<p>数组 ---&gt;集合:调用Arrays类的静态方法<strong>asList()</strong></p>
<p>List&lt;String&gt; list = Arrays.asList(new String[]{"AA", "BB", "CC"});</p></td>
</tr>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>遍历：</p>
<p>iterator():返回Iterator接口的实例，用于遍历集合元素。放在IteratorTest.java中测试</p>
<p>集合元素的遍历操作，使用迭代器Iterator接口</p>
<p><strong>Iterator可以删除集合的元素，但是是遍历过程中通过迭代器对象的remove方 法，不是集合对象的remove方法</strong></p>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>// 1.内部的方法：hasNext() 和 next()</strong></p>
<p><strong>// 2.集合对象每次调用iterator()方法都得到一个全新的迭代器对象，</strong></p>
<p><strong>// 默认游标都在集合的第一个元素之前。</strong></p>
<p><strong>Collection coll = new ArrayList();</strong></p>
<p><strong>Iterator iterator=coll.iterator();</strong></p>
<p><strong>while (iterator.hasNext()){</strong></p>
<p><strong>System.out.println(iterator.next());</strong></p>
<p><strong>}</strong></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

##  二、演示
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>public class CollectionTest {</strong></p>
<p></p>
<p><strong>@Test</strong></p>
<p><strong>public void test1(){</strong></p>
<p><strong>Collection coll = new ArrayList();</strong></p>
<p></p>
<p><strong>//1.add(Object e):将元素e添加到集合coll中</strong></p>
<p><strong>coll.add("AA");</strong></p>
<p><strong>coll.add("BB");</strong></p>
<p><strong>coll.add(123);//自动装箱</strong></p>
<p><strong>coll.add(new Date());</strong></p>
<p></p>
<p><strong>//2.size():获取添加的元素的个数</strong></p>
<p><strong>System.out.println(coll.size());//4</strong></p>
<p></p>
<p><strong>//3.addAll(Collection coll1):将coll1集合中的元素添加到当前的集合中</strong></p>
<p><strong>Collection coll1 = new ArrayList();</strong></p>
<p><strong>coll1.add(456);</strong></p>
<p><strong>coll1.add("CC");</strong></p>
<p><strong>coll.addAll(coll1);</strong></p>
<p></p>
<p><strong>System.out.println(coll.size());//6</strong></p>
<p><strong>System.out.println(coll);</strong></p>
<p></p>
<p><strong>//4.clear():清空集合元素</strong></p>
<p><strong>coll.clear();</strong></p>
<p></p>
<p><strong>//5.isEmpty():判断当前集合是否为空</strong></p>
<p><strong>System.out.println(coll.isEmpty());</strong></p>
<p></p>
<p><strong>}</strong></p>
<p></p>
<p><strong>}</strong></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>package java01;</strong></p>
<p></p>
<p><strong>import org.junit.Test;</strong></p>
<p></p>
<p><strong>import java.util.ArrayList;</strong></p>
<p><strong>import java.util.Arrays;</strong></p>
<p><strong>import java.util.Collection;</strong></p>
<p><strong>import java.util.List;</strong></p>
<p></p>
<p><strong>public class CollectionTest {</strong></p>
<p><strong>@Test</strong></p>
<p><strong>public void test1(){</strong></p>
<p><strong>Collection coll=new ArrayList();</strong></p>
<p><strong>coll.add(123);</strong></p>
<p><strong>coll.add(456);</strong></p>
<p><strong>coll.add(new Person("Jack",20));</strong></p>
<p><strong>//1.contains(Object obj):判断当前集合中是否包含obj</strong></p>
<p><strong>System.out.println(coll.contains(123));//true</strong></p>
<p><strong>//我们在判断时会调用obj对象所在类的equals()。</strong></p>
<p><strong>System.out.println(coll.contains(new Person("Jack",20)));//false,调用了==</strong></p>
<p><strong>System.out.println(coll.contains(new Person("Jack",20)));//true--&gt;复写了equals方法</strong></p>
<p></p>
<p><strong>//2.containsAll(Collection coll1):判断形参coll1中的所有元素是否都存在于当前集合中。</strong></p>
<p><strong>Collection coll1= Arrays.asList(123, 456,new Person("Jack",20));</strong></p>
<p><strong>System.out.println(coll.containsAll(coll1));//true</strong></p>
<p></p>
<p><strong>}</strong></p>
<p><strong>@Test</strong></p>
<p><strong>public void test2(){</strong></p>
<p><strong>//3.remove(Object obj):从当前集合中移除obj元素。</strong></p>
<p><strong>Collection coll = new ArrayList();</strong></p>
<p><strong>coll.add(123);</strong></p>
<p><strong>coll.add(456);</strong></p>
<p><strong>coll.add(new Person("Jerry",20));</strong></p>
<p><strong>coll.add(new String("Tom"));</strong></p>
<p><strong>coll.add(false);</strong></p>
<p></p>
<p><strong>coll.remove(1234);</strong></p>
<p><strong>System.out.println(coll);//[123, 456, Person{name='Jerry', age=20}, Tom, false]</strong></p>
<p></p>
<p><strong>coll.remove(new Person("Jerry",20));</strong></p>
<p><strong>System.out.println(coll);//[123, 456, Tom, false]</strong></p>
<p></p>
<p><strong>//4. removeAll(Collection coll1):差集：从当前集合中移除coll1中所有的元素。</strong></p>
<p><strong>Collection coll1 = Arrays.asList(123,456);</strong></p>
<p><strong>coll.removeAll(coll1);</strong></p>
<p><strong>System.out.println(coll);//[Tom, false]</strong></p>
<p><strong>}</strong></p>
<p><strong>@Test</strong></p>
<p><strong>public void test3(){</strong></p>
<p><strong>Collection coll=new ArrayList();</strong></p>
<p><strong>coll.add(123);</strong></p>
<p><strong>coll.add(456);</strong></p>
<p><strong>coll.add(new Person("Jerry",20));</strong></p>
<p><strong>coll.add(new String("Tom"));</strong></p>
<p><strong>coll.add(false);</strong></p>
<p><strong>// 5.retainAll(Collection coll1):交集：获取当前集合和coll1集合的交集，并返回给当前集合</strong></p>
<p><strong>Collection coll1=Arrays.asList(123,456,788);</strong></p>
<p><strong>coll.retainAll(coll1);</strong></p>
<p><strong>System.out.println(coll);//调用toString()方法[123, 456]</strong></p>
<p><strong>//6.equals(Object obj):要想返回true，需要当前集合和形参集合的元素都相同。</strong></p>
<p><strong>Collection coll2 = new ArrayList();</strong></p>
<p><strong>coll2.add(123);</strong></p>
<p><strong>coll2.add(456);</strong></p>
<p><strong>System.out.println(coll.equals(coll2));//true</strong></p>
<p><strong>}</strong></p>
<p><strong>@Test</strong></p>
<p><strong>public void test4(){</strong></p>
<p><strong>Collection coll=new ArrayList();</strong></p>
<p><strong>coll.add(123);</strong></p>
<p><strong>coll.add(456);</strong></p>
<p><strong>coll.add(new Person("Jerry",20));</strong></p>
<p><strong>coll.add(new String("Tom"));</strong></p>
<p><strong>coll.add(false);</strong></p>
<p><strong>//7.hashCode():返回当前对象的哈希值</strong></p>
<p><strong>System.out.println(coll.hashCode());//-1200490100</strong></p>
<p></p>
<p><strong>//8.集合 ---&gt;数组：toArray()</strong></p>
<p><strong>Object []arr=coll.toArray();</strong></p>
<p><strong>for(int i=0;i&lt;arr.length;i++){</strong></p>
<p><strong>System.out.print(arr[i]+" ");</strong></p>
<p><strong>}//123 456 Person{name='Jerry', age=20} Tom false</strong></p>
<p></p>
<p><strong>//拓展：数组 ---&gt;集合:调用Arrays类的静态方法asList()</strong></p>
<p><strong>List list= Arrays.asList(123,345);</strong></p>
<p><strong>System.out.println(list);//[123, 345]</strong></p>
<p></p>
<p><strong>List&lt;String&gt; list1=Arrays.asList(new String[]{"AA","BB"});</strong></p>
<p><strong>System.out.println(list1);//"AA","BB"</strong></p>
<p></p>
<p><strong>List arr1 = Arrays.asList(new int[]{123, 456});</strong></p>
<p><strong>System.out.println(arr1.size());//1</strong></p>
<p></p>
<p><strong>List arr2 = Arrays.asList(new Integer[]{123, 456});</strong></p>
<p><strong>System.out.println(arr2.size());//2</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p>
<p></p></td>
</tr>
</tbody>
</table>
<p></p>
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>package java01;</strong></p>
<p></p>
<p><strong>import org.junit.Test;</strong></p>
<p></p>
<p><strong>import java.util.ArrayList;</strong></p>
<p><strong>import java.util.Collection;</strong></p>
<p><strong>import java.util.Iterator;</strong></p>
<p></p>
<p><strong>public class IteratorTest {</strong></p>
<blockquote>
<p><strong>// 1.内部的方法：hasNext() 和 next()</strong></p>
<p><strong>// 2.集合对象每次调用iterator()方法都得到一个全新的迭代器对象，</strong></p>
<p><strong>// 默认游标都在集合的第一个元素之前。</strong></p>
<p></p>
</blockquote>
<p><strong>@Test</strong></p>
<p><strong>public void test(){</strong></p>
<p><strong>Collection coll = new ArrayList();</strong></p>
<p><strong>coll.add(123);</strong></p>
<p><strong>coll.add(456);</strong></p>
<p><strong>coll.add(new Person("Jerry",20));</strong></p>
<p><strong>coll.add(new String("Tom"));</strong></p>
<p><strong>coll.add(false);</strong></p>
<p></p>
<p><strong>Iterator iterator=coll.iterator();</strong></p>
<p><strong>// 方式一（不推荐）</strong></p>
<p><strong>for(int i=0;i&lt;coll.size();i++){</strong></p>
<p><strong>// System.out.println(iterator.next());</strong></p>
<p><strong>}</strong></p>
<p><strong>// 方式二：常用</strong></p>
<p><strong>//hasNext():判断是否还有下一个元素</strong></p>
<p><strong>//next():①指针下移 ②将下移以后集合位置上的元素返回</strong></p>
<p><strong>while (iterator.hasNext()){</strong></p>
<p><strong>System.out.println(iterator.next());</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p>
<p><strong>/**</strong></p>
<p><strong>* //测试Iterator中的remove()</strong></p>
<p><strong>* //如果还未调用next()或在上一次调用 next 方法之后已经调用了 remove 方法，</strong></p>
<p><strong>* // 再调用remove都会报IllegalStateException。</strong></p>
<p><strong>*/</strong></p>
<p><strong>@Test</strong></p>
<p><strong>public void test1(){</strong></p>
<p><strong>Collection coll = new ArrayList();</strong></p>
<p><strong>coll.add(123);</strong></p>
<p><strong>coll.add(456);</strong></p>
<p><strong>coll.add(new Person("Jerry",20));</strong></p>
<p><strong>coll.add(new String("Tom"));</strong></p>
<p><strong>coll.add(false);</strong></p>
<p></p>
<p><strong>//删除集合中"Tom"</strong></p>
<p></p>
<p><strong>Iterator iterator=coll.iterator();</strong></p>
<p><strong>while(iterator.hasNext()){</strong></p>
<p><strong>Object obj=iterator.next();</strong></p>
<p><strong>if("Tom".equals(obj)){</strong></p>
<p><strong>iterator.remove();</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p>
<p></p>
<p><strong>iterator=coll.iterator();</strong></p>
<p><strong>while(iterator.hasNext()){</strong></p>
<p><strong>System.out.println(iterator.next());</strong></p>
<p><strong>}</strong></p>
<p><strong>// while (iterator.hasNext()){</strong></p>
<p><strong>// System.out.println(iterator.next());</strong></p>
<p><strong>// }//没有被删除？--》，这是拿了一个新的指针重新遍历</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
