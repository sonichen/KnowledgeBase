---
title: 7 – Stacks and Queues
updated: 2021-01-09T15:58:31.0000000+08:00
created: 2020-12-24T22:01:39.0000000+08:00
---

一、stacks
1，stack，先进后出
The stack mechanism is known as Last-In-First-Out (LIFO) because the last item inserted is the first one removed 【栈的解释】

2，操作
• There are several things you can do with a stack
• Pop ( ) – pop the top item off the stack
• Push ( ) – put another item onto the top
• Peek ( ) – look at the top item and copy it
![image1](../../assets/720c2d900a364c55839ed3819a076af8.png)

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 66%" />
</colgroup>
<thead>
<tr class="header">
<th><p>push ( element )</p>
<p>• insert an element at the top of the stack</p></th>
<th><p>![image2](../../assets/7246ee0cfc174a80bfb112e3e55a30e5.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>• pop ( )</p>
<p>• remove an element from the top of the stack</p></td>
<td><p>![image3](../../assets/7c4902a3f8084d69b4d3d5f8aa924fc3.png)</p>
<p></p></td>
</tr>
<tr class="even">
<td><p>• Peek ( )</p>
<p>• look at the top item and copy it</p></td>
<td><p>![image4](../../assets/8bc9f23a24a64053aaf9dd7647109a78.png)</p>
<p></p></td>
</tr>
</tbody>
</table>

其他操作
| • MakeEmpty( ) | Remove all items from the stack         |
|----------------|-----------------------------------------|
| • IsEmpty( )   | True if stack is empty, false otherwise |
| • IsFull( )    | True if stack is full, false otherwise  |

3，用数组模拟stack
Array-based Stack
![image5](../../assets/5a2d9bba375f43df920808528b2c9a4f.png)

初始情况：top=-1

1，stack满则A push operation will then throw a **FullStackException**
• Limitation of the array-based implementation

• Not intrinsic to the Stack ADT
2，所需字段：
maxSize，stackArray，top=-1
<table>
<colgroup>
<col style="width: 22%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 26%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image6](../../assets/de5b65fee1734e60ae56a459f40ce71d.png)</p>
<p></p></th>
<th><p>![image7](../../assets/1f5b42f717314babaa729bf031108db6.png)</p>
<p>![image8](../../assets/23730fb39fb74726b3c0041a25b421d9.png)</p>
<p>![image9](../../assets/9d4e04d62ef246c59b22934157a76566.png)</p>
<p></p></th>
<th><p>![image10](../../assets/3f457c86a6ab43a89e7bfa19571111c4.png)</p>
<p></p></th>
<th><p>![image11](../../assets/3c7c68a602dc489e85902dda7c6f31b3.png)</p>
<p></p>
<p></p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

3, Can you think of anything else using a stack structure?
• Web browsers
• Undo sequence in a text editor
• Java Virtual Machine

4，Method Stack in the JVM

![image12](../../assets/a0ebd8265d3f42299f736756680ada5e.png)
![image13](../../assets/983abc3d0f29414e8ac3f4af77fb8ea9.png)

6，例子
（1）The LIFO principle can be used in reversing a word
（2）Checking for palindromes
![image14](../../assets/c63110eb1f1b418d8a5bb4e41fa14f31.png)

7，Performance
• Let 𝒏 be the number of elements in the stack
• The space used is 𝑶(𝒏)
• Each **operation** runs in time 𝑶(𝟏) (e.g. pop, push)

8,Limitations for **array-based** stacks
• The maximum size of the stack must be defined a
priori and cannot be changed
栈的长度已经定型
• Trying to push a new element into a full stack causes
an implementation-specific exception
向满栈加入元素有异常

二、Queues
1,queues的解释：
• A queue means **to line up for something**
Queues uses the **First-In-First-Out system (FIFO)，** the one that has been in the queue the longest is the one that is popped

2,variables
• Size of the array
• The array itself
• Variables for tracking front and rear

| Empty Queue:      | Front = 0, Rear = -1 |
|-------------------|----------------------|
| 3 items in queue: | Front = 0, Rear = 2  |

3，操作：加在rear，取走在front
Insertions are made at one end, the back of the queue
Deletions take place at the other end, the front of the queue

![image15](../../assets/5f4943783af4447a97e58d3710e10290.png)

Front=0；rear=-1；
<table>
<colgroup>
<col style="width: 13%" />
<col style="width: 86%" />
</colgroup>
<thead>
<tr class="header">
<th>Insert</th>
<th><p>• Assumes the queue is not full</p>
<p>• Inserts at rear</p>
<p>• If <strong>rear is at the top</strong> of the array then it wraps around to the bottom of the array</p>
<p>![image16](../../assets/0fc3905d639142af8a52eef1069c6998.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Remove()</td>
<td><p>Assumes queue is not empty</p>
<p>• Obtains the value at the front</p>
<p>• Increments the front variable</p>
<p>• If front goes beyond the end of the array it must be</p>
<p>wrapped around to 0•如果front超过数组的末尾，它必须绕成0</p></td>
</tr>
<tr class="even">
<td>peek ( )</td>
<td>Returns the value at the front</td>
</tr>
<tr class="odd">
<td>size ( )</td>
<td>Assumes queue not empty • Returns total number in queue</td>
</tr>
<tr class="even">
<td>isFull ( )</td>
<td>• Returns true if queue is full</td>
</tr>
<tr class="odd">
<td>isEmpty ( )</td>
<td>• Returns true if queue is empty</td>
</tr>
</tbody>
</table>

案例
![image17](../../assets/b5cbb62288e1468684ac5a7931fa09e4.png)

**wrapround包着的**
(rear+1)%maxSize==front \[满\]
![image18](../../assets/fd6f72de639d434f991fb72b61ceb852.png)

4，Array-based Queue
![image19](../../assets/b53c398ec1154e76b6771b725551ab17.png)
代码
<table>
<colgroup>
<col style="width: 18%" />
<col style="width: 28%" />
<col style="width: 27%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image20](../../assets/f9489409305c4d85a8bf88d8d906bd22.png)</p>
<p></p></th>
<th><p>![image21](../../assets/ff25e7d2f06c4fe5be5ce87c31efd4bc.png)</p>
<p></p></th>
<th><p>![image22](../../assets/c99d5c8baf39415bb296488eef20154e.png)</p>
<blockquote>
<p></p>
</blockquote></th>
<th><p>![image23](../../assets/5474278f685447ba9f92a27b6e33a677.png)</p>
<p></p>
<p>![image24](../../assets/81474a944a6b428e95d3aa27e45ac220.png)</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

案例
| **Operation** | **Output** | **front ç Q ç rear** |
|---------------|------------|-----------------------|
| insert(5)    | \-         | 5                     |
| insert(3)    | \-         | 5,3                   |
| remove()      | 5          | 3                     |
| insert(7)    | \-         | 3,7                   |
| remove()      | 3          | 7                     |
| front()      | 7          | 7                     |
| remove()      | 7          |                      |
| remove()      | error      |                      |
| isEmpty()     | true       |                      |
| insert(9)     | \-         | 9                     |
| insert(7)     | \-         | 9,7                   |
| size()        | 2          | 9,7                   |
| insert(3)     | \-         | 9,7,3                 |
| insert(5)     | \-         | 9,7,3,5               |
| remove()      | 9          | 735                   |

![image25](../../assets/b1ab4b7f48ab4c198c72b10e0d59ab9f.png)
5，Performance
• Let 𝒏 be the **number of elements** in the queue
• The space used is 𝑶(𝒏)
• Each operation runs in time 𝑶(𝟏)

6，• Limitations for **array-based queues**
• The maximum size of the queue must be defined a priori and cannot be changed
• Trying to insert a new element into a full queue causes an implementation-specific exception

三、Deque
1,• A deque is a **double-ended** queue 双端队列；双队列
insert items at either end and delete them at either end
**no longer a front and rear, simply two ends**

2,操作
<table>
<colgroup>
<col style="width: 19%" />
<col style="width: 80%" />
</colgroup>
<thead>
<tr class="header">
<th>• insertLeft( )</th>
<th><p>![image26](../../assets/3526457fc6604fd7a35d2a82e258617e.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>• insertRight( )</td>
<td>![image27](../../assets/9c36defb0d7347a5bf66d31a7db83541.png)</td>
</tr>
<tr class="even">
<td>• removeLeft( )</td>
<td>![image28](../../assets/79fab0f418234b0589ded65871a79b54.png)</td>
</tr>
<tr class="odd">
<td>• removeRight( )</td>
<td>![image29](../../assets/6961f8817bda4cc09ac595d4046eace8.png)</td>
</tr>
</tbody>
</table>

3，
<table>
<colgroup>
<col style="width: 64%" />
<col style="width: 35%" />
</colgroup>
<thead>
<tr class="header">
<th><p>• A stack is actually a deque with only the methods</p>
<p>• insertRight( ) • removeRight( )</p></th>
<th><p>![image30](../../assets/671337e2c3814031a0df109d7f32bd69.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>• A queue is a deque with only the methods</p>
<p>• insertRight( ) • removeLeft( )</p></td>
<td><p>![image31](../../assets/b123b9c575f6448eb6a179fdecf6e5f6.png)</p>
<p></p></td>
</tr>
</tbody>
</table>

四、Priority Queue
1，A priority queue is a queue where items **don’t just join at the rear**, they are slotted into the queue according to their priority
其中的项目不只是在后面加入，而是根据它们的优先级插入队列
2，操作
不需要front和rear，总是停留在**索引0**
only need to track the top

• Insert method has a for loop that shifts elements up 【shift elements up to make space rather 】

• Remove method simply removes the top (highest priority) element

是queue结构，但是类似栈，把最优先的放在“栈里的top”

<table>
<colgroup>
<col style="width: 53%" />
<col style="width: 46%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image32](../../assets/05e177516a35412b8a8ef8826ed14adf.png)</p>
<p></p></th>
<th><p>假设越小的数权重越大</p>
<p>![image33](../../assets/f39cdab6c37d4b7988a46c0affb9acf4.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

