### 1.Js基本数据类型有哪些

7种。`Number`、`String`、`Boolean`、`Null`、`undefined`、`object`、`symbol`。

> 在ES5的时候，我们认知的数据类型是前6种。
>
> ES6 中新增了一种 `Symbol` 。这种类型的对象永不相等，即始创建的时候传入相同的值，可以解决属性名冲突的问题，做为标记。

------

### 2.Ajax如何使用

> **全称：**`Asynchronous Javascript And XML`(异步传输+js+xml)。
> 所谓**异步**，在这里简单地解释就是：向服务器发送请求的时候，我们不必等待结果，而是可以同时做其他的事情，等到有了结果它自己会根据设定进行后续操作，与此同时，页面是**不会**发生整页刷新的，提高了用户体验

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
       console.log(xhr.responseText);
   } 
} 
```

------

### 3.如何判断一个数据是NaN

**注意：**NaN首先是一个`number`类型，然后同时又有着`not a number`的意义，而不仅仅只是表达着`不是"number类型"`

关于NaN的一些操作：

**1.isNaN(n)**

```javascript
let a  = NaN 
console.log(isNaN(a))  // true
```

**2.Object.is(n)**

```javascript
let a  = NaN
console.log(Object.is(a,NaN)) // true
```

**3.封装成方法：NaN连自己本身都不相等，所以可以利用这个特性来判断这个值是不是NaN**

```javascript
 let isNaNMethod = v=>v!==v && true 
    console.log(isNaNMethod(NaN)); // true
    console.log(isNaNMethod('sdsd')); // false
    console.log(isNaNMethod(3)); // false
    console.log(isNaNMethod('3.233')); // false
    let bq = {name:'zs'}
    console.log(isNaNMethod(bq)); // false
```

**4.判断数组中是否含有NaN**

```javascript
let arr = [1,2,3,NaN]
console.log(arr.includes(NaN))  // true
```

**注意：不能用indexOf判断数组中是否含有NaN**

------

### 4.Js中null与undefined区别

**Null** 只有一个值，是 null，代表一个`空对象指针`。

**Undefined** 只有一个值，是undefined。

当一个声明了一个变量未初始化时，得到的就是undefined。undefined 是从 null 中派生出来的。

**简单理解**就是：undefined 是没有定义的，null 是定义了但是为空。

------

### 5.闭包是什么?有什么特性?对页面会有什么影响?

闭包可以简单理解成"定义在一个函数内部的函数"。`当其中一个内部函数在包含它们的外部函数之外被调用`时，就会形成闭包。

**特点：**

1. 函数嵌套函数。
2. 函数内部可以引用外部的参数和变量。
3. 参数和变量不会被垃圾回收机制回收。

**用处**
 常驻内存 会增大内存的使用量 使用不：

1. 读取函数内部的变量；
2. 这些变量的值始终保持在内存中，不会在外层函数调用后被自动清除。

**优点：**

1. 变量长期驻扎在内存中；
2. 避免全局变量的污染；
3. 私有成员的存在 ；

**缺点：**

会造成内存泄露

###  6.事件委托是什么？如何确定事件源

事件委托还有一个名字叫事件代理，JS高程上讲：事件委托就是利用事件冒泡，只制定一个时间处理程序，就可以管理某一类型的所有事件。

**在事件中，当前操作的那个元素就是事件源。**比如网页元素中a标签和input都有onclick事件，当点击a发生onclick事件时，事件源就是a标签，当点击input发送onclic事件是，事件源就是input。

**如何获取事件源那？？**

> IE下：window.event.srcElement 
>
> 标准下：event.target

由此可见，我们是通过事件对象获取到的事件源。

------

### 7.本地存储与cookie的区别

**1.Cookie** 

是小甜饼的意思。顾名思义，cookie 确实非常小，它的大小限制为4KB左右。它的主要用途有保存登录信息，比如你登录某个网站市场可以看到“记住密码”，这通常就是通过在 Cookie 中存入一段辨别用户身份的数据来实现的。

**2.localStorage**

localStorage 是 HTML5 标准中新加入的技术，它并不是什么划时代的新东西。早在 IE 6 时代，就有一个叫 userData 的东西用于本地存储，而当时考虑到浏览器兼容性，更通用的方案是使用 Flash。而如今，localStorage 被大多数浏览器所支持，如果你的网站需要支持 IE6+，那以 userData 作为你方案是种不错的选择。

**3.sessionStorage**

sessionStorage 与 localStorage 的接口类似，但保存数据的生命周期与 localStorage 不同。做过后端开发的同学应该知道 Session 这个词的意思，直译过来是“会话”。而 sessionStorage 是一个前端的概念，它只是可以将一部分数据在当前会话中保存下来，刷新页面数据依旧存在。但当页面关闭后，sessionStorage 中的数据就会被清空。

**三者的异同**

| ***特性***     | **Cookie**                                                   | **localStorage**                                            | **sessionStorage**                           |
| -------------- | ------------------------------------------------------------ | ----------------------------------------------------------- | -------------------------------------------- |
| 数据的生命期   | 一般由服务器生成，可设置失效时间。如果在浏览器端生成Cookie，默认是关闭浏览器后失效 | 除非被清除，否则永久保存                                    | 仅在当前会话下有效，关闭页面或浏览器后被清除 |
| 存放数据大小   | 4K左右                                                       | 一般为5MB                                                   |                                              |
| 与服务器端通信 | 每次都会携带在HTTP头中，如果使用cookie保存过多数据会带来性能问题 | 仅在客户端（即浏览器）中保存，不参与和服务器的通信          |                                              |
| 易用性         | 需要程序员自己封装，源生的Cookie接口不友好                   | 源生接口可以接受，亦可再次封装来对Object和Array有更好的支持 |                                              |

**相同点：**都保存在浏览器端，同源的

**不同点：**

①传递方式不同

cookie数据始终在同源的http请求中携带（即使不需要），即cookie在浏览器和服务器间来回传递。

sessionStorage和localStorage不会自动把数据发给服务器，仅在本地保存。

②数据大小不同

cookie数据还有路径（path）的概念，可以限制cookie只属于某个路径下。

存储大小限制也不同，cookie数据不能超过4k，同时因为每次http请求都会携带cookie，所以cookie只适合保存很小的数据，如会话标识。

sessionStorage和localStorage 虽然也有存储大小的限制，但比cookie大得多，可以达到5M或更大。

③数据有效期不同

sessionStorage：仅在当前浏览器窗口关闭前有效，自然也就不可能持久保持；

localStorage：始终有效，窗口或浏览器关闭也一直保存，因此用作持久数据；

cookie只在设置的cookie过期时间之前一直有效，即使窗口或浏览器关闭。

④作用域不同

sessionStorage不在不同的浏览器窗口中共享，即使是同一个页面；

localStorage 在所有同源窗口中都是共享的；

cookie也是在所有同源窗口中都是共享的。

Web Storage 支持事件通知机制，可以将数据更新的通知发送给监听者。

Web Storage 的 api 接口使用更方便。

### 8.ES6新特性

***const和let***

***模板字符串***

***箭头函数***

***函数的参数默认值***

***对象和数组解构***

***for...of 和 for...in***

***ES6中的类***

### 9.Let与var与const的区别

**var声明的变量会挂载在window上,而let和const声明的变量不会;**

**声明变量存在变量提升,let和const不存在变量提升**

**let和const声明形成块作用域**

**同一作用域下let和const不能声明同名变量,而var可以**

**let暂存死区**

------

### 10.数组方法有哪些请简述

***arr.push()*** ***从后面添加元素，返回值为添加完后的数组的长度***

***arr.pop()*** ***从后面删除元素，只能是一个，返回值是删除的元素***

***arr.shift()*** ***从前面删除元素，只能删除一个 返回值是删除的元素***

***arr.unshift()*** ***从前面添加元素, 返回值是添加完后的数组的长度***

 ***arr.splice(i,n)*** ***删除从i(索引值)开始之后的那个元素。返回值是删除的元素***

***arr.concat()*** ***连接两个数组 返回值为连接后的新数组***

***str.split()*** ***将字符串转化为数组***

 ***arr.sort()*** ***将数组进行排序,返回值是排好的数组，默认是按照最左边的数字进行排序，不是按照数字大小排序的***

***arr.reverse()*** ***将数组反转,返回值是反转后的数组***

 ***arr.slice(start,end)*** ***切去索引值start到索引值end的数组，不包含end索引的值，返回值是切出来的数组***

 ***arr.forEach(callback)*** ***遍历数组,无return 即使有return，也不会返回任何值，并且会影响原来的数组***

 ***arr.map(callback)*** ***映射数组(遍历数组),有return 返回一个新数组 。***

 ***arr.filter(callback)*** ***过滤数组，返回一个满足要求的数组*** 

### 11.Json如何新增/删除键值对

(1)数据结构是Object

```javascript
var jsonStr={};
//增加
jsonStr["name1"]="yu";
jsonStr["name2"]="jin";
$.each(jsonStr,function(_key){
    console.log("Push结果："+_key+"=="+jsonStr[_key]+"\r\n");
});
//遍历
$.each(jsonStr,function(_key){
    var key = _key;
    var value = jsonStr[_key];
    if(_key=="name1")
    {  //删除
delete jsonStr[_key];
    }
});
$.each(jsonStr,function(_key){
    console.log("删除后的结果："+_key+"=="+jsonStr[_key]+"\r\n");
});
```

(2)数据结构是Array

```javascript
var str = '[{"name":"aa","age":"23"}]';
var array=JSON.parse(str);
//新增
array.push({"name":"dd","age":"25"});
//修改
var obj=array.firstOrDefault(
function(x){
return x.name=='bb';
}
);
obj.age=25;
//删除
array.delete(
function(x){
return x.name=='cc';
}
);
//转为json字符串
str=JSON.stringify(array);
```

------

### 12.什么是面向对象请简述

首先，我们要明确，**面向对象**不是语法，是一个思想，是一种编程模式
**面向过程(POP)：**关注点在于做了什么，描述的是发展的过程。
**面向对象(OOP)：**关注点在于能做什么，描述的是对象与对象之间的关系。
面向对象的**特点**：继承、多态、封装

总而言之，差不多就是老板不会管这个目标用什么技术方法实现，交给你完成就对了。

------

### 13.普通函数和构造函数去的区别

**构造函数:**如用函数用来初始化(使用new运算符)一个新建的对象，我们称之为构造函数(constructor)

**普通函数:**不使用new运算符的函数就是普通函数

1. 构造函数也是一个普通函数，创建方式和普通函数一样，但构造函数习惯上**首字母大写**

2. 构造函数和普通函数的区别在于：调用方式不一样。作用也不一样（**构造函数用来新建实例对象**）

3. 调用方式不一样。

   a. 普通函数的调用方式：**直接调用** `person()`;
   b.构造函数的调用方式：**需要使用new关键字来调用** `new Person()`;

4. 构造函数的函数名与类名相同：`Person()` 这个构造函数，`Person` 既是函数名，也是这个对象的类名

5. 构造函数内部可以使用`this`关键字；**普通函数内部不建议使用**`this`，因为这时候**this指向的是window全局对象**，这样无意间就会为window添加了一些全局变量或函数

   ```javascript
   function Person(name,job,age)
   {
        this.name=name;
        this.job=job;
        this.age=age;
        this.sayHi=function()
            {
             alert("Hi")
            }
    } 
   ```

6. 构造函数的执行流程

   A、立刻在堆内存中创建一个新的对象`var p = {};`

   B、将新建的对象设置为函数中的this

   C、逐个执行函数中的代码

   D、将新建的对象作为返回值

7. 普通函数例子：因为没有返回值，所以为undefined

   ```javascript
   //普通函数
   function person(){
   var per = person(); 
   consoLe.log(per);//undefined
   ```

8. 构造函数例子：构造函数会马上创建一个新对象，并将该新对象作为返回值返回

   ```javascript
   //构造函数
   function Person(){
   var per = new Person();
   console.log(per);//[object object]
   ```

9. 用instanceof 可以检查一个对象是否是一个类的实例，是则返回true；

   ```javascript
   //构造函数
   function Person (name , age , gender){
   //往对象中添加属性和属性值
   this.name = name ;
   this.age = age;
   this.gender = gender
   var per = new Person("张三”,18,"男");
   console.log(per);//[object object]  马上创建一个对象
   console.log(per.name);//"张三”
   console.log(per.age);//"18"
   console.log(per instanceof Person);//"true" per为Person函数的实例，返回true
   ```

所有对象都是Object对象的后代，所以任何对象和Object做instanceof都会返回true

------

### 14.请简述原型/原型链/继承

**原型**：一个可以被复制（或者叫克隆）的一个类，通过复制原型可以创建一个一模一样的新对象，也可以说原型就是一个模板，在设计语言中更准确的说是一个对象模板

> 在 JavaScript 中，每当定义一个对象（函数也是对象）时候，对象中都会包含一些预定义的属性。其中每个函数对象都有一个prototype 属性，这个属性指向函数的原型对象，使用原型对象的好处是所有对象实例共享它所包含的属性和方法

**隐式原型（_proto_）：**上面说的这个原型是JavaScript中的内置属性[[prototype]]，此属性继承自object对象，在脚本中没有标准的方式访问[[prototype]]，但Firefox、Safari和Chrome在每个对象上都支持一个属性_proto_，隐式原型的作用是用来构成原型链，实现基于原型的继承
**显示原型（prototype）：**每一个函数在创建之后，便会拥有一个prototype属性，这个属性指向函数的原型对象，显示原型的作用是用来实现基于原型的继承与属性的共享

**原型链：**原型链是原型对象创建过程的历史记录，当访问一个对象的某个属性时，会先在这个对象本身属性上查找，如果没有找到，则会去它的__proto__隐式原型上查找，即它的构造函数的prototype，如果还没有找到就会再在构造函数的prototype的__proto__中查找，这样一层一层向上查找就会形成一个链式结构

1）原型链解决的主要是继承问题
2）每个对象拥有一个原型对象，通过 proto 指针指向其原型对象，并从中继承方法和属性，同时原型对象也可能拥有原型，这样一层一层，最终指向 null(Object.proptotype.__proto__指向的是null)。这种关系被称为原型链(prototype chain)，通过原型链一个对象可以拥有定义在其他对象中的属性和方法
3）构造函数 Parent、Parent.prototype 和 实例 p 的关系如下:(p.__proto__ === Parent.prototype)



### 15.Promise的理解                    

### 16.Promise在哪里使用过

### 17.请简述async的用法

### 18.***jQuery相关的知识***

 

 

### 19.Css预处理sass less是什么？为什么使用他们

### 20.Js中.call()与.apply()区别

### 21.为什么会造成跨域/请简述同源策略

### 22.This指向

1. 如果一个函数中有this，但是它没有被上一级的对象所调用，那么this指向的就是window，这里需要说明的是在js的严格版中this指向的不是window，但是我们这里不探讨严格版的问题，你想了解可以自行上网查找。
2. 如果一个函数中有this，这个函数有被上一级的对象所调用，那么this指向的就是上一级的对象。
3. 一个函数中有this，这个函数中包含多个对象，尽管这个函数是被最外层的对象所调用，this指向的也只是它上一级的对象。

### 23.请输出三种减少页面加载时间的方式

什么是jsonp工作原理是什么？他为什么不是真正的ajax

请掌握2种以上数组去重的方式

深浅拷贝是什么如何实现？

为什么js是弱类型语言

怎么转换less为css

echarts使用最多的是什么

For循环与map循环有什么区别

请写出一个简单的类与继承

同步与异步的区别/阻塞与非阻塞区别

重绘和回流是什么

http是什么？有什么特点

HTTP协议和HTTPS区别

原型和继承，prototype，call和apply继承的区别（第一个参数是相同的，第二个的区别在哪）

数组的方法，字符串的方法，要知道每个的含义，掌握排序和去重的方法

箭头函数与普通函数的区别

什么是js内存泄露？

 

你如何对网站的文件和资源进行优化？

请简述ajax的执行过程 以及常见的HTTP状态码

预加载和懒加载的区别，预加载在什么时间加载合适

 

Jquery选择器有哪些

Jquery插入节点的方法

Js的函数节流和函数防抖的区别

Get和post不同

什么是csrf攻击

Js数据类型的分类

Js中手写一个深拷贝

什么时候用深拷贝 /浅拷贝

如何遍历一个多维数组