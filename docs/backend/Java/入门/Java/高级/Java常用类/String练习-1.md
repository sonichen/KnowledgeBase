---
title: String练习
updated: 2020-09-05T16:56:08.0000000+08:00
created: 2020-09-05T16:37:47.0000000+08:00
---

1，
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>public void test4(){</p>
<p>String s1 = "javaEEhadoop";</p>
<p>String s2 = "javaEE";</p>
<p>String s3 = s2 + "hadoop";</p>
<p>System.out.println(s1 == s3);//false</p>
<p></p>
<p>final String s4 = "javaEE";//s4:常量</p>
<p>String s5 = s4 + "hadoop";</p>
<p>System.out.println(s1 == s5);//true</p>
<p></p>
<p>}</p>
<p></p>
<p>@Test</p>
<p>public void test3(){</p>
<p>String s1 = "javaEE";</p>
<p>String s2 = "hadoop";</p>
<p></p>
<p>String s3 = "javaEEhadoop";</p>
<p>String s4 = "javaEE" + "hadoop";</p>
<p>String s5 = s1 + "hadoop";</p>
<p>String s6 = "javaEE" + s2;</p>
<p>String s7 = s1 + s2;</p>
<p></p>
<p>System.out.println(s3 == s4);//true</p>
<p>System.out.println(s3 == s5);//false</p>
<p>System.out.println(s3 == s6);//false</p>
<p>System.out.println(s3 == s7);//false</p>
<p>System.out.println(s5 == s6);//false</p>
<p>System.out.println(s5 == s7);//false</p>
<p>System.out.println(s6 == s7);//false</p>
<p></p>
<p>String s8 = s6.intern();//返回值得到的s8使用的常量值中已经存在的“javaEEhadoop”</p>
<p>System.out.println(s3 == s8);//true</p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

2，
![image1](../../../assets/e912069ff0c646cfb1cbb667bfaf003a.png)

