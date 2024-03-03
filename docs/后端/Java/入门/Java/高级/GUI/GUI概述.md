---
title: GUI概述
updated: 2020-09-21T17:43:01.0000000+08:00
created: 2020-09-20T10:06:14.0000000+08:00
---

## 一、基本概念
1，GUI(图形用户界面)
Graphical User Interface(图形用户接口)。
用图形的方式，来显示计算机操作的界面，这样更方便更直 观。

Java为GUI提供的对象都存在**java.Awt和javax.Swing**两个包中。

2，Awt与Swing
| java.Awt    | Abstract Window ToolKit (抽象窗口 工具包 )，需要调用本地系统方法实现功能。属 重量级控件。                     |
|-------------|---------------------------------------------------------------------------------------------------------------|
| javax.Swing | 在AWT的基础上，建立的一套图 形界面系统，其中提供了更多的组件，而且完全 由Java实现。增强了移植性，属轻量级控件 |
3，
![image1](../../../assets/f7ee5db9c12b47229c1b0d58ccc546a2.png)

## 二，建立窗体
### 1，创建图形化界面
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>1，创建frame窗体。</strong></p>
<p><strong>2，对窗体进行基本设置。</strong></p>
<blockquote>
<p><strong>比如大小，位置，布局。</strong></p>
</blockquote>
<p><strong>3，定义组件。</strong></p>
<p><strong>4，将组件通过窗体的add方法添加到窗体中。</strong></p>
<p><strong>5，让窗体显示，通过setVisible(true)</strong></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
###  2，基本套路
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>1，定义Frame,组件</strong></p>
<p><strong>2，在构造函数中调用初始化Frame的方法</strong></p>
<p><strong>3，在初始化函数中new出组件，</strong></p>
<blockquote>
<p><strong>进行位置，大小，形式的设定</strong></p>
<p><strong>加入到frame中</strong></p>
<p><strong>调用事件</strong></p>
<p><strong>设置成可见</strong></p>
</blockquote>
<p><strong>4，事件设置</strong></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

### 3，布局
| FlowLayout（流式布局管理器）      | •从左到右的顺序排列。                        |
|-----------------------------------|----------------------------------------------|
| Panel默认的布局管理器。           |                                             |
| BorderLayout（边界布局管理器）    | •东，南，西，北，中 •Frame默认的布局管理器。 |
| GridLayout（网格布局管理器）      | •规则的矩阵                                  |
| CardLayout（卡片布局管理器）      | •选项卡                                      |
| GridBagLayout（网格包布局管理器） | •非规则的矩阵                                |

## 二、事件监听机制的特点
![image2](../../../assets/1be8281e55e1442595d5a73933c39be0.png)

1，事件源：就是awt包或者swing包中的那些图形界面组件。
2，事件：每一个事件源都有自己特有的对应事件和共性事件。
3，监听器：将可以触发某一个事件的动作（不只一个动作）都已经封装到了监听器中。
以上三者，在java中都已经定义好了。
直接获取其对象来用就可以了。
要做的事情是，就是对产生的动作进行处理。

## 三、演示
1，
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>package GUITest;</strong></p>
<p></p>
<p><strong>import java.awt.Button;</strong></p>
<p><strong>import java.awt.FlowLayout;</strong></p>
<p><strong>import java.awt.Frame;</strong></p>
<p><strong>import java.awt.event.WindowAdapter;</strong></p>
<p><strong>import java.awt.event.WindowEvent;</strong></p>
<p></p>
<p><strong>import org.junit.Test;</strong></p>
<p></p>
<p><strong>//创建图形化界面：</strong></p>
<p><strong>public class AwtDemo {</strong></p>
<p><strong>public static void main(String[] args) {</strong></p>
<p><strong>//1，创建frame窗体。</strong></p>
<p><strong>Frame f=new Frame("my awt");</strong></p>
<p><strong>//2，对窗体进行基本设置。</strong></p>
<p><strong>//f.setSize(500,400);//设置窗口大小</strong></p>
<p><strong>//f.setLocation(300,200);//设置打开的位置，左顶点的距离</strong></p>
<p><strong>f.setBounds(300, 200, 500, 400);//位置，大小</strong></p>
<p><strong>f.setLayout(new FlowLayout());//设定形式</strong></p>
<p><strong>//3，定义组件。</strong></p>
<p><strong>Button b=new Button("我是按钮");</strong></p>
<p><strong>//4，将组件通过窗体的add方法添加到窗体中。</strong></p>
<p><strong>f.add(b);</strong></p>
<p><strong>f.addWindowListener(new WindowAdapter() {</strong></p>
<p><strong>public void windowClosing(WindowEvent e) {</strong></p>
<p><strong>System.out.println("关闭");</strong></p>
<p><strong>System.exit(0);</strong></p>
<p><strong>}</strong></p>
<p><strong>public void windowActivated(WindowEvent e) {</strong></p>
<p><strong>System.out.println("我活了");</strong></p>
<p><strong>}</strong></p>
<p><strong></strong></p>
<p><strong> public void windowOpened(WindowEvent e) {</strong></p>
<p><strong> System.out.println("被打开了");</strong></p>
<p><strong> }</strong></p>
<p><strong>});</strong></p>
<p><strong>//5，让窗体显示，通过setVisible(true)</strong></p>
<p><strong>f.setVisible(true);</strong></p>
<p><strong>}</strong></p>
<p></p>
<p><strong>}</strong></p>
<p><strong>//因为WindowListener的子类WindowAdapter已经实现了WindowListener接口。</strong></p>
<p><strong>//并覆盖了其中的所有方法。那么我只要继承自Windowadapter覆盖我需要的方法即可。</strong></p>
<p><strong>//class MyWin extends WindowAdapter</strong></p>
<p><strong>//{</strong></p>
<p><strong>//public void windowClosing(WindowEvent e)</strong></p>
<p><strong>//{</strong></p>
<p><strong>////System.out.println("window closing---"+e.toString());</strong></p>
<p><strong>//System.exit(0);</strong></p>
<p><strong>//}</strong></p>
<p><strong>//}</strong></p>
<p></p>
<p></p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

,2，
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>package GUITest;</strong></p>
<p></p>
<p><strong>import java.awt.Button;</strong></p>
<p><strong>import java.awt.FlowLayout;</strong></p>
<p><strong>import java.awt.Frame;</strong></p>
<p><strong>import java.awt.event.ActionEvent;</strong></p>
<p><strong>import java.awt.event.ActionListener;</strong></p>
<p><strong>import java.awt.event.WindowAdapter;</strong></p>
<p><strong>import java.awt.event.WindowEvent;</strong></p>
<p></p>
<p><strong>public class FrameDemo {</strong></p>
<p><strong>private Frame f;</strong></p>
<p><strong>private Button but;</strong></p>
<p><strong>FrameDemo(){</strong></p>
<p><strong>init();</strong></p>
<p><strong>}</strong></p>
<p><strong>public void init() {</strong></p>
<p><strong>f=new Frame("my frame");</strong></p>
<p><strong></strong></p>
<p><strong>//对窗口进行基本设置</strong></p>
<p><strong>f.setBounds(300, 200, 600, 500);</strong></p>
<p><strong>f.setLayout(new FlowLayout());</strong></p>
<p><strong>//添加组件</strong></p>
<p><strong>but=new Button("my button");</strong></p>
<p><strong>f.add(but);</strong></p>
<p><strong>myEvent();</strong></p>
<p><strong>f.setVisible(true);</strong></p>
<p><strong>}</strong></p>
<p><strong>private void myEvent() {</strong></p>
<p><strong>f.addWindowListener(new WindowAdapter() {</strong></p>
<p><strong></strong></p>
<p><strong>public void windowClosing(WindowEvent e) {</strong></p>
<p><strong>System.exit(0);</strong></p>
<p><strong>}</strong></p>
<p><strong></strong></p>
<p><strong>});</strong></p>
<p><strong>//让按钮具备退出程序的功能</strong></p>
<p><strong>/**</strong></p>
<p><strong> * 按钮就是事件源。</strong></p>
<p><strong>那么选择哪个监听器呢？</strong></p>
<p><strong>通过关闭窗体示例了解到，想要知道哪个组件具备什么样的特有监听器。</strong></p>
<p><strong>需要查看该组件对象的功能。</strong></p>
<p><strong> 通过查阅button的描述。发现按钮支持一个特有监听addActionListener。</strong></p>
<p><strong> * @param args</strong></p>
<p><strong> */</strong></p>
<p><strong></strong></p>
<p><strong>but.addActionListener(new ActionListener() {</strong></p>
<p><strong>private int count = 1;</strong></p>
<p><strong>@Override</strong></p>
<p><strong>public void actionPerformed(ActionEvent e) {</strong></p>
<p><strong>System.exit(0);</strong></p>
<p><strong>//Button b = (Button)e.getSource();</strong></p>
<p><strong>//</strong></p>
<p><strong>//Frame f1 = (Frame)b.getParent();</strong></p>
<p><strong>//</strong></p>
<p><strong>//f1.add(new Button("button-"+count++));</strong></p>
<p><strong>//f1.validate();</strong></p>
<p><strong></strong></p>
<p><strong>}</strong></p>
<p><strong>});</strong></p>
<p><strong>}</strong></p>
<p></p>
<p><strong></strong></p>
<p><strong></strong></p>
<p></p>
<p><strong></strong></p>
<p><strong>public static void main(String[] args) {</strong></p>
<p><strong>// TODO Auto-generated method stub</strong></p>
<p><strong>new FrameDemo();</strong></p>
<p><strong>}</strong></p>
<p></p>
<p><strong>}</strong></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
**基本逻辑**
**1，定义Frame,组件**
**2，在构造函数中调用初始化Frame的方法**
**3，在初始化函数中进行位置，大小，形式的设定**
**加入到frame中**
**调用事件**
**设置成可见**
**4，事件设置**
