---
title: JFrame
updated: 2020-09-21T17:45:13.0000000+08:00
created: 2020-09-20T15:56:31.0000000+08:00
---

继承于Frame类

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>package GUITest;</strong></p>
<p><strong>import java.awt.*;</strong></p>
<p><strong>import java.awt.event.*;</strong></p>
<p></p>
<p><strong>import javax.swing.*;</strong></p>
<p><strong>import javax.swing.event.*;</strong></p>
<p></p>
<p><strong>class SwingDemo</strong></p>
<p><strong>{</strong></p>
<p><strong>public static void main(String[] args)</strong></p>
<p><strong>{</strong></p>
<p><strong>JFrame f = new JFrame();</strong></p>
<p></p>
<p><strong>f.setBounds(300,100,500,400);</strong></p>
<p></p>
<p><strong>f.setLayout(new FlowLayout());</strong></p>
<p></p>
<p><strong>JButton but = new JButton("我是一个按钮");</strong></p>
<p></p>
<p><strong>f.add(but);</strong></p>
<p></p>
<p><strong>f.addWindowListener(new WindowAdapter()</strong></p>
<p><strong>{</strong></p>
<p><strong>public void windowClosing(WindowEvent e)</strong></p>
<p><strong>{</strong></p>
<p><strong>System.exit(0);</strong></p>
<p><strong>}</strong></p>
<p><strong>});</strong></p>
<p></p>
<p></p>
<p><strong>f.setVisible(true);</strong></p>
<p><strong>}</strong></p>
<p><strong>}</strong></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
