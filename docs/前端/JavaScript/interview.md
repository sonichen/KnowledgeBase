## 1.数据类型

### 1.1 基本数据类型

8种数据类型，分为两大类

值类型，直接存在栈stack中的简单数据段，大小固定，是频繁使用的

引用类型（object），存在heap堆中，大小不固定

另外，es6中

symbol: 独一无二

bigint: 表示任意大小数

### 1.2 数据类型判断

typeof：判断所有的值类型，函数；不能判断null, 对象和array，因为都返回object

instanceof：能判断对象类型，不能判断基本数据类型，其内部运⾏机制是判断在其原型链中能否找到该类型 的原型。

在⾯试中有⼀个经常被问的问题就是：如何判断变量是否为数组？

```
  Array.isArray(arr); // true 

  arr.__proto__ ===  Array.prototype; // true  

  arr instanceof Array; // true  

  Object.prototype.toString.call(arr);  // "[object Array]"  

```

### 1.3 深拷贝，浅拷贝

深拷贝和浅拷贝是指**在赋值一个对象时，拷贝的深度不同**。 区别是浅拷贝是拷贝了对象的引用，当原对象发生变化的时候，拷贝对象也跟着变化；深拷贝是另外申请了一块内存，内容和原对象一样，更改原对象，拷贝对象不会发生变化。

Deep copy and shallow copy mean that **when assigning an object, the copy depth is different.** The difference is that **shallow copy copies the reference of the object.** When the original object changes, the copied object also changes; **deep copy applies for another piece of memory, and the content is the same as the original object.** If the original object is changed, the copied object will not change. .

**JSON.parse(JSON.stringify(obj))**

> 性能最快

▪ 具有循环引⽤的对象时，报错

▪ 当值为函数、undefined、或symbol时，⽆法拷⻉

### 1.4 根据 0.1+0.2 ! == 0.3，讲讲 IEEE 754 ，如何让其相等？

但是 js 采⽤ 的 IEEE 754 ⼆进制浮点运算，最⼤可以存储 53 位有效数字，于是⼤于 53 位后⾯的会全部截 掉，将导致精度丢失。

**JavaScript使⽤Number类型表示数字（整数和浮点数），遵循 IEEE 754 标准 通过64位来表示⼀个数字**

sulution:

- 将数字转成整数(对大树不好)
- 第三方库（Math.js, big.js）
- 转成字符串，对字符串做加法运算。

## 2. 原型和原型链

*JavaScript 中*所有的对象都有一个内置属性，称为它的prototype（*原型*）。它本身是一个对象，故*原型*对象也会有它自己的*原型*，逐渐构成了*原型*链。



## 3.作用域和作用域链条

作用域：作⽤域决定了代码区块中变量和其他资源的可⻅性。

作用域链条

## 4.闭包

闭包是指那些能够访问⾃由变量的函数。 ⾃由变量是指在函数中使⽤的，但既不是函数参数也不是函数的局部变量的变量。

**闭包 = 函数 + 函数能够访问的⾃由变量。**



## 5. call、apply、bind 实现

call() ⽅法在使⽤⼀个指定的 this 值和若⼲个指定的参数值的前提下调⽤某个函数或⽅法。

bind() 返回的是⼀个函数



## 6. new 实现



## 7.异步

### 什么是宏任务与微任务？

> `JavaScript`将所有执行任务分为了同步任务和异步任务。我们都知道 Js 是单线程都，但是⼀些⾼耗时操作就带来了进程阻塞问题。为了解决这个问题，Js 有两种任务 的执⾏模式：同步模式（Synchronous）和异步模式（Asynchronous）。

ES6 规范中，宏任务（Macrotask） 称为 Task， 微任务（Microtask） 称为 Jobs。宏任务是由宿主（浏览器、Node）发起的，⽽ 微任务由 JS ⾃身发起。

### 如何理解 script（整体代码块）是个宏任务呢

### 什么是 EventLoop ？

*Event Loop是*一个程序结构，用于等待和发送消息和事件。

*Event Loop* 即事件循环,*是*指浏览器或Node的一种解决javaScript单线程运行时不会阻塞的一种机制。

Event Loop is an event loop, which refers to a mechanism of the browser or Node that prevents JavaScript from blocking when running in a single thread.

### 7.2 Promise

### 7.3 async/await 和 Promise 的关系

• async/await 是消灭异步回调的终极武器。

• 但和 Promise 并不互斥，反⽽，两者相辅相成。

• 执⾏ async 函数，返回的⼀定是 Promise 对象。

• await 相当于 Promise 的 then。

• try...catch 可捕获异常，代替了 Promise 的 catch。



##  8 浏览器的垃圾回收机制

### 两种垃圾回收策略

• 标记清除：标记阶段即为所有活动对象做上标记，清除阶段则把没有标记（也就是⾮活动对象）销毁。

• 引⽤计数：它把对象是否不再需要简化定义为对象有没有其他对象引⽤到它。如果没有引⽤指向该对象 （引⽤计数为 0），对象将被垃圾回收机制回收。



## web 存储

### cookie，session localStorage 和 sessionStorage。

### cookie

*Cookie 是*浏览器访问服务器后，服务器传给浏览器的一段数据。 

浏览器需要保存这段数据，不得轻易删除。

本身⽤于浏览器和 server 通讯。

是保存在客户端的，⼀般由后端设置值，可以设置过期时间

### session

session是保存在服务端的 session的运⾏依赖sessionId，⽽sessionId⼜保存在cookie中，所以如果禁⽤的 cookie，session也是不能⽤的，不过硬要⽤也可以，可以把sessionId保存在URL 中

session⼀般⽤来跟踪⽤户的状态

session 的安全性更⾼，保存在服务端，不过⼀般为使服务端性能更加，会考虑 部分信息保存在cookie中



### localStorage 和 sessionStorage

• localStorage 数据会永久存储，除⾮代码删除或⼿动删除。

 • sessionStorage 数据只存在于当前会话，浏览器关闭则清空。

## 设计模式

### MVVM（Model-View-ViewModel)

### 观察者模式和发布/订阅模式

#### 观察者

观察者模式是使⽤⼀个subject⽬标对象维持⼀系列依赖于它的observer观察者对象，**将有关状态的任何变更 ⾃动通知给这⼀系列观察者对象。**当subject⽬标对象需要告诉观察者发⽣了什么事情时，它会向观察者对象 们⼴播⼀个通知。

#### 订阅者

发布/订阅模式使⽤⼀个事件通道，这个通道介于订阅者和发布者之间，该设计模式允许代码定义应⽤程序的特定事 件，这些事件可以传递⾃定义参数，⾃定义参数包含订阅者需要的信息，采⽤事件通道可以避免发布者和订阅者之 间产⽣依赖关系。

观察者模式：允许观察者实例对象(订阅者)执⾏适当的事 件处理程序来注册和接收⽬标实例对象(发布者)发出的通 知（即在观察者实例对象上注册update⽅法），使订阅者 和发布者之间产⽣了依赖关系，且没有事件通道。不存 在封装约束的单⼀对象，⽬标对象和观察者对象必须合 作才能维持约束。 观察者对象向订阅它们的对象发布其 感兴趣的事件。通信只能是单向的。

发布/订阅模式：单⼀⽬标通常有很多观察者，有时⼀个 ⽬标的观察者是另⼀个观察者的⽬标。通信可以实现双 向。该模式存在不稳定性，发布者⽆法感知订阅者的状态。

