### 1.Js基本数据类型有哪些

7种。`Number`、`String`、`Boolean`、`Null`、`undefined`、`object`、`symbol`。

> 在ES5的时候，我们认知的数据类型是前6种。
>
> ES6 中新增了一种 `Symbol` 。这种类型的对象永不相等，即始创建的时候传入相同的值，可以解决属性名冲突的问题，做为标记。

------

### 2.Ajax如何使用

> **全称：**`Asynchronous Javascript And XML`(异步传输+js+xml)。
> 所谓**异步**，在这里简单地解释就是：向服务器发送请求的时候，我们不必等待结果，而是可以同时做其他的事情，等到有了结果它自己会根据设定进行后续操作，与此同时，页面是不会发生整页刷新的，提高了用户体验

(1)创建`XMLHttpRequest`对象,也就是创建一个异步调用对象.
(2)创建一个新的`HTTP`请求,并指定该HTTP请求的方法、URL及验证信息.
(3)设置响应`HTTP`请求状态变化的函数.
(4)发送`HTTP`请求.
(5)获取异步调用返回的数据.
(6)使用`JavaScript`和`DOM`实现局部刷新.

```javascript
var xmlHttp = new XMLHttpRequest(); 
xmlHttp.open('GET','demo.php','true'); 
xmlHttp.send() 
xmlHttp.onreadystatechange = function(){ 
   if(xmlHttp.readyState === 4 & xmlHttp.status === 200){ 
   } 
} 
```



### 3.如何判断一个数据是NaN

### 4.Js中null与undefined区别

Null 只有一个值，是 null。不存在的对象。

  Undefined 只有一个值，是undefined。没有初始化。undefined 是从 null 中派生出来的。

  简单理解就是：undefined 是没有定义的，null 是定义了但是为空。

### 5.闭包是什么有什么特性，对页面会有什么影响

 

闭包可以简单理解成“定义在一个函数内部的函数“。当其中一个内部函数在包含它们的外部函数之外被调用时，就会形成闭包。

特点：

1.函数嵌套函数。

2.函数内部可以引用外部的参数和变量。

3.参数和变量不会被垃圾回收机制回收。

用处
 常驻内存 会增大内存的使用量 使用不：

1.读取函数内部的变量；

 2.这些变量的值始终保持在内存中，不会在外层函数调用后被自动清除。

优点：1:变量长期驻扎在内存中；

​      2:避免全局变量的污染；

​      3:私有成员的存在 ；

缺点：

当会造成内存泄露

###  6.事件委托是什么？如何确定事件源

事件委托还有一个名字叫事件代理，JS高程上讲：事件委托就是利用事件冒泡，只制定一个时间处理程序，就可以管理某一类型的所有事件。

### 7.本地存储与cookie的区别

Cookie 是小甜饼的意思。顾名思义，cookie 确实非常小，它的大小限制为4KB左右。它的主要用途有保存登录信息，比如你登录某个网站市场可以看到“记住密码”，这通常就是通过在 Cookie 中存入一段辨别用户身份的数据来实现的。

### 8.localStorage

localStorage 是 HTML5 标准中新加入的技术，它并不是什么划时代的新东西。早在 IE 6 时代，就有一个叫 userData 的东西用于本地存储，而当时考虑到浏览器兼容性，更通用的方案是使用 Flash。而如今，localStorage 被大多数浏览器所支持，如果你的网站需要支持 IE6+，那以 userData 作为你方案是种不错的选择。

### 9.sessionStorage

sessionStorage 与 localStorage 的接口类似，但保存数据的生命周期与 localStorage 不同。做过后端开发的同学应该知道 Session 这个词的意思，直译过来是“会话”。而 sessionStorage 是一个前端的概念，它只是可以将一部分数据在当前会话中保存下来，刷新页面数据依旧存在。但当页面关闭后，sessionStorage 中的数据就会被清空。