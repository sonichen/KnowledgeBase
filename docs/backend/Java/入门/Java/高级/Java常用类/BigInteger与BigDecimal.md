---
title: BigInteger与BigDecimal
updated: 2020-09-08T08:19:27.0000000+08:00
created: 2020-09-07T13:20:08.0000000+08:00
---

1，java.math包的BigInteger可以表示**不可变的任意精度的整数**。
2， 构造器
BigInteger(String val)：根据字符串构建BigInteger对象
3，方法
| public BigInteger abs()                           | 返回此 BigInteger 的绝对值的 BigInteger。                          |
|---------------------------------------------------|--------------------------------------------------------------------|
| BigInteger add(BigInteger val)                    | 返回其值为 (this + val) 的 BigInteger                              |
| BigInteger subtract(BigInteger val)               | 返回其值为 (this - val) 的 BigInteger                              |
| BigInteger multiply(BigInteger val)               | 返回其值为 (this \* val) 的 BigInteger                             |
| BigInteger divide(BigInteger val)                 | 返回其值为 (this / val) 的 BigInteger。整数 相除只保留整数部分。   |
| BigInteger remainder(BigInteger val)              | 返回其值为 (this % val) 的 BigInteger。                            |
| BigInteger\[\] divideAndRemainder(BigInteger val) | 返回包含 (this / val) 后跟 (this % val) 的两个 BigInteger 的数组。 |
| BigInteger pow(int exponent)                      | 返回其值为 (thisexponent) 的 BigInteger                            |

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>首先说一下用法，BigDecimal中的divide主要就是用来做除法的运算。其中有这么一个方法.</p>
<p>public BigDecimal divide(BigDecimal divisor,int scale, int roundingMode)</p>
<p> 第一个参数是除数，第二个参数代表保留几位小数，第三个代表的是使用的模式。其中我们标题上就是其中的两种</p>
<p>BigDecimal.ROUND_DOWN:直接省略多余的小数，比如1.28如果保留1位小数，得到的就是1.2</p>
<p> BigDecimal.ROUND_UP:直接进位，比如1.21如果保留1位小数，得到的就是1.3</p>
<p> BigDecimal.ROUND_HALF_UP:四舍五入，2.35保留1位，变成2.4</p>
<p> BigDecimal.ROUND_HALF_DOWN:四舍五入，2.35保留1位，变成2.3</p></th>
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
<th><p>public void test3(){</p>
<p>BigInteger bi=new BigInteger("12456789009876543234567898765434567");</p>
<p>BigDecimal bd=new BigDecimal("2134567.1243567");</p>
<p>BigDecimal bd2=new BigDecimal("11");</p>
<p>System.out.println(bi);</p>
<p>System.out.println(bd.divide(bd2,25,BigDecimal.ROUND_HALF_UP));</p>
<p>//194051.5567597000000000000000000</p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
