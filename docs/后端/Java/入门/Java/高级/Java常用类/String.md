---
title: String
updated: 2020-09-05T17:21:10.0000000+08:00
created: 2020-09-05T11:29:20.0000000+08:00
---

## 一、String概述
String:字符串，使用一对""引起来表示。
1.String声明为final的，不可被继承
2.String实现了Serializable接口：表示字符串是支持序列化的。
实现了Comparable接口：表示String可以比较大小
3.String内部定义了final char\[\] value用于存储字符串数据
4.String:**不可变性**。
体现：
1.当对字符串重新赋值时，需要重写指定内存区域赋值，不能使用原有的value进行赋值。
2\. 当对现有的字符串进行连接操作时，也需要重新指定内存区域赋值，不能使用原有的value进行赋值。
3\. 当调用String的replace()方法修改指定字符或字符串时，也需要重新指定内存区域赋值，不能使用原有的value进行赋值。
5.通过字面量的方式（区别于new）给一个字符串赋值，此时的字符串值声明在字符串常量池中。
6.字符串常量池中是不会存储相同内容的字符串的。
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>1.常量与常量的拼接结果在常量池。且常量池中不会存在相同内容的常量。</p>
<p>2.只要其中有一个是变量，结果就在堆中。</p>
<p>3.如果拼接的结果调用intern()方法，返回值就在常量池中</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
## 二、String实例化方式
1，通过字面量定义的方式
2，通过new + 构造器的方式
3，面试题：
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>String s = new String("abc");方式创建对象，在内存中创建了几个对象？</p>
<p><strong>两个</strong>:一个是堆空间中new结构，另一个是char[]对应的常量池中的数据："abc"</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## 三、String的方法
int length()返回字符串的长度
| char charAt(int index)                         | 返回某索引处的字符                                                                                                               |
|------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------|
| boolean isEmpty()                              | 判断是否是空字符串                                                                                                               |
| String toLowerCase()                           | 将 String 中的所有字符转换为小写                                                                                                 |
| String toUpperCase()                           | 将 String 中的所有字符转换为大写                                                                                                 |
| String trim()                                  | 返回字符串的副本，忽略**前导**空白和**尾部**空白                                                                                 |
| boolean equals(Object obj)                     | 比较字符串的内容是否相同                                                                                                         |
| boolean equalsIgnoreCase(String anotherString) | 与equals方法类似，忽略大小写                                                                                                     |
| String concat(String str)                      | 将指定字符串连接到此字符串的结尾。 **等价于用“+”**                                                                               |
| int compareTo(String anotherString)            | 比较两个字符串的大小                                                                                                             |
| String substring(int beginIndex)               | 返回一个新的字符串，它是此字符串的从 beginIndex开始截取到最后的一个子字符串。                                                    |
| String substring(int beginIndex, int endIndex) | 返回一个新字符串，它是此字 符串从beginIndex开始截取到endIndex(不包含)的一个子字符串。                                            |
| boolean endsWith(String suffix）               | 测试此字符串是否以指定的后缀结束                                                                                                 |
| boolean startsWith(String prefix)              | 测试此字符串是否以指定的前缀开始                                                                                                 |
| boolean startsWith(String prefix, int toffset) | 测试此字符串从指定索引开始的 子字符串是否以指定前缀开始                                                                          |
| boolean contains(CharSequence s)               | 当且仅当此字符串包含指定的 char 值序列 时，返回 true                                                                             |
| int indexOf(String str)                        | 返回指定子字符串在此字符串中第一次出现处的索引                                                                                   |
| int indexOf(String str, int fromIndex)         | 返回指定子字符串在此字符串中第一次出 现处的索引，从指定的索引开始                                                                |
| int lastIndexOf(String str)                    | 返回指定子字符串在此字符串中最右边出现处的索引                                                                                   |
| int lastIndexOf(String str, int fromIndex)     | 返回指定子字符串在此字符串中最后 一次出现处的索引，从指定的索引开始反向搜索 **注：indexOf和lastIndexOf方法如果未找到都是返回-1** |

| String replace(char oldChar, char newChar)                    | 返回一个新的字符串，它是 通过用 newChar 替换此字符串中出现的所有 oldChar 得到的。                                                                                                                     |
|---------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| String replace(CharSequence target, CharSequence replacement) | 使 用指定的字面值替换序列替换此字符串所有匹配字面值目标序列的子字符串。 String replaceAll(String regex, String replacement) 使用给 定 的 replacement 替换此字符串所有匹配给定的正则表达式的子字符串。 |
| String replaceFirst(String regex, String replacement)         | 使用给 定 的 replacement 替换此字符串匹配给定的正则表达式的第一个子字符串。                                                                                                                           |
| boolean matches(String regex)                                 | 告知此字符串是否匹配给定的正则表达式。                                                                                                                                                                |
| String\[\] split(String regex)                                | 根据给定正则表达式的匹配拆分此字符串。                                                                                                                                                                |
| String\[\] split(String regex, int limit)                     | 根据匹配给定的正则表达式来拆分此 字符串，最多不超过limit个，如果超过了，剩下的全部都放到最后一个元素中。                                                                                              |

### 四、String类与其他结构之间的转换
### 1， String 与基本数据类型、包装类之间的转换。
| String --\> 基本数据类型、包装类：调用包装类的静态方法 | parseXxx(str)                |
|--------------------------------------------------------|------------------------------|
| 基本数据类型、包装类 --\> String                       | 调用String重载的valueOf(xxx) |
### 2， String 与 char\[\]之间的转换
| String --\> char\[\] | 调用String的toCharArray() |
|----------------------|---------------------------|
| char\[\] --\> String | 调用String的构造器        |
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>public void test2() {</p>
<p>String str="hello";</p>
<p>char[]charArr=str.toCharArray();//String--&gt;char[]</p>
<p>//char[]--&gt;String</p>
<p>String newStr=new String(charArr);</p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

### 3，String 与 byte\[\]之间的转换
编码：String --\> byte\[\]:调用String的getBytes()
解码：byte\[\] --\> String:调用String的构造器

编码：字符串 --\>字节 (看得懂 ---\>看不懂的二进制数据)
解码：编码的逆过程，字节 --\> 字符串 （看不懂的二进制数据 ---\> 看得懂）

说明：解码时，要求解码使用的字符集必须与编码时使用的字符集一致，否则会出现乱码。
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>@Test</p>
<p>public void test3() throws UnsupportedEncodingException {</p>
<p>String str1 = "abc123中国";</p>
<p>byte[] bytes = str1.getBytes();//使用默认的字符集，进行编码。</p>
<p>System.out.println(Arrays.toString(bytes));</p>
<p></p>
<p>byte[] gbks = str1.getBytes("gbk");//使用gbk字符集进行编码。</p>
<p>System.out.println(Arrays.toString(gbks));</p>
<p></p>
<p>System.out.println("******************");</p>
<p></p>
<p>String str2 = new String(bytes);//使用默认的字符集，进行解码。</p>
<p>System.out.println(str2);</p>
<p></p>
<p>String str3 = new String(gbks);</p>
<p>System.out.println(str3);//出现乱码。原因：编码集和解码集不一致！</p>
<p></p>
<p></p>
<p>String str4 = new String(gbks, "gbk");</p>
<p>System.out.println(str4);//没有出现乱码。原因：编集和解码集一致！</p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
