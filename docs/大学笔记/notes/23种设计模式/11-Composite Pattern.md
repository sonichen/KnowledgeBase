---
title: 11-Composite Pattern
updated: 2024-01-29T12:56:22.0000000+08:00
created: 2021-12-14T10:29:10.0000000+08:00
---

## 1，定义
<table>
<colgroup>
<col style="width: 9%" />
<col style="width: 90%" />
</colgroup>
<thead>
<tr class="header">
<th>官方的</th>
<th>是用于把一组相似的对象当作一个单一的对象。组合模式依据树形结构来组合对象，用来表示部分以及整体层次。这种类型的设计模式属于结构型模式，它创建了对象组的树形结构。</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>通俗的</td>
<td><p>java中的组合是指：在A类里定义一个B类的引用，A拥有了B，叫组合。</p>
<p>只是单纯的组合而已，而不是一种设计模式。</p>
<p></p>
<p>组合和组合模式不是一回事！</p>
<p></p>
<p>基本上见到的树形结构都使用到了组合模式。</p></td>
</tr>
</tbody>
</table>
## 2，各类含义，UML
![image1](../../assets/afe7db8cfd7c49abb18a8422e3521cf3.jpg)
组合模式中有几个核心的部分：

Leaf（叶子）：表示该节点下面没有其他子节点了，就称为叶子
Compostie（容器构件）：容器构件，该节点下还有其他子节点，理解为一个容器，里面包含了其他子节点。就叫做容器构件
Component（抽象构件）：抽象构件中定义了叶子和容器构件的共同点。比如，有公共的添加删除叶子功能，有显示节点功能。

## 3，代码
<table>
<colgroup>
<col style="width: 47%" />
<col style="width: 52%" />
</colgroup>
<thead>
<tr class="header">
<th>![image2](../../assets/8a70345f974b4a25908e084b6b7145aa.png)</th>
<th><p>![image3](../../assets/2bcba577cb044e45a80b298ba313130c.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

![image4](../../assets/59ae7346881b4b9197d9138a0b1bb70f.png)

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>import java.util.ArrayList;</p>
<p>import java.util.List;</p>
<p></p>
<p>class CompositeEmployee implements IEmployee</p>
<p>{</p>
<p>//private static int employeeCount=0;</p>
<p>private int employeeCount=0;</p>
<p>private String name;</p>
<p>private String dept;</p>
<p>//The container for child objects</p>
<p>private List&lt;IEmployee&gt; controls;</p>
<p>//Constructor</p>
<p>public CompositeEmployee(String name, String dept)</p>
<p>{</p>
<p>this.name = name;</p>
<p>this.dept = dept;</p>
<p>controls = new ArrayList&lt;IEmployee&gt;();</p>
<p>}</p>
<p>public void addEmployee(IEmployee e)</p>
<p>{</p>
<p>controls.add(e);</p>
<p>}</p>
<p>public void removeEmployee(IEmployee e)</p>
<p>{</p>
<p>controls.remove(e);</p>
<p>}</p>
<p>@Override</p>
<p>public void printStructures()</p>
<p>{</p>
<p>System.out.println("\t" + this.name + " works in " + this.dept);</p>
<p>for(IEmployee e: controls)</p>
<p>{</p>
<p>e.printStructures();</p>
<p>}</p>
<p>}</p>
<p>@Override</p>
<p>public int getEmployeeCount()</p>
<p>{</p>
<p>employeeCount=controls.size();</p>
<p>for(IEmployee e: controls)</p>
<p>{</p>
<p>employeeCount+=e.getEmployeeCount();</p>
<p>}</p>
<p>return employeeCount;</p>
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
<th><p></p>
<p>class CompositePatternExample {</p>
<p>/**Principal is on top of college.</p>
<p>*HOD -Maths and Comp. Sc directly reports to him</p>
<p>*Teachers of Computer Sc. directly reports to HOD-CSE</p>
<p>*Teachers of Mathematics directly reports to HOD-Maths</p>
<p>*/</p>
<p>public static void main(String[] args) {</p>
<p>System.out.println("***Composite Pattern Demo ***");</p>
<p>//2 teachers other than HOD works in Mathematics department</p>
<p>Employee mathTeacher1 = new Employee("Math Teacher-1","Maths");</p>
<p>Employee mathTeacher2 = new Employee("Math Teacher-2","Maths");</p>
<p>//teachers other than HOD works in Computer Sc. Department</p>
<p>Employee cseTeacher1 = new Employee("CSE Teacher-1", "Computer Sc.");</p>
<p>Employee cseTeacher2 = new Employee("CSE Teacher-2", "Computer Sc.");</p>
<p>Employee cseTeacher3 = new Employee("CSE Teacher-3", "Computer Sc.");</p>
<p>//The College has 2 Head of Departments-One from Mathematics, One</p>
<p>//from Computer Sc.</p>
<p>CompositeEmployee hodMaths = new CompositeEmployee("Mrs.S.Das(HOD-Maths)","Maths");</p>
<p>CompositeEmployee hodCompSc = new CompositeEmployee("Mr. V.Sarcar(HOD-CSE)", "Computer Sc.");</p>
<p>//Principal of the college</p>
<p>CompositeEmployee principal = new CompositeEmployee("Dr.S.Som (Principal)","Planning-Supervising-Managing");</p>
<p>//Teachers of Mathematics directly reports to HOD-Maths</p>
<p>hodMaths.addEmployee(mathTeacher1);</p>
<p>hodMaths.addEmployee(mathTeacher2);</p>
<p>//Teachers of Computer Sc. directly reports to HOD-CSE</p>
<p>hodCompSc.addEmployee(cseTeacher1);</p>
<p>hodCompSc.addEmployee(cseTeacher2);</p>
<p>hodCompSc.addEmployee(cseTeacher3);</p>
<p>/*Principal is on top of college.HOD -Maths and Comp. Sc directly</p>
<p>reports to him*/</p>
<p>principal.addEmployee(hodMaths);</p>
<p>principal.addEmployee(hodCompSc);</p>
<p>/*Printing the leaf-nodes and branches in the same way i.e.</p>
<p>in each case, we are calling PrintStructures() method</p>
<p>*/</p>
<p>System.out.println("\n Testing the structure of a Principal object");</p>
<p>//Prints the complete structure</p>
<p>principal.printStructures();</p>
<p>System.out.println("At present Principal has control over "+</p>
<p>principal.getEmployeeCount()+ " number of employees.");</p>
<p>System.out.println("\n Testing the structure of a HOD-CSE object:");</p>
<p>//Prints the details of Computer Sc, department</p>
<p>hodCompSc.printStructures();</p>
<p>System.out.println("At present HOD-CSE has control over "+</p>
<p>hodCompSc.getEmployeeCount()+ " number of employees.");</p>
<p>System.out.println("\n Testing the structure of a HOD-Maths object:");</p>
<p>//Prints the details of Mathematics department</p>
<p>hodMaths.printStructures();</p>
<p>System.out.println("At present HOD-Maths has control over "+</p>
<p>hodMaths.getEmployeeCount()+ " number of employees.");</p>
<p>//Leaf node</p>
<p>System.out.println("\n Testing the structure of a leaf node:");</p>
<p>mathTeacher1.printStructures();</p>
<p>System.out.println("At present Math Teacher-1 has control over "+</p>
<p>mathTeacher1.getEmployeeCount()+ " number of employees.");</p>
<p>/*Suppose, one computer teacher is leaving now</p>
<p>from the organization*/</p>
<p>hodCompSc.removeEmployee(cseTeacher2);</p>
<p>System.out.println("\n After CSE Teacher-2 resigned, the organization has following members:");</p>
<p>principal.printStructures();</p>
<p>System.out.println("At present Principal has control over "+</p>
<p>principal.getEmployeeCount()+ " number of employees");</p>
<p>System.out.println("At present HOD-CSE has control over "+</p>
<p>hodCompSc.getEmployeeCount()+ " number of employees");</p>
<p>System.out.println("At present HOD-Maths has control over "+</p>
<p>hodMaths.getEmployeeCount()+ " number of employees");</p>
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
<th><p>***Composite Pattern Demo ***</p>
<p></p>
<p>Testing the structure of a Principal object</p>
<blockquote>
<p>Dr.S.Som (Principal) works in Planning-Supervising-Managing</p>
<p>Mrs.S.Das(HOD-Maths) works in Maths</p>
<p>Math Teacher-1 works in Maths</p>
<p>Math Teacher-2 works in Maths</p>
<p>Mr. V.Sarcar(HOD-CSE) works in Computer Sc.</p>
<p>CSE Teacher-1 works in Computer Sc.</p>
<p>CSE Teacher-2 works in Computer Sc.</p>
<p>CSE Teacher-3 works in Computer Sc.</p>
</blockquote>
<p>At present Principal has control over 7 number of employees.</p>
<p></p>
<p>Testing the structure of a HOD-CSE object:</p>
<blockquote>
<p>Mr. V.Sarcar(HOD-CSE) works in Computer Sc.</p>
<p>CSE Teacher-1 works in Computer Sc.</p>
<p>CSE Teacher-2 works in Computer Sc.</p>
<p>CSE Teacher-3 works in Computer Sc.</p>
</blockquote>
<p>At present HOD-CSE has control over 3 number of employees.</p>
<p></p>
<p>Testing the structure of a HOD-Maths object:</p>
<blockquote>
<p>Mrs.S.Das(HOD-Maths) works in Maths</p>
<p>Math Teacher-1 works in Maths</p>
<p>Math Teacher-2 works in Maths</p>
</blockquote>
<p>At present HOD-Maths has control over 2 number of employees.</p>
<p></p>
<p>Testing the structure of a leaf node:</p>
<blockquote>
<p>Math Teacher-1 works in Maths</p>
</blockquote>
<p>At present Math Teacher-1 has control over 0 number of employees.</p>
<p></p>
<p>After CSE Teacher-2 resigned, the organization has following members:</p>
<blockquote>
<p>Dr.S.Som (Principal) works in Planning-Supervising-Managing</p>
<p>Mrs.S.Das(HOD-Maths) works in Maths</p>
<p>Math Teacher-1 works in Maths</p>
<p>Math Teacher-2 works in Maths</p>
<p>Mr. V.Sarcar(HOD-CSE) works in Computer Sc.</p>
<p>CSE Teacher-1 works in Computer Sc.</p>
<p>CSE Teacher-3 works in Computer Sc.</p>
</blockquote>
<p>At present Principal has control over 6 number of employees</p>
<p>At present HOD-CSE has control over 2 number of employees</p>
<p>At present HOD-Maths has control over 2 number of employees</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## 4，优缺点
优点： 1、高层模块调用简单。 2、节点自由增加。

缺点：在使用组合模式时，其叶子和树枝的声明都是实现类，而不是接口，违反了依赖倒置原则。
“依赖倒置原则（Dependence Inversion Principle）是程序要依赖于抽象接口，不要依赖于具体实现。简单的说就是要求对抽象进行编程，不要对实现进行编程，这样就降低了客户与实现模块间的耦合。

## 5，适用场景
部分、整体场景，如树形菜单，文件、文件夹的管理。

![image5](../../assets/3ca43854d701453a90e7fbee742fd0f4.png)

