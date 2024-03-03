---
title: String练习
updated: 2020-09-08T21:35:34.0000000+08:00
created: 2020-09-06T16:21:42.0000000+08:00
---

1，
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>package StringEver;</p>
<p>/*</p>
<p>模拟一个trim方法，去除字符串两端的空格。</p>
<p></p>
<p>*/</p>
<p>public class Ever1 {</p>
<p>public static void main(String[] args) {</p>
<p>String str=new String(" 765 67 ");</p>
<p>System.out.println(str);// 765 67</p>
<p>System.out.println(TrimTest(str));//765 67</p>
<p>}</p>
<p>public static String TrimTest(String str){</p>
<p>int start=0;// 用于记录从前往后首次索引位置不是空格的位置的索引</p>
<p>int end=str.length()-1;// 用于记录从后往前首次索引位置不是空格的位置的索引</p>
<p>while(start&lt;end&amp;&amp;str.charAt(start)==' '){</p>
<p>start++;</p>
<p>}</p>
<p>while(start&lt;end&amp;&amp;str.charAt(end)==' '){</p>
<p>end--;</p>
<p>}</p>
<p>if(str.charAt(start)==' '){</p>
<p>return "";</p>
<p>}</p>
<p>str=str.substring(start,end+1);</p>
<p>return str;</p>
<p>}</p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

2，
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>package StringEver;</p>
<p></p>
<p>/**</p>
<p>* 将一个字符串进行反转。将字符串中指定部分进行反转。比如“abcdefg”反 转为”abfedcg”</p>
<p>*/</p>
<p>public class Ever2 {</p>
<p>public static String reverse1(String str,int startIndex,int endIndex){</p>
<p>if(str!=null&amp;&amp;startIndex&lt;endIndex){</p>
<p></p>
<p>char []arr=str.toCharArray();</p>
<p></p>
<p>for(int i=startIndex,j=endIndex;i&lt;j;i++,j--){</p>
<p>char temp=arr[i];</p>
<p>arr[i]=arr[j];</p>
<p>arr[j]=temp;</p>
<p>}</p>
<p></p>
<p>return new String(arr);</p>
<p>}else{</p>
<p>return null;</p>
<p>}</p>
<p>}</p>
<p>public static String reverse2(String str,int startIndex,int endIndex){</p>
<p>if(str!=null&amp;&amp;startIndex&lt;endIndex){</p>
<p>String newStr=str.substring(0,startIndex);</p>
<p>for (int i=endIndex;i&gt;=startIndex;i--){</p>
<p>newStr+=str.charAt(i);</p>
<p>}</p>
<p>newStr+=str.substring(endIndex+1);</p>
<p>return newStr;</p>
<p>}else{</p>
<p>return null;</p>
<p>}</p>
<p>}</p>
<p>public static String reverse3(String str,int startIndex,int endIndex){</p>
<p>StringBuilder s=new StringBuilder();</p>
<p>s.append(str.substring(0,startIndex));</p>
<p>for(int i=endIndex;i&gt;=startIndex;i--) {</p>
<p>s.append(str.charAt(i));</p>
<p>}</p>
<p>s.append(str.substring(endIndex+1));</p>
<p>return s.toString();</p>
<p>}</p>
<p>public static void main(String[] args) {</p>
<p>String str1=reverse1("abcdefg",2,5);</p>
<p>System.out.println(str1);</p>
<p></p>
<p>String str2=reverse2("abcdefg",2,5);</p>
<p>System.out.println(str2);</p>
<p></p>
<p>String str3=reverse3("abcdefg",2,5);</p>
<p>System.out.println(str3);</p>
<p>}</p>
<p>}</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

3
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>package StringEver;</p>
<p></p>
<p>/**</p>
<p>* 获取一个字符串在另一个字符串中出现的次数。 比如：获取“ ab”在 “abkkcadkabkebfkabkskab” 中出现的次数</p>
<p>*/</p>
<p>public class Ever3 {</p>
<p>public static int Count(String str, String subStr){</p>
<p>if(str.length()&gt;=subStr.length()){</p>
<p>int index=0;</p>
<p>int count=0;</p>
<p>while((index= str.indexOf(subStr,index))!=-1){</p>
<p>index+=subStr.length();</p>
<p>count++;</p>
<p>}</p>
<p>return count;</p>
<p>}</p>
<p>return 0;</p>
<p>}</p>
<p></p>
<p>public static void main(String[] args) {</p>
<p>System.out.println(Count("abkkcadkabkebfkabkskab","ab"));//4</p>
<p>}</p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

4，
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>package StringEver;</p>
<p></p>
<p>/**</p>
<p>* 获取两个字符串中最大相同子串。比如： str1 = "abcwerthelloyuiodef“;str2 = "cvhellobnm"</p>
<p>* 提示：将短的那个串进行长度依次递减的子串与较长的串比较。</p>
<p>*/</p>
<p>public class Ever4 {</p>
<p>public static void main(String[] args) {</p>
<p>System.out.println(CompareTest("abcwerthelloyuiodef","cvhellobnm"));//hello</p>
<p>}</p>
<p>public static String CompareTest(String str1, String str2){</p>
<p>if(str1!=null&amp;&amp;str2!=null){</p>
<p>String maxStr=(str1.length()&gt;=str2.length())? str1:str2;</p>
<p>String minStr=(str1.length()&lt;str2.length())? str1:str2;</p>
<p>int length=minStr.length();</p>
<p>for(int i=0;i&lt;length;i++){// 0 1 2 3 4 此层循环决定要去几个字符</p>
<p>for(int x=0,y=length-i;y&lt;length;x++,y++){</p>
<p>if(maxStr.contains(minStr.substring(x,y))){</p>
<p>return minStr.substring(x,y);</p>
<p>}</p>
<p>}</p>
<p>}</p>
<p>}</p>
<p>return null;</p>
<p></p>
<p>}</p>
<p>// 如果存在多个长度相同的最大相同子串</p>
<p>// 此时先返回String[]，后面可以用集合中的ArrayList替换，较方便</p>
<p>public String[] getMaxSameSubString1(String str1, String str2) {</p>
<p>if (str1 != null &amp;&amp; str2 != null) {</p>
<p>StringBuffer sBuffer = new StringBuffer();</p>
<p>String maxString = (str1.length() &gt; str2.length()) ? str1 : str2;</p>
<p>String minString = (str1.length() &gt; str2.length()) ? str2 : str1;</p>
<p></p>
<p>int len = minString.length();</p>
<p>for (int i = 0; i &lt; len; i++) {</p>
<p>for (int x = 0, y = len - i; y &lt;= len; x++, y++) {</p>
<p>String subString = minString.substring(x, y);</p>
<p>if (maxString.contains(subString)) {</p>
<p>sBuffer.append(subString + ",");</p>
<p>}</p>
<p>}</p>
<p>System.out.println(sBuffer);</p>
<p>if (sBuffer.length() != 0) {</p>
<p>break;</p>
<p>}</p>
<p>}</p>
<p>String[] split = sBuffer.toString().replaceAll(",$", "").split("\\,");</p>
<p>return split;</p>
<p>}</p>
<p></p>
<p>return null;</p>
<p>}</p>
<p>// 如果存在多个长度相同的最大相同子串：使用ArrayList</p>
<p>//public List&lt;String&gt; getMaxSameSubString1(String str1, String str2) {</p>
<p>//if (str1 != null &amp;&amp; str2 != null) {</p>
<p>//List&lt;String&gt; list = new ArrayList&lt;String&gt;();</p>
<p>//String maxString = (str1.length() &gt; str2.length()) ? str1 : str2;</p>
<p>//String minString = (str1.length() &gt; str2.length()) ? str2 : str1;</p>
<p>//</p>
<p>//int len = minString.length();</p>
<p>//for (int i = 0; i &lt; len; i++) {</p>
<p>//for (int x = 0, y = len - i; y &lt;= len; x++, y++) {</p>
<p>//String subString = minString.substring(x, y);</p>
<p>//if (maxString.contains(subString)) {</p>
<p>//list.add(subString);</p>
<p>//}</p>
<p>//}</p>
<p>//if (list.size() != 0) {</p>
<p>//break;</p>
<p>//}</p>
<p>//}</p>
<p>//return list;</p>
<p>//}</p>
<p>//</p>
<p>//return null;</p>
<p>//}</p>
<p>}</p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

5，
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>package StringEver;</p>
<p></p>
<p>import java.util.Arrays;</p>
<p></p>
<p>/**</p>
<p>* 对字符串中字符进行自然顺序排序。</p>
<p>* 提示：</p>
<p>* 1）字符串变成字符数组。</p>
<p>* 2）对数组排序，选择，冒泡，Arrays.sort();</p>
<p>* 3）将排序后的数组变成字符串。</p>
<p>*/</p>
<p>public class Ever5 {</p>
<p>public static String sort(String str){</p>
<p>char [] arr=str.toCharArray();</p>
<p>Arrays.sort(arr);</p>
<p>String newStr=new String(arr);</p>
<p>return new String(newStr);</p>
<p>}</p>
<p></p>
<p>public static void main(String[] args) {</p>
<p>String str=sort("Hello");</p>
<p>System.out.println(str);</p>
<p>}</p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
