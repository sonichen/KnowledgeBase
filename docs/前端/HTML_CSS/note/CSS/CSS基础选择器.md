---
title: CSS基础选择器
updated: 2020-11-07T19:54:40.0000000+08:00
created: 2020-06-18T17:38:47.0000000+08:00
---

# CSS基础选择器
![image1](../../assets/fffcb5998a734ea292950c829b0b8aef.png)
## 一、基础选择器
**基础选择器—单个选择器构成**
### 1.、标签选择器
把HTML标签名作为选择器，制定统一格式

标签名 {

属性1 ：属性值1；

属性2 ： 属性值2；

……

}

快速把页面里同类型一起设置，但是不能分别改同类中的某个地方
### 2.类选择器
利用class属性来调用

差异化设置

. 类名{

属性1： 属性值1；

属性2： 属性值2;

......

}

口诀：样式点定义，结构类调用，一个或多个，开发最常用

案例：

![image2](../../assets/23a1bbe541304d8394b00e2eba9890e5.png)
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>&lt;head&gt;</p>
<p>...</p>
<p>&lt;style&gt;</p>
<p>.red {</p>
<p>color: red;</p>
<p>}</p>
<p>&lt;/style&gt;</p>
<p>&lt;/head&gt;</p>
<p>&lt;body&gt;</p>
<p>&lt;ul&gt;</p>
<p>&lt;li class="red"&gt;冰雨&lt;/li&gt;</p>
<p>&lt;li&gt;来生缘&lt;/li&gt;</p>
<p>&lt;li&gt;生僻字&lt;/li&gt;</p>
<p>&lt;/ul&gt;</p>
<p>&lt;/body&gt;</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
注意
1.  类名自己定义，标签名字不能做类名
2.  长名字用-连接
3.  不要用纯数字、中文命名，尽量英文
4.  命名规范

案例

![image3](../../assets/9594940d1afd489c854a46f06314ccfa.png)
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>&lt;head&gt;</p>
<p>......</p>
<p>&lt;style&gt;</p>
<p>.box {</p>
<p>width: 100px;</p>
<p>height: 100px;</p>
<p>}</p>
<p></p>
<p>.red {</p>
<p>background-color: red;</p>
<p>}</p>
<p></p>
<p>.green {</p>
<p>background-color: green;</p>
<p>}</p>
<p>&lt;/style&gt;</p>
<p>&lt;/head&gt;</p>
<p>&lt;body&gt;</p>
<p>&lt;div class="red box"&gt;红色&lt;/div&gt;</p>
<p>&lt;div class="green box"&gt;绿色&lt;/div&gt;</p>
<p>&lt;div class="red box"&gt;红色&lt;/div&gt;</p>
<p>&lt;/body&gt;</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
多类名：达到更多选择的目的：一个标签多个类名，多个类名必须用空格分开
### 3.id选择器
可以为标有特定id的HTML元素指定特定样式

HTML元素以id属性来设置id选择器,CSS中 id 选择器以”#”来定义

语法
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>#id {</p>
<p>属性1： 属性值1；</p>
<p>…</p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

==样式#定义，结构id调用,只能调用一次，别人切勿使用==

用于页面上为一线元素

与类选择器区别：**类选择器多次使用，id选择器一次使用**

案例

![image4](../../assets/53db743743af44f19fe211c0e07f0b9f.png)
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>&lt;head&gt;</p>
<p>...</p>
<p>&lt;style&gt;</p>
<p>#yes {</p>
<p>color: pink;</p>
<p>}</p>
<p>&lt;/style&gt;</p>
<p>&lt;/head&gt;</p>
<p>&lt;body&gt;</p>
<p>&lt;div id="yes"&gt;我帅气&lt;/div&gt;</p>
<p>&lt;/body&gt;</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
### 4、通配符选择器
使用“\*”定义，选取页面里所有元素，不需要调用，自动给所有

格式
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>*{</p>
<p>操作；</p>
<p>}</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
## 5、总结
| 基础选择器   | 作用                   | 特点                               | 使用情况     | 用法                 |
|--------------|------------------------|------------------------------------|--------------|----------------------|
| 标签选择器   | 可以选出所有相同的标签 | 不能差异化选择                     | 较多         | p { color: red; }    |
| 类选择器     | 可以选出一个或多个标签 | 可以根据需求选择                   | 非常多       | .nav { color: red; } |
| id选择器     | 一次只能选择1个标签    | ID属性只能在每个HTML文档中出现一次 | 一般和js搭配 | \#nav { color: red;} |
| 通配符选择器 | 选择所有的标签         | 选择的太多，有部分不需要           | 特殊情况使用 | \*{ color: red;}     |
