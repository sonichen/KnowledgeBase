---
title: 20-State Pattern
updated: 2024-01-29T13:00:33.0000000+08:00
created: 2021-12-07T16:58:57.0000000+08:00
---

## 1，定义
<table>
<colgroup>
<col style="width: 10%" />
<col style="width: 89%" />
</colgroup>
<thead>
<tr class="header">
<th>官方的</th>
<th>当一个对象的内在状态改变时允许改变其行为，这个对象看起来像是改变了其类</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>通俗的</td>
<td><p>当遇到<strong>不同的状态遇到不同的行为</strong>的时候，可以使用状态模式</p>
<p></p>
<p>不用写if,else，swith语句，</p>
<p>可以实现复杂的程序状态迁移</p>
<p>我们创建表示各种状态的对象和一个行为随着状态对象改变而改变的 context 对象。</p>
<p></p></td>
</tr>
</tbody>
</table>
## 2，各类含义，UML
State（抽象状态类）：定义一个接口以封装与Context的一个特定状态相关的行为。
ConcreteStateA，B，C（具体状态）：每一个子类实现一个不同的状态或行为
Context（上下文）：维护一个State子类状态的实例，这个实例中定义了当前的状态。

![image1](../../assets/ecd9870c32e44d148b475ecc2e0ad146.jpg)

## 3，代码
![image2](../../assets/a17cf44045d84b3c9dc743063e58b758.png)

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>interface PossibleState</p>
<p>{</p>
<p>void pressOnButton(TV context);</p>
<p>void pressOffButton(TV context);</p>
<p>void pressMuteButton(TV context);</p>
<p>}</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>package learn.book.state;</p>
<p></p>
<p>//On state</p>
<p>class On implements PossibleState</p>
<p>{</p>
<p>//TV is On already, user is pressing On button again</p>
<p>@Override</p>
<p>public void pressOnButton(TV context)</p>
<p>{</p>
<p>System.out.println("You pressed On button. TV is already in On state.");</p>
<p>}</p>
<p>//User is pressing Off button when the TV is in On state</p>
<p>@Override</p>
<p>public void pressOffButton(TV context)</p>
<p>{</p>
<p>System.out.println("You pressed Off button.Going from On to Off state.");</p>
<p>context.setCurrentState(new Off());</p>
<p>System.out.println(context.getCurrentState().toString());</p>
<p>}</p>
<p>//User is pressing Mute button when the TV is in On state</p>
<p>@Override</p>
<p>public void pressMuteButton(TV context)</p>
<p>{</p>
<p>System.out.println("You pressed Mute button.Going from On to Mute mode.");</p>
<p>context.setCurrentState(new Mute());</p>
<p>System.out.println(context.getCurrentState().toString());</p>
<p>}</p>
<p>public String toString()</p>
<p>{</p>
<p>return "\t**TV is switched on now.**";</p>
<p>} }</p></th>
<th><p>package learn.book.state;</p>
<p>class Off implements PossibleState</p>
<p>{</p>
<p>//User is pressing Off button when the TV is in Off state</p>
<p>@Override</p>
<p>public void pressOnButton(TV context)</p>
<p>{</p>
<p>System.out.println("You pressed On button. Going from Off to On state.");</p>
<p>context.setCurrentState(new On());</p>
<p>System.out.println(context.getCurrentState().toString());</p>
<p>}</p>
<p>//TV is Off already, user is pressing Off button again</p>
<p>@Override</p>
<p>public void pressOffButton(TV context)</p>
<p>{</p>
<p>System.out.println("You pressed Off button. TV is already in Off state.");</p>
<p>}</p>
<p>//User is pressing Mute button when the TV is in Off state</p>
<p>@Override</p>
<p>public void pressMuteButton(TV context)</p>
<p>{</p>
<p>System.out.println("You pressed Mute button.TV is already in Off state, so Mute operation will not work.");</p>
<p>}</p>
<p>public String toString()</p>
<p>{</p>
<p>return "\t**TV is switched off now.**";</p>
<p>} }</p></th>
<th><p>package learn.book.state;</p>
<p></p>
<p>//Mute state</p>
<p>class Mute implements PossibleState</p>
<p>{</p>
<p>//User is pressing On button when the TV is in Mute mode</p>
<p>@Override</p>
<p>public void pressOnButton(TV context)</p>
<p>{</p>
<p>System.out.println("You pressed On button.Going from Mute mode to On state.");</p>
<p>context.setCurrentState(new On());</p>
<p>System.out.println(context.getCurrentState().toString());</p>
<p>}</p>
<p>//User is pressing Off button when the TV is in Mute mode</p>
<p>@Override</p>
<p>public void pressOffButton(TV context)</p>
<p>{</p>
<p>System.out.println("You pressed Off button. Going from Mute mode to Off state.");</p>
<p>context.setCurrentState(new Off());</p>
<p>System.out.println(context.getCurrentState().toString());</p>
<p>}</p>
<p>//TV is in mute mode already, user is pressing mute button again</p>
<p>@Override</p>
<p>public void pressMuteButton(TV context)</p>
<p>{</p>
<p>System.out.println("You pressed Mute button.TV is already in Mute mode.");</p>
<p>}</p>
<p>public String toString()</p>
<p>{</p>
<p>return "\t**TV is silent(mute) now**";</p>
<p>} }</p></th>
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
<th><p>package learn.book.state;</p>
<p></p>
<p>class TV</p>
<p>{</p>
<p>private PossibleState currentState;</p>
<p>public TV()</p>
<p>{</p>
<p>//Initially TV is initialized with Off state</p>
<p>this.setCurrentState(new Off());</p>
<p>}</p>
<p>public PossibleState getCurrentState()</p>
<p>{</p>
<p>return currentState;</p>
<p>}</p>
<p>public void setCurrentState(PossibleState currentState)</p>
<p>{</p>
<p>this.currentState = currentState;</p>
<p>}</p>
<p>public void pressOffButton()</p>
<p>{</p>
<p>currentState.pressOffButton(this);//Delegating the state</p>
<p>}</p>
<p>public void pressOnButton()</p>
<p>{</p>
<p>currentState.pressOnButton(this);//Delegating the state</p>
<p>}</p>
<p>public void pressMuteButton()</p>
<p>{</p>
<p>currentState.pressMuteButton(this);//Delegating the state</p>
<p>} }</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

![image3](../../assets/145a0a1df35d41d0943dd802a23d8ecf.png)

![image4](../../assets/94fcef2ac9044e58bd9f377c784f0521.png)

## 4，优缺点
优点：
1、封装了转换规则。
2、枚举可能的状态，在枚举状态之前需要确定状态种类。
3、将所有与某个状态有关的行为放到一个类中，并且可以方便地增加新的状态，只需要改变对象状态即可改变对象的行为。
4、允许状态转换逻辑与状态对象合成一体，而不是某一个巨  
对象的个数。

缺点：
1、状态模式的使用必然会增加系统类和对象的个数。
2、状态模式的结构与实现都较为复杂，如果使用不当将导致程序结构和代码的混乱。
3、状态模式对"开闭原则"的支持并不太好，对于可以切换状态的状态模式，增加新的状态类需要修改那些负责状态转换的源代码，否则无法切换到新增状态，而且修改某个状态类的行为也需修改对应类的源代码。

## 5，适用场景

当一个对象的行为取决于它的状态，并且它必须在运行时刻根据状态改变它的行为时，就可以考虑使用状态模式了。

开发中场景：

银行系统中账号状态的管理

OA系统中公文状态的管理

酒店系统中，房间状态的管理

线程对象各状态之间的切换
![image5](../../assets/d1875229ef3d41afb537c8712d6d70ae.png)

