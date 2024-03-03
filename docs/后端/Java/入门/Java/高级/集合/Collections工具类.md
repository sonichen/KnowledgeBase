---
title: Collections工具类
updated: 2020-09-14T18:05:42.0000000+08:00
created: 2020-09-13T19:40:33.0000000+08:00
---

| reverse(List)          | 反转 List 中元素的顺序                                   |
|------------------------|----------------------------------------------------------|
| shuffle(List)          | 对 List 集合元素进行随机排序                             |
| sort(List)             | 根据元素的自然顺序对指定 List 集合元素按升序排序         |
| sort(List，Comparator) | 根据指定的 Comparator 产生的顺序对 List 集合元素进行排序 |
| swap(List，int， int)  | 将指定 list 集合中的 i 处元素和 j 处元素进行交换         |

| Object max(Collection)             | 根据元素的自然顺序，返回给定集合中的最大元素         |
|------------------------------------|------------------------------------------------------|
| Object max(Collection，Comparator) | 根据 Comparator 指定的顺序，返回给定集合中的最大元素 |
| Object min(Collection)             |                                                     |
| Object min(Collection，Comparator) |                                                     |

| int frequency(Collection，Object)                           | 返回指定集合中指定元素的出现次数 |
|-------------------------------------------------------------|----------------------------------|
| void copy(List dest,List src)                               | 将src中的内容复制到dest中        |
| boolean replaceAll(List list，Object oldVal，Object newVal) | 使用新值替换 List 对象的所有旧值 |

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
<p><strong>import java.util.Arrays;</strong></p>
<p><strong>import java.util.Collections;</strong></p>
<p><strong>import java.util.List;</strong></p>
<p></p>
<p><strong>public class CollectionTest {</strong></p>
<p><strong>@Test</strong></p>
<p><strong>public void test1(){</strong></p>
<p><strong>List list=new ArrayList();</strong></p>
<p><strong>list.add(123);</strong></p>
<p><strong>list.add(43);</strong></p>
<p><strong>list.add(765);</strong></p>
<p><strong>list.add(-97);</strong></p>
<p><strong>list.add(0);</strong></p>
<p><strong>//报异常：IndexOutOfBoundsException("Source does not fit in dest")</strong></p>
<p><strong>// List dest = new ArrayList();</strong></p>
<p><strong>// Collections.copy(dest,list);</strong></p>
<p><strong>List dest= Arrays.asList(new Object [list.size()]);//dest的size要大于等于list</strong></p>
<p><strong>// 复制list</strong></p>
<p><strong>Collections.copy(dest,list);</strong></p>
<p><strong>System.out.println(dest);//[123, 43, 765, -97, 0]</strong></p>
<p></p>
<p><strong>/*</strong></p>
<p><strong>Collections 类中提供了多个 synchronizedXxx() 方法，</strong></p>
<p><strong>该方法可使将指定集合包装成线程同步的集合，从而可以解决</strong></p>
<p><strong>多线程并发访问集合时的线程安全问题</strong></p>
<p></p>
<p><strong>*/</strong></p>
<p><strong>//返回的list1即为线程安全的List</strong></p>
<p><strong>List list1 = Collections.synchronizedList(list);</strong></p>
<p><strong>}</strong></p>
<p><strong>@Test</strong></p>
<p><strong>public void test2(){</strong></p>
<p><strong>List list = new ArrayList();</strong></p>
<p><strong>list.add(123);</strong></p>
<p><strong>list.add(43);</strong></p>
<p><strong>list.add(765);</strong></p>
<p><strong>list.add(765);</strong></p>
<p><strong>list.add(765);</strong></p>
<p><strong>list.add(-97);</strong></p>
<p><strong>list.add(0);</strong></p>
<p><strong>//System.out.println(list);//[123, 43, 765, 765, 765, -97, 0]</strong></p>
<p><strong>// Collections.reverse(list);[0, -97, 765, 765, 765, 43, 123]</strong></p>
<p><strong>//Collections.shuffle(list);//[43, -97, 0, 765, 765, 123, 765]\</strong></p>
<p><strong>// Collections.sort(list);//[-97, 0, 43, 123, 765, 765, 765]</strong></p>
<p><strong>// Collections.swap(list,1,2);[123, 765, 43, 765, 765, -97, 0]</strong></p>
<p></p>
<p><strong>int frequency=Collections.frequency(list,123);</strong></p>
<p><strong>System.out.println(list);</strong></p>
<p><strong>System.out.println(frequency);//1</strong></p>
<p></p>
<p><strong>}</strong></p>
<p></p>
<p><strong>}</strong></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
