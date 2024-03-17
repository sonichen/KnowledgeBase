---
title: CSS的复合选择器
updated: 2020-11-07T20:13:43.0000000+08:00
created: 2020-06-18T17:40:44.0000000+08:00
---

# CSS的复合选择器
复合选择器建立在基础选择器之上，对基本选择器进行组合形成

![image1](../../assets/e4919f2de16242ceb3fe115bbf3f1ac7.png)
<table>
<colgroup>
<col style="width: 17%" />
<col style="width: 21%" />
<col style="width: 19%" />
<col style="width: 10%" />
<col style="width: 29%" />
</colgroup>
<thead>
<tr class="header">
<th>选择器</th>
<th>作用</th>
<th>特征</th>
<th>隔开符号</th>
<th>用法</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>后代选择器</td>
<td>用来选择后代元素</td>
<td>可以选择低于这一级别的</td>
<td>空格</td>
<td>.nav a{}</td>
</tr>
<tr class="even">
<td>子代选择器</td>
<td>选择最近一级元素</td>
<td>只选择下一级别</td>
<td>大于</td>
<td>.nav&gt;p{}</td>
</tr>
<tr class="odd">
<td>并集选择器</td>
<td>选择某些相同样式的元素</td>
<td>可以用于集体声明</td>
<td>逗号</td>
<td>.nav,.header{}</td>
</tr>
<tr class="even">
<td>链接伪类选择器</td>
<td>选择不同状态的链接</td>
<td>和链接相关</td>
<td></td>
<td><p>a{}</p>
<p>a:hover</p></td>
</tr>
<tr class="odd">
<td>:focus选择器</td>
<td>选择获得光标的表单</td>
<td>和表单相关</td>
<td></td>
<td>Input:focus</td>
</tr>
</tbody>
</table>

## 
## 一、后代选择器（包含选择器）
元素1 元素2 {样式声明；}

对元素2操作
选择元素1里面的所有元素2（后代元素）
注意：
1，元素1和元素2 空格分开
2，元素1父级，元素2子集，最终选择的是元素2
3，元素2只要是元素1后代即可
4，元素1，元素2可以是任意基础选择器

![image2](../../assets/efc78a8902254cfbaf12d579b4dd67ec.png)
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>&lt;head&gt;</p>
<p>&lt;style&gt;</p>
<p>/* 我想要把ol里面的小li选出来改为pink */</p>
<p></p>
<p>ol li {</p>
<p>color: pink;</p>
<p>}</p>
<p></p>
<p>/* 中国 山东 济南 蓝翔 */</p>
<p>ol li a {</p>
<p>color: red;</p>
<p>}</p>
<p></p>
<p>.nav li a {</p>
<p>color: yellow;</p>
<p>}</p>
<p>&lt;/style&gt;</p>
<p>&lt;/head&gt;</p>
<p></p>
<p>&lt;body&gt;</p>
<p>&lt;ol&gt;</p>
<p>变态写法</p>
<p>&lt;li&gt;我是ol 的孩子&lt;/li&gt;</p>
<p>&lt;li&gt;我是ol 的孩子&lt;/li&gt;</p>
<p>&lt;li&gt;我是ol 的孩子&lt;/li&gt;</p>
<p>&lt;li&gt;&lt;a href="#"&gt;我是孙子&lt;/a&gt;&lt;/li&gt;</p>
<p>&lt;/ol&gt;</p>
<p>&lt;ul&gt;</p>
<p>&lt;li&gt;我是ul 的孩子&lt;/li&gt;</p>
<p>&lt;li&gt;我是ul 的孩子&lt;/li&gt;</p>
<p>&lt;li&gt;我是ul 的孩子&lt;/li&gt;</p>
<p>&lt;li&gt;&lt;a href="#"&gt;不会变化的&lt;/a&gt;&lt;/li&gt;</p>
<p>&lt;/ul&gt;</p>
<p>&lt;ul class="nav"&gt;</p>
<p>&lt;li&gt;我是ul 的孩子&lt;/li&gt;</p>
<p>&lt;li&gt;我是ul 的孩子&lt;/li&gt;</p>
<p>&lt;li&gt;我是ul 的孩子&lt;/li&gt;</p>
<p>&lt;li&gt;&lt;a href="#"&gt;不会变化的&lt;/a&gt;&lt;/li&gt;</p>
<p>&lt;li&gt;&lt;a href="#"&gt;不会变化的&lt;/a&gt;&lt;/li&gt;</p>
<p>&lt;li&gt;&lt;a href="#"&gt;不会变化的&lt;/a&gt;&lt;/li&gt;</p>
<p>&lt;li&gt;&lt;a href="#"&gt;不会变化的&lt;/a&gt;&lt;/li&gt;</p>
<p>&lt;/ul&gt;</p>
<p>&lt;\body&gt;</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
## 二．子代选择器
元素1 \> 元素2 {样式声明；}

元素2是元素1的直接后代，选择最近一级的子元素
Eg。div\>p{样式声明}
注意
1，元素1和元素2中间大于号隔开
2，元素1父级，元素2子集，最终选择元素2
## 三、并集选择器
元素1，元素2{样式声明；}

可以选择多组标签，同时为他们定义相同样式，集体声明
![image3](../../assets/52b2fa8bb6db4f4eb28971ee6657eba3.png)
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p></p>
<p>&lt;head&gt;</p>
<p>….</p>
<p>&lt;style&gt;</p>
<p>/* 要求: 请把熊大和熊二改为粉色 还有 小猪一家改为粉色 */</p>
<p>div,</p>
<p>p,</p>
<p>.pig li {</p>
<p>color: pink;</p>
<p>}</p>
<p>&lt;/style&gt;</p>
<p>&lt;/head&gt;</p>
<p></p>
<p>&lt;body&gt;</p>
<p>&lt;div&gt;熊大&lt;/div&gt;</p>
<p>&lt;p&gt;熊二&lt;/p&gt;</p>
<p>&lt;span&gt;光头强&lt;/span&gt;</p>
<p>&lt;ul class="pig"&gt;</p>
<p>&lt;li&gt;小猪佩奇&lt;/li&gt;</p>
<p>&lt;li&gt;猪爸爸&lt;/li&gt;</p>
<p>&lt;li&gt;猪妈妈&lt;/li&gt;</p>
<p>&lt;/ul&gt;</p>
<p>&lt;/body&gt;</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

注意
1，约定的语法规范,我们并集选择器喜欢竖着写
2，一定要注意,最后一个选择器 不需要加逗号

## 四、伪类选择器
用于给某类选择器添加特殊效果
==最大特点是用冒号表示==
有很多种，重点看链接伪类、结构伪类
### 1、链接伪类选择器
| a:link    | 选择所有未被访问的链接               |
|-----------|--------------------------------------|
| a:visited | 选择所有已被访问的链接               |
| a: hover  | 选择鼠标指针位于其上的链接           |
| a: active | 选择活动链接（鼠标按下未弹起的链接） |

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>/* 1.未访问的链接 a:link 把没有点击过的(访问过的)链接选出来 */</p>
<p>a:link {</p>
<p>color: #333;</p>
<p>text-decoration: none;</p>
<p>}</p>
<p></p>
<p>/*2. a:visited 选择点击过的(访问过的)链接 */</p>
<p>a:visited {</p>
<p>color: orange;</p>
<p>}</p>
<p></p>
<p>/*3. a:hover 选择鼠标经过的那个链接 */</p>
<p>a:hover {</p>
<p>color: skyblue;</p>
<p>}</p>
<p></p>
<p>/* 4. a:active 选择的是我们鼠标正在按下还没有弹起鼠标的那个链接 */</p>
<p>a:active {</p>
<p>color: green;</p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

注意
==1：严格按照LVHA顺序书写 link-visited-hover-active==
2给链接指定样式要单独指定
3.实际开发写法
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>&lt;style&gt;</p>
<p>a {</p>
<p>color: #333;</p>
<p>text-decoration: none;</p>
<p>}</p>
<p></p>
<p>a:hover {</p>
<p>color: #369;</p>
<p>text-decoration: underline;</p>
<p>}</p>
<p>&lt;/style&gt;</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
### 2.：focus伪类选择器
用于获取获得焦点的的表单元素
焦点就是光标，一般情况\<input\>类表单元素才能获取，因此这个选择器也主要针对表单元素来说
![image4](../../assets/1e2cb4faee0f41b8816c00e09e3e2c52.png)
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>&lt;head&gt;</p>
<p>...</p>
<p>&lt;title&gt;focus伪类选择器&lt;/title&gt;</p>
<p>&lt;style&gt;</p>
<p>/* // 把获得光标的input表单元素选取出来 */</p>
<p>input:focus {</p>
<p>background-color: pink;</p>
<p>color: red;</p>
<p>}</p>
<p>&lt;/style&gt;</p>
<p>&lt;/head&gt;</p>
<p></p>
<p>&lt;body&gt;</p>
<p>&lt;input type="text"&gt;</p>
<p>&lt;input type="text"&gt;</p>
<p>&lt;input type="text"&gt;</p>
<p>&lt;/body&gt;</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
## 五、总结
<table>
<colgroup>
<col style="width: 17%" />
<col style="width: 21%" />
<col style="width: 19%" />
<col style="width: 10%" />
<col style="width: 29%" />
</colgroup>
<thead>
<tr class="header">
<th>选择器</th>
<th>作用</th>
<th>特征</th>
<th>隔开符号</th>
<th>用法</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>后代选择器</td>
<td>用来选择后代元素</td>
<td>可以选择低于这一级别的</td>
<td>空格</td>
<td>.nav a{}</td>
</tr>
<tr class="even">
<td>子代选择器</td>
<td>选择最近一级元素</td>
<td>只选择下一级别</td>
<td>大于</td>
<td>.nav&gt;p{}</td>
</tr>
<tr class="odd">
<td>并集选择器</td>
<td>选择某些相同样式的元素</td>
<td>可以用于集体声明</td>
<td>逗号</td>
<td>.nav,.header{}</td>
</tr>
<tr class="even">
<td>链接伪类选择器</td>
<td>选择不同状态的链接</td>
<td>和链接相关</td>
<td></td>
<td><p>a{}</p>
<p>a:hover</p></td>
</tr>
<tr class="odd">
<td>:focus选择器</td>
<td>选择获得光标的表单</td>
<td>和表单相关</td>
<td></td>
<td>Input:focus</td>
</tr>
</tbody>
</table>
