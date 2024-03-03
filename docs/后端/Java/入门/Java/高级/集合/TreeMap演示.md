---
title: TreeMap演示
updated: 2020-09-14T18:04:20.0000000+08:00
created: 2020-09-13T17:31:56.0000000+08:00
---

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
<p><strong>import java.util.*;</strong></p>
<p></p>
<p><strong>public class TreeMapTest {</strong></p>
<p><strong>//向TreeMap中添加key-value，要求key必须是由同一个类创建的对象</strong></p>
<p><strong>//因为要按照key进行排序：自然排序 、定制排序</strong></p>
<p><strong>//自然排序</strong></p>
<p><strong>@Test</strong></p>
<p><strong>public void test1(){</strong></p>
<p><strong>TreeMap map = new TreeMap();</strong></p>
<p><strong>User u1 = new User("Tom",23);</strong></p>
<p><strong>User u2 = new User("Jerry",32);</strong></p>
<p><strong>User u3 = new User("Jack",20);</strong></p>
<p><strong>User u4 = new User("Rose",18);</strong></p>
<p></p>
<p><strong>map.put(u1,98);</strong></p>
<p><strong>map.put(u2,89);</strong></p>
<p><strong>map.put(u3,76);</strong></p>
<p><strong>map.put(u4,100);</strong></p>
<p><strong>Set entrySet=map.entrySet();</strong></p>
<p><strong>Iterator iterator=entrySet.iterator();</strong></p>
<p><strong>while (iterator.hasNext()){</strong></p>
<p><strong>Object obj= iterator.next();</strong></p>
<p><strong>Map.Entry entry=(Map.Entry)obj;</strong></p>
<p><strong>System.out.println(entry.getKey()+"--&gt;"+entry.getValue());</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p>
<p><strong>//定制排序</strong></p>
<p><strong>@Test</strong></p>
<p><strong>public void test2(){</strong></p>
<p><strong>TreeMap map = new TreeMap(new Comparator() {</strong></p>
<p><strong>@Override</strong></p>
<p><strong>public int compare(Object o1, Object o2) {</strong></p>
<p><strong>if(o1 instanceof User&amp;&amp;o2 instanceof User){</strong></p>
<p><strong>User u1=(User)o1;</strong></p>
<p><strong>User u2=(User)o2;</strong></p>
<p><strong>int compare=u1.getName().compareTo(u2.getName());</strong></p>
<p><strong>if(compare!=0){</strong></p>
<p><strong>return Integer.compare(u1.getAge(),u2.getAge());</strong></p>
<p><strong>}else{</strong></p>
<p><strong>return compare;</strong></p>
<p><strong>}</strong></p>
<p><strong>}else {</strong></p>
<p><strong>throw new RuntimeException("输入类型有误");</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p>
<p><strong>});</strong></p>
<p><strong>User u1 = new User("Tom",23);</strong></p>
<p><strong>User u2 = new User("Jerry",32);</strong></p>
<p><strong>User u3 = new User("Jack",20);</strong></p>
<p><strong>User u4 = new User("Rose",18);</strong></p>
<p></p>
<p><strong>map.put(u1,98);</strong></p>
<p><strong>map.put(u2,89);</strong></p>
<p><strong>map.put(u3,76);</strong></p>
<p><strong>map.put(u4,100);</strong></p>
<p></p>
<p><strong>Set entrySet=map.entrySet();</strong></p>
<p><strong>Iterator iterator=entrySet.iterator();</strong></p>
<p><strong>while(iterator.hasNext()){</strong></p>
<p><strong>Object obj=iterator.next();</strong></p>
<p><strong>Map.Entry entry=(Map.Entry)obj;</strong></p>
<p><strong>System.out.println(entry.getKey()+"--&gt;"+entry.getValue());</strong></p>
<p><strong>}</strong></p>
<p></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p>
<p></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>package java01;</strong></p>
<p></p>
<p><strong>import java.util.Objects;</strong></p>
<p></p>
<p><strong>public class User implements Comparable{</strong></p>
<p><strong>private String name;</strong></p>
<p><strong>private int age;</strong></p>
<p><strong>public User(String name,int age){</strong></p>
<p><strong>this.name=name;</strong></p>
<p><strong>this.age=age;</strong></p>
<p><strong>}</strong></p>
<p></p>
<p><strong>public String getName() {</strong></p>
<p><strong>return name;</strong></p>
<p><strong>}</strong></p>
<p></p>
<p><strong>public void setName(String name) {</strong></p>
<p><strong>this.name = name;</strong></p>
<p><strong>}</strong></p>
<p></p>
<p><strong>public int getAge() {</strong></p>
<p><strong>return age;</strong></p>
<p><strong>}</strong></p>
<p></p>
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
<p><strong>return Objects.hash(name, age);</strong></p>
<p><strong>}</strong></p>
<p><strong>//按照姓名从大到小排列,年龄从小到大排列</strong></p>
<p><strong>@Override</strong></p>
<p><strong>public int compareTo(Object o) {</strong></p>
<p><strong>if(o instanceof User){</strong></p>
<p><strong>User u=(User)o;</strong></p>
<p><strong>int compare=this.name.compareTo(u.name);</strong></p>
<p><strong>if(compare!=0){</strong></p>
<p><strong>return Integer.compare(this.age,u.age);</strong></p>
<p><strong>}else{</strong></p>
<p><strong>return compare;</strong></p>
<p><strong>}</strong></p>
<p><strong>}else{</strong></p>
<p><strong>throw new RuntimeException("输入类型有误");</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p></td>
</tr>
</tbody>
</table>
