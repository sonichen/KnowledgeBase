---
title: List接口
updated: 2020-09-14T18:36:13.0000000+08:00
created: 2020-09-10T14:45:28.0000000+08:00
---

## 一、List概述
1\. List接口框架
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>|----Collection接口：单列集合，用来存储一个一个的对象</p>
<blockquote>
<p>|----List接口：存储<strong>有序的、可重复的</strong>数据。 --&gt;“动态”数组,替换原有的数组</p>
<p><strong>|----ArrayList：作为List接口的主要实现类；线程不安全的，效率高；底层使用Object[] elementData存储</strong></p>
<p>|----LinkedList：对于频繁的插入、删除操作，使用此类效率比ArrayList高；底层使用双向链表存储</p>
<p>|----Vector：作为List接口的古老实现类；线程安全的，效率低；底层使用Object[] elementData存储</p>
</blockquote></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
2\. ArrayList的源码分析：
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>2.1 jdk 7情况下</p>
<p>ArrayList list = new ArrayList();//底层创建了长度是10的Object[]数组elementData</p>
<p>list.add(123);//elementData[0] = new Integer(123);</p>
<p>...</p>
<p>list.add(11);//如果此次的添加导致底层elementData数组容量不够，则扩容。</p>
<p>默认情况下，扩容为原来的容量的<strong>1.5</strong>倍，同时需要将原有数组中的数据复制到新的数组中。</p>
<p><strong>结论：建议开发中使用带参的构造器：ArrayList list = new ArrayList(int capacity)</strong></p>
<p>2.2 jdk 8中ArrayList的变化：</p>
<p>ArrayList list = new ArrayList();//底层Object[] elementData初始化为{}.并没有创建长度为10的数组</p>
<p>list.add(123);//第一次调用add()时，底层才创建了长度10的数组，并将数据123添加到elementData[0]</p>
<p>...</p>
<p>后续的添加和扩容操作与jdk 7 无异。</p>
<p>2.3 小结：jdk7中的ArrayList的对象的创建类似于单例的饿汉式，而jdk8中的ArrayList的对象</p>
<p>的创建类似于单例的懒汉式，延迟了数组的创建，节省内存。</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
3\. LinkedList的源码分析：
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>LinkedList list = new LinkedList(); 内部声明了Node类型的first和last属性，默认值为null</p>
<p>list.add(123);//将123封装到Node中，创建了Node对象。</p>
<p>其中，Node定义为：体现了LinkedList的双向链表的说法</p>
<p>private static class Node&lt;E&gt; {</p>
<p>E item;</p>
<p>Node&lt;E&gt; next;</p>
<p>Node&lt;E&gt; prev;</p>
<p></p>
<p>Node(Node&lt;E&gt; prev, E element, Node&lt;E&gt; next) {</p>
<p>this.item = element;</p>
<p>this.next = next;</p>
<p>this.prev = prev;</p>
<p>}</p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

4\. Vector的源码分析：
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>jdk7和jdk8中通过Vector()构造器创建对象时，底层都创建了长度为10的数组。</p>
<p>在扩容方面，默认扩容为原来的数组长度的2倍。</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
面试题：ArrayList、LinkedList、Vector三者的异同？
同：三个类都是实现了List接口，存储数据的特点相同：存储有序的、可重复的数据
不同：见上
## 二、常用方法
增：
| void add(int index, Object ele)            | 在index位置插入ele元素                    |
|--------------------------------------------|-------------------------------------------|
| boolean addAll(int index, Collection eles) | 从index位置开始将eles中的所有元素添加进来 |

删：
remove(int index) / remove(Object obj)

改：
| Object set(int index, Object ele) | 设置指定index位置的元素为ele |
|-----------------------------------|------------------------------|
|                                  |                             |
查：
| Object get(int index)       | 获取指定index位置的元素           |
|-----------------------------|-----------------------------------|
| int indexOf(Object obj)     | 返回obj在集合中首次出现的位置     |
| int lastIndexOf(Object obj) | 返回obj在当前集合中末次出现的位置 |

其他：
| List subList(int fromIndex, int toIndex) | 返回从fromIndex到toIndex位置的子集合 |
|------------------------------------------|--------------------------------------|

长度：
size()

遍历：① Iterator迭代器方式
② 增强for循环
③ 普通的循环
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>public void test1() {</strong></p>
<p><strong>ArrayList list = new ArrayList();</strong></p>
<p><strong>list.add(123);</strong></p>
<p><strong>list.add(456);</strong></p>
<p><strong>list.add("AA");</strong></p>
<p></p>
<p><strong>//方式一：Iterator迭代器方式</strong></p>
<p><strong>Iterator iterator = list.iterator();</strong></p>
<p><strong>while (iterator.hasNext()) {</strong></p>
<p><strong>System.out.println(iterator.next());</strong></p>
<p><strong>}</strong></p>
<p></p>
<p><strong>//方式二：增强for循环</strong></p>
<p><strong>for (Object obj : list) {</strong></p>
<p><strong>System.out.println(obj);</strong></p>
<p><strong>}</strong></p>
<p></p>
<p><strong>//方式三：普通for循环</strong></p>
<p><strong>for (int i = 0; i &lt; list.size(); i++) {</strong></p>
<p><strong>System.out.println(list.get(i));</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## 三、方法演示
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>@Test</strong></p>
<p><strong>public void test3(){</strong></p>
<p><strong>ArrayList list = new ArrayList();</strong></p>
<p><strong>list.add(123);</strong></p>
<p><strong>list.add(456);</strong></p>
<p><strong>list.add("AA");</strong></p>
<p><strong>list.add(new Person("Tom",12));</strong></p>
<p><strong>list.add(456);</strong></p>
<p></p>
<p><strong>//int indexOf(Object obj):返回obj在集合中首次出现的位置。如果不存在，返回-1.</strong></p>
<p><strong>//int lastIndexOf(Object obj):返回obj在当前集合中末次出现的位置。如果不存在，返回-1.</strong></p>
<p><strong>System.out.println(list.indexOf("AA"));//2</strong></p>
<p><strong>System.out.println(list.lastIndexOf("AA"));//2</strong></p>
<p></p>
<p><strong>//Object remove(int index):移除指定index位置的元素，并返回此元素</strong></p>
<p><strong>Object obj=list.remove(0);</strong></p>
<p><strong>System.out.println(obj);//123</strong></p>
<p><strong>System.out.println(list);//[456, AA, Person{name='Tom', age=12}, 456]</strong></p>
<p></p>
<p><strong>//Object set(int index, Object ele):设置指定index位置的元素为ele</strong></p>
<p><strong>list.set(1,"CC");</strong></p>
<p><strong>System.out.println(list);//[456, CC, Person{name='Tom', age=12}, 456]</strong></p>
<p></p>
<p><strong>//List subList(int fromIndex, int toIndex):返回从fromIndex到toIndex位置的左闭右开区间的子集合</strong></p>
<p><strong>List subList=list.subList(2,4);</strong></p>
<p><strong>System.out.println(subList);//[Person{name='Tom', age=12}, 456]</strong></p>
<p><strong>System.out.println(list);//[456, CC, Person{name='Tom', age=12}, 456]</strong></p>
<p><strong>}</strong></p>
<p><strong>@Test</strong></p>
<p><strong>public void test2(){</strong></p>
<p><strong>ArrayList list = new ArrayList();</strong></p>
<p><strong>list.add(123);</strong></p>
<p><strong>list.add(456);</strong></p>
<p><strong>list.add("AA");</strong></p>
<p><strong>list.add(new Person("Tom",12));</strong></p>
<p><strong>list.add(456);</strong></p>
<p><strong>System.out.println(list);//[123, 456, AA, Person{name='Tom', age=12}, 456]</strong></p>
<p><strong>//void add(int index, Object ele):在index位置插入ele元素</strong></p>
<p><strong>list.add(1,"BB");</strong></p>
<p><strong>System.out.println(list);//[123, BB, 456, AA, Person{name='Tom', age=12}, 456]</strong></p>
<p><strong>//boolean addAll(int index, Collection eles):从index位置开始将eles中的所有元素添加进来</strong></p>
<p><strong>List list1= Arrays.asList(1,2,3);</strong></p>
<p><strong>list.addAll(list1);</strong></p>
<p><strong>System.out.println(list.size());//9</strong></p>
<p></p>
<p><strong>//Object get(int index):获取指定index位置的元素</strong></p>
<p><strong>System.out.println(list.get(0));//123</strong></p>
<p><strong>}</strong></p>
<p><strong></strong></p>
<p><strong>}</strong></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
