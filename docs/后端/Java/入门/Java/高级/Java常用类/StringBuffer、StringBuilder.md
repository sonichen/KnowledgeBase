---
title: StringBuffer、StringBuilder
updated: 2020-09-05T17:27:20.0000000+08:00
created: 2020-09-05T17:21:37.0000000+08:00
---

##  一、String、StringBuffer、StringBuilder三者的异同
1,对比String、StringBuffer、StringBuilder三者的效率：从高到低排列：**StringBuilder \> StringBuffer \> String**
2,码源
String:不可变的字符序列；**底层使用char\[\]存储**
StringBuffer:可变的字符序列；**线程安全的，效率低**；底层使用char\[\]存储
StringBuilder:可变的字符序列；jdk5.0新增的，**线程不安全的，效率高**；底层使用char\[\]存储
开发中建议大家使用：StringBuffer(int capacity) 或 StringBuilder(int capacity)
## 二、StringBuffer的常用方法
总结：
| 增   | append(xxx)                                                         |
|------|---------------------------------------------------------------------|
| 删   | delete(int start,int end)                                           |
| 改   | setCharAt(int n ,char ch) / replace(int start, int end, String str) |
| 查   | charAt(int n )                                                      |
| 插   | insert(int offset, xxx)                                             |
| 长度 | length();                                                           |
| 遍历 | for() + charAt() / toString()                                       |

| StringBuffer append(xxx)                             | 提供了很多的append()方法，用于进行字符串拼接             |
|------------------------------------------------------|----------------------------------------------------------|
| StringBuffer delete(int start,int end)               | 删除指定位置的内容                                       |
| StringBuffer replace(int start, int end, String str) | 把\[start,end)位置替换为str                              |
| StringBuffer insert(int offset, xxx)                 | 在指定位置插入xxx                                        |
| StringBuffer reverse()                               | 把当前字符序列逆转                                       |
| public int indexOf(String str)                       |                                                         |
| public String substring(int start,int end)           | 返回一个从start开始到end索引结束的左闭右开区间的子字符串 |
| public int length()                                  |                                                         |
| public char charAt(int n )                           |                                                         |
| public void setCharAt(int n ,char ch)                |                                                         |
