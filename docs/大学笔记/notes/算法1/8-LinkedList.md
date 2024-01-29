---
title: 8-LinkedList
updated: 2021-01-08T15:33:23.0000000+08:00
created: 2020-12-26T21:50:34.0000000+08:00
---

LinkedList和array的优缺点
<table>
<colgroup>
<col style="width: 7%" />
<col style="width: 40%" />
<col style="width: 52%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Linked List</th>
<th>Array</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>优点</td>
<td><p>1，they can adapt their ordering by changing the items they point to – no memory is wasted</p>
<p>3，extra links can easily be added</p></td>
<td><p>1，New elements can be stored anywhere and a reference is created for the new element using pointers.</p>
<p>2，Random accessing is possible.</p>
<p>3，Memory is allocated during the run-time (Dynamic memory allocation).</p>
<p>4，Array elements can be accessed randomly using the array index.</p>
<p>5，Insertion and Deletion operations are fast and easy.</p>
<p></p></td>
</tr>
<tr class="even">
<td>缺点</td>
<td><p>1，With a linked list, if we need to find the special link, we have to start at the beginning of the chain, and work the way along in order to find an item</p>
<p>2，Binary search not possible – big disadvantage of linked lists</p></td>
<td><p>1. waste space</p>
<p>2. not easy to extend an array.</p>
<p>Size of the array must be specified at the time of array declaration/initialization.</p>
<p>3. to insert a new element is not easy</p></td>
</tr>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 10%" />
<col style="width: 23%" />
<col style="width: 65%" />
</colgroup>
<thead>
<tr class="header">
<th>Linked List</th>
<th>头节点=空数据+第一个link的reference</th>
<th><p>![image1](../../assets/568e762370654efa9de462c60e2c7d61.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Double-Ended Linked Lists</td>
<td>头节点=first reference+last reference</td>
<td><p>![image2](../../assets/5c69c6a6cdf84ac4aa8d001b5bb5bc08.png)</p>
<p></p></td>
</tr>
<tr class="even">
<td>Singly Linked List</td>
<td>无上述的头节点，直接第一个开始【data+reference】</td>
<td><p>![image3](../../assets/975f8c15382a4f7cbbaffa98a5185eb2.png)</p>
<p></p></td>
</tr>
<tr class="odd">
<td>Sorted Lists</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>Doubly Linked Lists</td>
<td>头节点=first reference+last reference</td>
<td><p>![image4](../../assets/0fb7f416c6cf43b39de1099d7894e302.png)</p>
<p></p></td>
</tr>
</tbody>
</table>

一、Linked List
1， A linked list is an abstract data structure consisting of **a sequence of links**
![image5](../../assets/fab6a66af84f48c0b711f874653066a1.png)

• Link objects are created for each link in the list
• All contain **references** to the next link in the list

2，结构
![image6](../../assets/d4c8d3f581524fa4b7db6b5e70d362be.png)
这里的first相当于head，头结点,不存储数据，只是一个指向头
this is only a reference to the next Link，**does not represent the actual object itself**

• Linked list only contains a reference to the first link
• This is originally set to null
![image7](../../assets/577784ff110e4bd38691c414223c672c.png)

2，操作
• The head is the first link
• The tail is the last link

<table>
<colgroup>
<col style="width: 51%" />
<col style="width: 48%" />
</colgroup>
<thead>
<tr class="header">
<th>Inserting at the Head</th>
<th></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>• 1. Create a new link</p>
<p>• 2. Have new link point to old first link</p>
<p>• 3. Update Linked List to point to new link</p>
<p>![image8](../../assets/39e46019d9384693a955d5d9fce12b9b.png)</p>
<p></p></td>
<td><p>![image9](../../assets/726b2a29273944e9ab4518fcfc76130f.png)</p>
<p></p></td>
</tr>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 45%" />
<col style="width: 54%" />
</colgroup>
<thead>
<tr class="header">
<th>Deleting at the Head</th>
<th></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>• Update head to point to next node in the list</p>
<p>• Garbage collector will now reclaim the former first node</p>
<p>![image10](../../assets/cc2532f738994c2cb45a5ccbf2c3ffca.png)</p>
<p></p></td>
<td><p>![image11](../../assets/e3129a43976a4925b130167d506b3a76.png)</p>
<p></p></td>
</tr>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 18%" />
<col style="width: 81%" />
</colgroup>
<thead>
<tr class="header">
<th>Traversing a linked list</th>
<th></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>必须从头开始遍历，</p>
<p>而且二分法不能用【大大滴缺点】</p></td>
<td><p>![image12](../../assets/d572582212d74a7aae80c5af7167c015.png)</p>
<p></p></td>
</tr>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 44%" />
<col style="width: 55%" />
</colgroup>
<thead>
<tr class="header">
<th>find or delete one particular node</th>
<th></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>• Take in the value to be found or deleted</p>
<p>• Start at the beginning of the list</p>
<p>• Keep moving down the links until we find the correct</p>
<p>one</p>
<p>• All the while keep tracking the current link and the</p>
<p>previous link (so we can join them up when required)</p>
<p>• Now update the references to bypass the link to be</p>
<p>deleted</p>
<p>![image13](../../assets/a48c5b00afe94fa8b0a12e173ceebd8e.png)</p>
<p></p></td>
<td><p>![image14](../../assets/05eabdbb0b174309bb36cc889ca6ec0c.png)</p>
<p></p></td>
</tr>
</tbody>
</table>

二、Double-Ended Linked Lists 双头链表
1，• It as a reference to the last link as well as the first
![image15](../../assets/1dc7920b570c4b1c9ec1ab0662216b19.png)

2，操作
![image16](../../assets/4f44e01052b84738940d12d920e535ea.png)

<table>
<colgroup>
<col style="width: 46%" />
<col style="width: 53%" />
</colgroup>
<thead>
<tr class="header">
<th>Inserting at the Tail</th>
<th></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>• Create a new link</p>
<p>• Have new link point to null</p>
<p>• Have old <strong>last link point to new node</strong></p>
<p>• Update tail of Linked List object to point to new node</p></td>
<td><p>![image17](../../assets/2bb440769d5b4e91ac1a88c86682361d.png)</p>
<p></p></td>
</tr>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 14%" />
<col style="width: 85%" />
</colgroup>
<thead>
<tr class="header">
<th>Removing at the Tail</th>
<th></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>• Removing at the tail of a singly-linked double ended list</p>
<p><strong>is not efficient!</strong></p>
<p>• There is no constant time way to update the tail to point</p>
<p>to the previous node</p>
<p>• We need to use</p>
<p>double links (that point to <strong>both next and previous link</strong>)</p></td>
<td><p>![image18](../../assets/915939fcf0df438ea1ddf7cb24cf9bf8.png)</p>
<p></p></td>
</tr>
</tbody>
</table>

三、Linked-List Efficiency
![image19](../../assets/ba03f431c2c84ef7bf85a9a3579cdd48.png)
用堆栈来实现均可
![image20](../../assets/c3a679b7f26443ffa8f362ba4b40d442.png)

四、Singly Linked List
1，**Stack with a Singly Linked List**
此时无头结点
• The top element is stored at the first node of the list
• The space used is 𝑶(𝒏) and each operation of the Stack ADT takes 𝑶(𝟏) time
![image21](../../assets/02bc58227427492ab1260e16aa7d02ad.png)

2，Queue with a Singly Linked List
• The front element is stored at the first node
• The rear element is stored at the last node
![image22](../../assets/19a8bb6ab7bd4d10bbcb6e3ea381c7b3.png)

五、Sorted Lists
priority queue – this required the items to be sorted
1，Only way to find the correct location is to **search through the list**
– can’t use binary search
• When you find the correct location (i.e. when you find a value bigger than the one you want to insert) update the pointers of the relevant links

2，操作
<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 49%" />
</colgroup>
<thead>
<tr class="header">
<th>Insertion</th>
<th></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>The new element must be set to point to the next</p>
<p>element in the linked list</p>
<p></p>
<p>The previous element must be updated to point to</p>
<p>the new element</p>
<p>![image23](../../assets/b3646dda3e5647b4a789206fa9d939fd.png)</p>
<p></p></td>
<td><p>![image24](../../assets/bf1f18126d5146b594975b710edc88f4.png)</p>
<p></p></td>
</tr>
</tbody>
</table>

3、Efficiency of Sorted Linked Lists
![image25](../../assets/36da07c2b20f4067a255cafc4244dc1a.png)

4，Using linked lists for array sorting
![image26](../../assets/c54c952b7b9747a099f7b22ca49cc756.png)

六、Doubly Linked Lists 双链表
单链表不能backwards
1，A linked list where you can traverse it forwards or
backwards is a **doubly linked list** (references going both ways)
<table>
<colgroup>
<col style="width: 37%" />
<col style="width: 62%" />
</colgroup>
<thead>
<tr class="header">
<th><p>现在是data+（next reference和prev reference）</p>
<p>操作的时候记得更新两个索引</p>
<p>list中，</p>
<p><strong>first头结点的next是第一个link</strong></p>
<p><strong>第一个link的pre是空，</strong></p></th>
<th>![image4](../../assets/0fb7f416c6cf43b39de1099d7894e302.png)</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

2，操作
<table>
<colgroup>
<col style="width: 47%" />
<col style="width: 52%" />
</colgroup>
<thead>
<tr class="header">
<th>Insertion at begining</th>
<th></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>– Change prev of first link</p>
<p>– Change next of new link</p>
<p>– Change first of Linked List</p>
<p>![image27](../../assets/66477d536ab1467b91254b9c02b79101.png)</p>
<p></p></td>
<td><p>![image28](../../assets/358332c23a274bdc894fc7e9df09d2b7.png)</p>
<p></p></td>
</tr>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 49%" />
</colgroup>
<thead>
<tr class="header">
<th>Insertion in order</th>
<th></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>![image29](../../assets/4c1e11fdad5448b5a27b4cef3026aae9.png)</p>
<p></p>
<p>![image30](../../assets/19a72083e4264582a82f99e2f87c5af5.png)</p></td>
<td>![image31](../../assets/a27cd897b01944be9aa419b41ebfa9d9.png)</td>
</tr>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 51%" />
<col style="width: 48%" />
</colgroup>
<thead>
<tr class="header">
<th>Deletion</th>
<th></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>– Change next of left link</p>
<p>– Change prev of right link</p>
<p>![image32](../../assets/197baa662b1a46ea9a750920aa5dd552.png)</p>
<p></p></td>
<td>![image33](../../assets/53066ab39b2c420580c1d0e61ca5f3f4.png)</td>
</tr>
</tbody>
</table>

七、Iterators\[!!重点，看不懂\]

1，• Iterators always **point to some link** in the list
• They are associated with the list but are **not part of it**
![image34](../../assets/f321e599acdf4392bcded8c1cb8f1c5b.png)

2，Objects containing references to items in data structures, used to
traverse these structures, are commonly called iterators
![image35](../../assets/74f34112392442b897357ec49a2754e6.png)

• If our linked list **isn’t doubly-linked** then the iterator
**should store both current and previous** so that it can
delete links
• It is also handy for the iterator to store a reference to the
linked list class so it can access the first element of the
list
![image36](../../assets/12e528e92b774bc59c027195e63f407b.png)

3，操作
![image37](../../assets/c5487ffc89c54c5ea513b26557f53b31.png)

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th>Removing a Link using the Iterator【注意】</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>![image38](../../assets/63b3fbbd13ba4b0fa665c6d9b209f837.png)</p>
<p></p></td>
</tr>
</tbody>
</table>

| Adding a Link using the Iterator【注意】                                                                                                                                                                                                                                                                                                                                                                                |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ![image39](../../assets/6c2738ddccfc48e6902e2a77a2263b61.png) |

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th>The atEnd() Method</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>![image40](../../assets/dd7db82b13d74eb6b5d4d6227cd150ea.png)</p>
<p></p></td>
</tr>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th>Stacks using Linked Lists</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>![image41](../../assets/5031cceb13a24429b17ea1b865ff0b7d.png)</p>
<p></p></td>
</tr>
</tbody>
</table>

Linked List代码
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>![image42](../../assets/7488efb5b5ec432581e29b7210a89354.png)</p>
<p></p>
<p>![image43](../../assets/b6ea8266c42a4bb188ac1a4c98bb8f19.png)</p>
<p></p>
<p>![image44](../../assets/ab19ac0b711344c6ace94c66676fd45e.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

![image45](../../assets/1ac9fadb8dfd4f799bae12a584ec5877.png)

