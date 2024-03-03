---
title: Set概述
updated: 2020-09-14T18:54:55.0000000+08:00
created: 2020-09-10T21:14:07.0000000+08:00
---

## 一、Set接口的框架
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>|----Collection接口：单列集合，用来存储一个一个的对象</p>
<p>|----Set接口：存储<strong>无序的、不可重复</strong>的数据 --&gt;高中讲的“集合”</p>
<blockquote>
<p>----HashSet：作为Set接口的主要实现类；线程不安全的；<strong>可以存储null值</strong></p>
</blockquote>
<p>|----LinkedHashSet：作为HashSet的子类；遍历其内部数据时，可以按照添加的顺序遍历</p>
<p>对于频繁的遍历操作，LinkedHashSet效率高于HashSet.</p>
<p>|----TreeSet：<strong>可以按照添加对象的指定属性，进行排序</strong>。</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
## 二、Set概述
1\. **Set接口中没有额外定义新的方法，使用的都是Collection中声明过的方法**。
2\. 要求：向Set(主要指：HashSet、LinkedHashSet)中添加的数据，**其所在的类一定要重写hashCode()和equals()**
要求：重写的hashCode()和equals()尽可能保持一致性：相等的对象必须具有相等的散列码
**重写两个方法的小技巧：对象中用作 equals() 方法比较的 Field，都应该用来计算 hashCode 值。**
## 三、Set内部
1、Set：存储无序的、不可重复的数据
以HashSet为例说明：
1\. **无序性：不等于随机性**。存储的数据在底层数组中并非按照数组索引的顺序添加，而是**根据数据的哈希值决定的**。

2\. 不可重复性：保证添加的元素按照equals()判断时，不能返回true.即：相同的元素只能添加一个。

2、添加元素的过程：以HashSet为例：
我们向HashSet中添加元素a,**首先**调用元素a所在类的hashCode()方法，**计算元素a的哈希值**，
此哈希值接着通过某种算法计算出在HashSet底层数组中的存放位置（即为：索引位置），判断
数组此位置上是否已经有元素：
如果此位置上没有其他元素，则元素a添加成功。 ---\>情况1

**如果此位置上有其他元素b(或以链表形式存在的多个元素）**，则比较元素a与元素b的hash值：

如果hash值不相同，则元素a添加成功。---\>情况2

如果hash值相同，进而需要调用元素a所在类的equals()方法：

equals()返回true,元素a添加失败

equals()返回false,则元素a添加成功。---\>情况2

对于添加成功的情况2和情况3而言：元素a 与已经存在指定索引位置上数据以链表的方式存储。
jdk 7 :元素a放到数组中，指向原来的元素。
jdk 8 :原来的元素在数组中，指向元素a
总结：七上八下

**HashSet底层：数组+链表的结构。**
**补充**
LinkedHashSet的使用
LinkedHashSet作为HashSet的子类，在添加数据的同时，每个数据还维护了两个引用，记录此数据前一个
数据和后一个数据。
优点：对于频繁的遍历操作，LinkedHashSet效率高于HashSet
## 四、练习
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>//练习：在List内去除重复数字值，要求尽量简单</strong></p>
<p><strong>@Test</strong></p>
<p><strong>public void test1(){</strong></p>
<p><strong>List list=new ArrayList();</strong></p>
<p><strong>list.add(new Integer(1));</strong></p>
<p><strong>list.add(new Integer(2));</strong></p>
<p><strong>list.add(new Integer(2));</strong></p>
<p><strong>list.add(new Integer(4));</strong></p>
<p><strong>list.add(new Integer(4));</strong></p>
<p><strong>List list2=distinctList(list);</strong></p>
<p><strong>for (Object l:list2) {</strong></p>
<p><strong>System.out.println(l);</strong></p>
<p><strong>}</strong></p>
<p></p>
<p><strong>}</strong></p>
<p><strong>public static List distinctList(List list){</strong></p>
<p><strong>HashSet set=new HashSet();</strong></p>
<p><strong>set.addAll(list);</strong></p>
<p><strong>return new ArrayList(set);</strong></p>
<p><strong>}</strong></p>
<p>![image1](../../../../assets/0b08e312d76d43f2a083a0ddda947490.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## 五、代码演示
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>package java03;</strong></p>
<p></p>
<p><strong>import java.util.Objects;</strong></p>
<p></p>
<p><strong>public class User implements Comparable{</strong></p>
<p><strong>private String name;</strong></p>
<p><strong>private int age;</strong></p>
<p></p>
<p><strong>public User(String name,int age){</strong></p>
<p><strong>this.name=name;</strong></p>
<p><strong>this.age=age;</strong></p>
<p><strong>}</strong></p>
<p></p>
<p><strong>public String getName() {</strong></p>
<p><strong>return name;</strong></p>
<p><strong>}</strong></p>
<p></p>
<p><strong>public int getAge() {</strong></p>
<p><strong>return age;</strong></p>
<p><strong>}</strong></p>
<p></p>
<p><strong>public void setName(String name) {</strong></p>
<p><strong>this.name = name;</strong></p>
<p><strong>}</strong></p>
<p></p>
<p><strong>public void setAge(int age) {</strong></p>
<p><strong>this.age = age;</strong></p>
<p><strong>}</strong></p>
<p></p>
<p><strong>@Override</strong></p>
<p><strong>public String toString() {</strong></p>
<p><strong>return "User{" +</strong></p>
<p><strong>"name='" + name + '\'' +</strong></p>
<p><strong>", age=" + age +</strong></p>
<p><strong>'}';</strong></p>
<p><strong>}</strong></p>
<p></p>
<p><strong>@Override</strong></p>
<p><strong>public boolean equals(Object o) {</strong></p>
<p><strong>if (this == o) return true;</strong></p>
<p><strong>if (o == null || getClass() != o.getClass()) return false;</strong></p>
<p><strong>User user = (User) o;</strong></p>
<p><strong>return age == user.age &amp;&amp;</strong></p>
<p><strong>Objects.equals(name, user.name);</strong></p>
<p><strong>}</strong></p>
<p></p>
<p><strong>@Override</strong></p>
<p><strong>public int hashCode() {</strong></p>
<p><strong>int result = name != null ? name.hashCode() : 0;</strong></p>
<p><strong>result = 31 * result + age;//避免偶然性，31是2的五次方-1，节约空间</strong></p>
<p><strong>return result;</strong></p>
<p><strong>}</strong></p>
<p><strong>//按照姓名从大到小排列,年龄从小到大排列</strong></p>
<p><strong>public int compareTo(Object obj){</strong></p>
<p><strong>if(obj instanceof User){</strong></p>
<p><strong>User user=(User)obj;</strong></p>
<p><strong>int compare=-this.name.compareTo(user.name);</strong></p>
<p><strong>if(compare!=0){</strong></p>
<p><strong>return compare;</strong></p>
<p><strong>}else{</strong></p>
<p><strong>return Integer.compare(this.age,user.age);</strong></p>
<p><strong>}</strong></p>
<p><strong>}else {</strong></p>
<p><strong>throw new RuntimeException("输入的类型不正确");</strong></p>
<p><strong>}</strong></p>
<p></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p>
<p></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>package java03;</strong></p>
<p></p>
<p><strong>import org.junit.Test;</strong></p>
<p></p>
<p><strong>import java.util.HashSet;</strong></p>
<p><strong>import java.util.Iterator;</strong></p>
<p><strong>import java.util.LinkedHashSet;</strong></p>
<p><strong>import java.util.Set;</strong></p>
<p></p>
<p><strong>public class SetTest {</strong></p>
<p><strong>//还重写任何方法</strong></p>
<p><strong>@Test</strong></p>
<p><strong>public void test1(){</strong></p>
<p><strong>Set set = new HashSet();</strong></p>
<p><strong>set.add(456);</strong></p>
<p><strong>set.add(123);</strong></p>
<p><strong>set.add(123);</strong></p>
<p><strong>set.add("AA");</strong></p>
<p><strong>set.add("CC");</strong></p>
<p><strong>set.add(new User("Tom",12));</strong></p>
<p><strong>set.add(new User("Tom",12));</strong></p>
<p><strong>set.add(129);</strong></p>
<p><strong>Iterator it=set.iterator();</strong></p>
<p><strong>while(it.hasNext()){</strong></p>
<p><strong>System.out.println(it.next());</strong></p>
<p><strong>}</strong></p>
<p><strong>/*</strong></p>
<p><strong>AA</strong></p>
<p><strong>CC</strong></p>
<p><strong>129</strong></p>
<p><strong>User{name='Tom', age=12}</strong></p>
<p><strong>456</strong></p>
<p><strong>User{name='Tom', age=12}</strong></p>
<p><strong>123</strong></p>
<p><strong>*/</strong></p>
<p><strong>}</strong></p>
<p><strong>//重写方equals后</strong></p>
<p><strong>@Test</strong></p>
<p><strong>public void test2(){</strong></p>
<p><strong>Set set = new LinkedHashSet();</strong></p>
<p><strong>set.add(456);</strong></p>
<p><strong>set.add(123);</strong></p>
<p><strong>set.add(123);</strong></p>
<p><strong>set.add("AA");</strong></p>
<p><strong>set.add("CC");</strong></p>
<p><strong>set.add(new User("Tom",12));</strong></p>
<p><strong>set.add(new User("Tom",12));</strong></p>
<p><strong>set.add(129);</strong></p>
<p><strong>Iterator it=set.iterator();</strong></p>
<p><strong>while(it.hasNext()){</strong></p>
<p><strong>System.out.println(it.next());</strong></p>
<p><strong>}</strong></p>
<p><strong>/*</strong></p>
<p><strong>456</strong></p>
<p><strong>123</strong></p>
<p><strong>AA</strong></p>
<p><strong>CC</strong></p>
<p><strong>User{name='Tom', age=12}</strong></p>
<p><strong>129</strong></p>
<p><strong>*/</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p>
<p></p></td>
</tr>
<tr class="even">
<td><p><strong>package java03;</strong></p>
<p></p>
<p><strong>import org.junit.Test;</strong></p>
<p></p>
<p><strong>import java.util.Comparator;</strong></p>
<p><strong>import java.util.Iterator;</strong></p>
<p><strong>import java.util.TreeSet;</strong></p>
<p></p>
<p><strong>/**</strong></p>
<p><strong>* 1.向TreeSet中添加的数据，要求是相同类的对象。</strong></p>
<p><strong>* 2.两种排序方式：自然排序（实现Comparable接口） 和 定制排序（Comparator）</strong></p>
<p><strong>* 3.自然排序中，比较两个对象是否相同的标准为：compareTo()返回0.不再是equals().</strong></p>
<p><strong>* 4.定制排序中，比较两个对象是否相同的标准为：compare()返回0.不再是equals().</strong></p>
<p><strong>*/</strong></p>
<p><strong>public class TreeSetTest {</strong></p>
<p><strong>@Test</strong></p>
<p><strong>public void test1(){</strong></p>
<p><strong>TreeSet set=new TreeSet();</strong></p>
<p><strong>// 失败：不能添加不同类的对象</strong></p>
<p><strong>// set.add(123);</strong></p>
<p><strong>// set.add(456);</strong></p>
<p><strong>// set.add("AA");</strong></p>
<p><strong>// set.add(new User("Tom",12));</strong></p>
<p></p>
<p><strong>//举例一：</strong></p>
<p><strong>set.add(34);</strong></p>
<p><strong>set.add(-34);</strong></p>
<p><strong>set.add(43);</strong></p>
<p><strong>set.add(11);</strong></p>
<p><strong>set.add(8);</strong></p>
<p><strong>/**</strong></p>
<p><strong>* -34</strong></p>
<p><strong>* 8</strong></p>
<p><strong>* 11</strong></p>
<p><strong>* 34</strong></p>
<p><strong>* 43</strong></p>
<p><strong>*/</strong></p>
<p></p>
<p><strong>Iterator iterator=set.iterator();</strong></p>
<p><strong>while(iterator.hasNext()){</strong></p>
<p><strong>System.out.println(iterator.next());</strong></p>
<p><strong>}</strong></p>
<p></p>
<p><strong>}</strong></p>
<p><strong>@Test</strong></p>
<p><strong>public void test2(){</strong></p>
<p><strong>Comparator com=new Comparator() {</strong></p>
<p><strong>@Override</strong></p>
<p><strong>public int compare(Object o1, Object o2) {</strong></p>
<p><strong>if(o1 instanceof User&amp;&amp;o2 instanceof User){</strong></p>
<p><strong>User u1=(User)o1;</strong></p>
<p><strong>User u2=(User)o2;</strong></p>
<p><strong>return Integer.compare(u1.getAge(),u2.getAge());</strong></p>
<p><strong>}else{</strong></p>
<p><strong>throw new RuntimeException("输入类型不正确");</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p>
<p><strong>};</strong></p>
<p><strong>TreeSet set = new TreeSet(com);</strong></p>
<p><strong>set.add(new User("Tom",12));</strong></p>
<p><strong>set.add(new User("Jerry",32));</strong></p>
<p><strong>set.add(new User("Jim",2));</strong></p>
<p><strong>set.add(new User("Mike",65));</strong></p>
<p><strong>set.add(new User("Mary",33));</strong></p>
<p><strong>set.add(new User("Jack",33));</strong></p>
<p><strong>set.add(new User("Jack",56));</strong></p>
<p></p>
<p></p>
<p><strong>Iterator iterator = set.iterator();</strong></p>
<p><strong>while(iterator.hasNext()){</strong></p>
<p><strong>System.out.println(iterator.next());</strong></p>
<p><strong>}</strong></p>
<p><strong>/**</strong></p>
<p><strong>* User{name='Jim', age=2}</strong></p>
<p><strong>* User{name='Tom', age=12}</strong></p>
<p><strong>* User{name='Jerry', age=32}</strong></p>
<p><strong>* User{name='Mary', age=33}</strong></p>
<p><strong>* User{name='Jack', age=56}</strong></p>
<p><strong>* User{name='Mike', age=65}</strong></p>
<p><strong>*/</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p></td>
</tr>
</tbody>
</table>
