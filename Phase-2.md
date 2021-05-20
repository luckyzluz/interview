### 1.Js基本数据类型有哪些

7种。`Number`、`String`、`Boolean`、`Null`、`undefined`、`object`、`symbol`。

> 在ES5的时候，我们认知的数据类型是前6种。
>
> ES6 中新增了一种 `Symbol` 。这种类型的对象永不相等，即始创建的时候传入相同的值，可以解决属性名冲突的问题，做为标记。
>

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

**隐式原型(_proto_):**上面说的这个原型是JavaScript中的内置属性[[prototype]]，此属性继承自object对象，在脚本中没有标准的方式访问[[prototype]]，但Firefox、Safari和Chrome在每个对象上都支持一个属性_proto_，隐式原型的作用是用来构成原型链，实现基于原型的继承
**显示原型(prototype):**每一个函数在创建之后，便会拥有一个prototype属性，这个属性指向函数的原型对象，显示原型的作用是用来实现基于原型的继承与属性的共享

**原型链:**原型链是原型对象创建过程的历史记录，当访问一个对象的某个属性时，会先在这个对象本身属性上查找，如果没有找到，则会去它的__proto__隐式原型上查找，即它的构造函数的prototype，如果还没有找到就会再在构造函数的prototype的__proto__中查找，这样一层一层向上查找就会形成一个链式结构

1）原型链解决的主要是继承问题
2）每个对象拥有一个原型对象，通过 proto 指针指向其原型对象，并从中继承方法和属性，同时原型对象也可能拥有原型，这样一层一层，最终指向 null(Object.proptotype.__proto__指向的是null)。这种关系被称为原型链(prototype chain)，通过原型链一个对象可以拥有定义在其他对象中的属性和方法
3）构造函数 Parent、Parent.prototype 和 实例 p 的关系如下:(p.__proto__ === Parent.prototype)

### 15.Promise的理解  

Promise 是异步编程的一种解决方案：从语法上讲，promise是一个对象，从它可以获取异步操作的消息；从本意上讲，它是承诺，承诺它过一段时间会给你一个结果。promise有三种状态： pending(等待态)，resolved(成功态)，rejected(失败态)；状态一旦改变，就不会再变。创造promise实例后，它会立即执行。
 即使在我短短的编程生涯中，需要使用到的promise也是十分多的，在需要用到异步处理并且需要回调值时，但是promise本身并不是异步的。

### 16.Promise在哪里使用过

加载图片，ajax请求，vue接口请求

### 17.请简述async的用法

**(1)async函数的基本形式**

```javascript
//函数声明
async function foo() {}
//函数表达式
const foo = async function () {};
//对象的方法
let obj = { async foo() {} };
obj.foo().then(...)
//Class 的方法
class Storage {
constructor() {
    this.cachePromise = caches.open('avatars');
}
async getAvatar(name) {
    const cache = await this.cachePromise;
    return cache.match(`/avatars/${name}.jpg`);
}
}
const storage = new Storage();
storage.getAvatar('jake').then(…);
//箭头函数
const foo = async () => {};
```

**(2) async函数的返回值总是一个Promise**

无论async函数有无await操作，其总是返回一个Promise。

1. 没有显式return，相当于return Promise.resolve(undefined);
2. return非Promise的数据data，相当于return Promise.resolve(data);
3. return Promise, 会得到Promise对象本身

async总是返回Promise，因此，其后面可以直接调用then方法，
函数内部return返回的值，会成为then回调函数的参数
函数内部抛出的错误，会被then的第二个函数或catch方法捕获到

```javascript
//正常返回值
async function f(){
    retrun 'hello world';
}
f().then(v => console.log(v));//hello world
//抛出错误
async function f(){
    throw new Error('出错了');
}
f().then(
    v => console.log(v),
    e => console.log(e) //Error: 出错了
)
```

### 18.jQuery相关的知识

 见jquery

 

### 19.Css预处理sass less是什么？为什么使用他们

Sass 和 LESS 都是是 CSS 预处理器，是 CSS 上的一种抽象层，是一种特殊的 语法/语言 最终会编译成 CSS

less 是一种动态样式语言，将 CSS 赋予了动态语言的特性，如变量，继承，运算， 函数.。less 既可以在客户端上运行 (支持 IE 6+, Webkit, Firefox)，也可一在服务端运行(需要借助 Node.js)。

1. **为什么要使用它们？**
   结构清晰，便于扩展。
2. 可以方便地屏蔽浏览器私有语法差异。这个不用多说，封装对浏览器语法差异的重复处理，
   减少无意义的机械劳动。

3. 可以轻松实现多重继承。

4. 完全兼容 CSS 代码，可以方便地应用到老项目中。LESS 只是在 CSS 语法上做了扩展，所
   以老的 CSS 代码也可以与 LESS 代码一同编译。

### 20.Js中.call()与.apply()区别

`apply`接受两个参数，第一个参数指定了函数体内`this`对象的指向，第二个参数为一个带下标的集合，这个集合可以为数组，也可以为类数组，

`apply`方法把这个集合中的元素作为参数传递给被调用的函数。

```javascript
let func = function(a,b,c){
    console.log([a,b,c])
}
func.apply(null,[1,2,3])  // [1,2,3]
```

`call`传入的参数数量不固定，跟`apply`相同的是，第一个参数也是代表函数体内的`this`指向，从第二个参数开始往后，每个参数被依次传入函数

```javascript
let func = function(a,b,c){
    console.log([a,b,c])
}
func.call(null,3,4,5) // [3,4,5]
```

### 21.为什么会造成跨域/请简述同源策略

**为什么会造成跨域**

因为浏览器的同源政策，就会产生跨域。比如说发送的异步请求是不同的两个源，就比如是不同的的两个端口或者不同的两个协议或者不同的域名。由于浏览器为了安全考虑，就会产生一个同源政策，不是同一个地方出来的是不允许进行交互的。

**简述同源策略**

同源策略是客户端脚本（尤其是Javascript）的重要的安全度量标准。它最早出自Netscape Navigator2.0，其目的是防止某个文档或脚本从多个不同源装载。
这里的同源策略指的是：协议，域名，端口相同，同源策略是一种安全协议。
指一段脚本只能读取来自同一来源的窗口和文档的属性。

### 22.This指向

1. 如果一个函数中有this，但是它没有被上一级的对象所调用，那么this指向的就是window，这里需要说明的是在js的严格版中this指向的不是window，但是我们这里不探讨严格版的问题，你想了解可以自行上网查找。
2. 如果一个函数中有this，这个函数有被上一级的对象所调用，那么this指向的就是上一级的对象。
3. 一个函数中有this，这个函数中包含多个对象，尽管这个函数是被最外层的对象所调用，this指向的也只是它上一级的对象。

### 23.请输出三种减少页面加载时间的方式

1. 优化图片 
2. 图像格式的选择（GIF：提供的颜色较少，可用在一些对颜色要求不高的地方）
3. 优化CSS（压缩合并css，如margin-top,margin-left...)
4. 网址后加斜杠，对服务器而言，不加斜杠服务器会多一次判断的过程，加斜杠就会直接返回网站设置的存放在网站根目录下的默认页面。
5. 标明高度和宽度（如果浏览器没有找到这两个参数，它需要一边下载图片一边计算大小，如果图片很多，浏览器需要不断地调整页面。这不但影响速度，也影响浏览体验。 当浏览器知道了高度和宽度参数后，即使图片暂时无法显示，页面上也会腾出图片的空位，然后继续加载后面的内容。从而加载时间快了，浏览体验也更好了。）
6. 减少http请求（合并文件，合并图片）。

### 24.什么是jsonp，工作原理是什么？他为什么不是真正的ajax

**Jsonp其实就是一个跨域解决方案。**

**jsonp的原理**:就是利用浏览器可以动态地插入一段js并执行的特点完成的。

**为什么不是真正的 ajax?**   

**ajax的核心**：通过`XmlHttpRequest`获取非本页内容，

**jsonp的核心**：动态添加`<script>`标签来调用服务器提供的js脚本。

**相同点：**

ajax和jsonp的调用方式很像，目的一样，都是请求url，然后把服务器返回的数据进行处理，因此jquery和ext等框架都把jsonp作为ajax的一种形式进行了封装；

**不同点：**

1. 实质不同
   　ajax的核心是通过xmlHttpRequest获取非本页内容
      　jsonp的核心是动态添加script标签调用服务器提供的js脚本
2. ajax通过服务端代理一样跨域
   　jsonp也不并不排斥同域的数据的获取
3. jsonp是一种方式或者说非强制性的协议
   　ajax也不一定非要用json格式来传递数据　
4. jsonp只支持get请求，ajax支持get和post请求

### 25.请掌握2种以上数组去重的方式

```javascript
let originalArray = [1,2,3,4,5,3,2,4,1];
```

**方式1：(ES6的Set集合)**

```javascript
const result = Array.from(new Set(originalArray));
console.log(result); // -> [1, 2, 3, 4, 5]
```

**方式2:(map集合)**

```javascript
const result = [];
const map = new Map();
for (let v of originalArray) {
    if (!map.has(v)) {
        map.set(v, true);
        result.push(v);
    }
}
console.log(result); // -> [1, 2, 3, 4, 5]
```

**方式3:(Includes)**

```javascript
const result = [];
for (let v of originalArray) {
    if (!result.includes(v)) {
        result.push(v);
    }
}
console.log(result); // -> [1, 2, 3, 4, 5]
```

**方式4:(前后对比)**

```javascript
for (let i = 0; i < originalArray.length; i++) {
    for (let j = i + 1; j < originalArray.length; j++) {
        if (originalArray[i] === originalArray[j]) {
            originalArray.splice(j, 1);
            j--;
        }
    }
}
console.log(originalArray); // -> [1, 2, 3, 4, 5]
```

**方式5:(Filter过滤器)**

```javascript
const obj = {};
const result = originalArray.filter(item => obj.hasOwnProperty(typeof item + item) ? false:(obj[typeof item + item] = true));
console.log(result); // -> [1, 2, 3, 4, 5]
```

### 26.深浅拷贝是什么,如何实现？

**浅拷贝**子对象复制父对象，父子对象发生关联，两者属性值指向同一内存空间。简单来讲，就是改变其中一个对象，另一个对象也会跟着改变。

```javascript
let a = [0,1,2],b = a;
a[0] = 3;
console.log(a,b) // [3,1,2] [3,1,2]
```

**深拷贝**拷贝对象各个层级的属性。简单的讲，就是复制出来的每个对象都有属于自己的内存空间，不会互相干扰。

**借用JSON对象的 parse 和 stringify**

```javascript
function deepClone(obj){
    let newObj = JSON.stringify(obj);
    let objClone = JSON.parse(newObj);
    return objClone;
}
let a=[0,1,[2,3],4],
    b=deepClone(a);
a[0]=1;
a[2][0]=1;
console.log(a,b);
```

### 27.为什么js是弱类型语言

**弱类型语言**是相对强类型语言来说的。

在强类型语言中，变量类型有多种，例如`int` `char` `float` `boolean` 等不同的类型相互转换有时需要强制转换而javascript只有一种类型`var`，为变量赋值时会自动判断类型并进行转换所以javascript是弱语言就体现在变量定义类型var上了 

### 28.怎么转换less为css

**Less** 是一门 CSS 预处理语言，它扩充了 CSS 语言，增加了诸如变量、混合（mixin）、函数等功能，让 CSS 更易维护、方便制作主题、扩充。

1. 首先，你要确认你的电脑已经安装了node。
2. 使用 npm 安装 lessc，命令行：
   `npm install -g less`
3. 然后，进入需要转换的less文件的目标位置。
4. 最后，你只需输入以下两条命令：

```cmd
npm install -g less
lessc less文件名.less 生成的css文件名.css
```

### 29.echarts使用最多的是什么

> ​		商业级数据图表，它是一个纯JavaScript的图标库，兼容绝大部分的浏览器，底层依赖轻量级的canvas类库ZRender，提供直观，生动，可交互，可高度个性化定制的数据可视化图表。创新的拖拽重计算、数据视图、值域漫游等特性大大增强了用户体验，赋予了用户对数据进行挖掘、整合的能力。

**折线图（区域图）、柱状图（条状图）、散点图（气泡图）、K线图、饼图（环形图）**

**雷达图（填充雷达图）**

### 30.For循环与map循环有什么区别

**map方法**
1.map方法**返回一个新的数组**，数组中的元素为原始数组调用函数处理后的值。
2.map方法不会对空数组进行检测，map方法不会改变原始数组。



### 31.请写出一个简单的类与继承

### 32.同步与异步的区别/阻塞与非阻塞区别

### 33.重绘和回流是什么

引起DOM树结构变化，页面布局变化的行为叫回流，且回流一定伴随重绘。

只是样式的变化，不会引起DOM树变化，页面布局变化的行为叫重绘，且重绘不一定会便随回流。

### 34.http是什么？有什么特点



### 35.HTTP协议和HTTPS区别

### 36.原型和继承，prototype，call和apply继承的区别（第一个参数是相同的，第二个的区别在哪）

### 37.数组的方法，字符串的方法，要知道每个的含义，掌握排序和去重的方法

### 38.箭头函数与普通函数的区别

**一.外形不同**：箭头函数使用箭头定义，普通函数中没有
代码实例如下：

**二.箭头函数都是匿名函数**
普通函数可以有匿名函数，也可以有具体名函数，但是箭头函数都是匿名函数。
代码实例如下：

**三.箭头函数不能用于构造函数，不能使用new**
普通函数可以用于构造函数，以此创建对象实例。
代码实例如下：

**四.箭头函数中this的指向不同**
在普通函数中，this总是指向调用它的对象，如果用作构造函数，this指向创建的对象实例。
1.箭头函数本身不创建this
也可以说箭头函数本身没有this，但是它在声明时可以捕获其所在上下文的this供自己使用。
注意：this一旦被捕获，就不再发生变化

### 39.什么是js内存泄露？

 指由于疏忽或者错误造成程序未能释放已经不再使用的内存，从而造成内存上的浪费。

### 40.你如何对网站的文件和资源进行优化？

### 41.请简述ajax的执行过程 以及常见的HTTP状态码



### 42.预加载和懒加载的区别，预加载在什么时间加载合适

 预加载是指在页面加载完成之前，提前将所需资源下载，之后使用的时候从缓存中调用；懒加载是延迟加载，按照一定的条件或者需求等到满足条件的时候再加载对应的资源

预加载增加了服务器压力，换来的是用户体验的提升，典型例子是在一个图片较多的网页中，如果使用了预加载就可以避免网页加载出来是时，图片的位置一片空白（图片可能还没加载出来），造成不好的用户体验；懒加载的作用减少不要的请求，缓解了服务器压力

懒加载的原理

原理：原理很简单，先把img的src指向空或者一个小图片，图片真实的地址存储在img一个自定义的属性里,`< img src=”” data-src=”http://real.com/real.jpg” />`,等到此图片出现在视野范围内了，获取img元素，把data-src里的值赋给src。这样做能防止页面一次性向服务器响应大量请求导致服务器响应慢，页面卡顿或崩溃等问题。

优点：页面加载速度快、可以减轻服务器的压力、节约了流量,用户体验好

预加载的原理

提前加载图片，当用户需要查看时可直接从本地缓存中渲染

意义：预加载可以说是牺牲服务器前端性能，换取更好的用户体验，这样可以使用户的操作得到最快的反映。

### 43.Jquery选择器有哪些

### 44.Jquery插入节点的方法

`append()`:向每个匹配的元素内部追加内容

`prepend()`: 向每个匹配的元素内部前置内容

`appendTo()`: 将所有匹配的元素追加到指定元素中，实际上，使用该方法是颠倒了常规的$(A).append(B)的操作，即不是将B追加到A中，而是将A追加到B中

`prependTo()`: 将所有匹配的元素前置到指定的元素中。实际上，使用该方法是颠倒了常规的$(A).prepend(B)的操作，即不是将B前置到A中，而是将A前置到B中

`after()`:在每个匹配的元素之后插入内容

`insertAfter()`:将所有匹配的元素插入到指定元素的后面。实际上，使用该方法是颠倒了常规的$(A).after(B)的操作，即不是讲B插入到A后面，而是将A插入到B后面

`before()`	在每个匹配的元素之前插入内容

`insertBefore()`:将所有匹配的元素插入到指定的元素的前面。实际上，使用该方法是颠倒了常规的$(A).before(B)的操作，即不是将B插入到A前面，而是将A插入到B前面

### 45.Js的函数节流和函数防抖的区别

**函数节流**是指一定时间内js方法只跑一次。比如人的眨眼睛，就是一定时间内眨一次。这是函数节流最形象的解释。

函数节流应用的**实际场景**，多数在监听页面元素滚动事件的时候会用到。因为滚动事件，是一个高频触发的事件。以下是监听页面元素滚动的示例代码：

```javascript
// 函数节流
var canRun = true;
document.getElementById("throttle").onscroll = function(){
    if(!canRun){
        // 判断是否已空闲，如果在执行中，则直接return
        return;
    }

   canRun = false;
   setTimeout(function(){
       console.log("函数节流");
       canRun = true;
   }, 300);
};
```

函数节流的**要点**是，声明一个变量当标志位，记录当前代码是否在执行。
 如果空闲，则可以正常触发方法执行。
 如果代码正在执行，则取消这次方法执行，直接return。

**函数防抖**是指频繁触发的情况下，只有足够的空闲时间，才执行代码一次。比如生活中的坐公交，就是一定时间内，如果有人陆续刷卡上车，司机就不会开车。只有别人没刷卡了，司机才开车。

函数防抖的**应用场景**，最常见的就是用户注册时候的手机号码验证和邮箱验证了。只有等用户输入完毕后，前端才需要检查格式是否正确，如果不正确，再弹出提示语。以下还是以页面元素滚动监听的例子，来进行解析：

```javascript
// 函数防抖
var timer = false;
document.getElementById("debounce").onscroll = function(){
 clearTimeout(timer); // 清除未执行的代码，重置回初始化状态

timer = setTimeout(function(){
    console.log("函数防抖");
}, 300);
};  
```

函数防抖的**要点**，也是需要一个setTimeout来辅助实现。延迟执行需要跑的代码。
 如果方法多次触发，则把上次记录的延迟执行代码用clearTimeout清掉，重新开始。
 如果计时完毕，没有方法进来访问触发，则执行代码。

### 46.Get和post不同

| 请求方式区别 |                             get                              |                             post                             |
| ------------ | :----------------------------------------------------------: | :----------------------------------------------------------: |
| 用途         |                       从服务器获取数据                       |                       向服务器提交数据                       |
| 参数传递     |          参数拼接在URL上，xxx?id=1234&name=zhagnsan          |             参数封装在消息主体中一起提交到服务器             |
| 传输数据量   | 传送的数据量较小，不能大于2KB（URL 的最大长度是 2048 个字符）。 |             参数封装在消息主体中一起提交到服务器             |
| 安全性       | 与 POST 相比，GET的安全性较差，因为所发送的数据是 URL 的一部分。(在发送密码或其他敏感信息时绝不要使用 GET ) | POST 比 GET 更安全，因为参数不会被保存在浏览器历史或 web 服务器日志中。 |
| 书签         |                         可收藏为书签                         |                        不可收藏为书签                        |
| 缓存         |                           能被缓存                           |                           不能缓存                           |
| 编码类型     |              application/x-www-form-urlencoded               | application/x-www-form-urlencoded 或 multipart/form-data。为二进制数据使用多重编码 |
| 历史         |                    参数保留在浏览器历史中                    |                  参数不会保存在浏览器历史中                  |
| 可见性       |                数据在URL中对所有人都是可见的                 |                     数据不会显示在URL中                      |



### 47.什么是csrf攻击

CSRF（Cross-site request forgery）也被称为 one-click attack或者 session riding，中文全称是叫**跨站请求伪造**。

一般来说，攻击者通过伪造用户的浏览器的请求，向访问一个用户自己曾经认证访问过的网站发送出去，使目标网站接收并误以为是用户的真实操作而去执行命令。常用于盗取账号、转账、发送虚假消息等。攻击者利用网站对请求的验证漏洞而实现这样的攻击行为，网站能够确认请求来源于用户的浏览器，却不能验证请求是否源于用户的真实意愿下的操作行为。

### 48.Js数据类型的分类

 **基本数据类型 （值类型）**
  +  数字number
  +  字符串string
  +  布尔 boolean
  +  null
  +  undefined

  **引用数据类型**
  对象object

函数function

### 49.Js中手写一个深拷贝

1、数组中map方法通过制定函数对数组进行操作，并将处理结果返回，不会修改原数组，结果以新数组的形式返回，不会修改原数组
            

```javascript
//深拷贝
            let obj=[1,2,3,4,5,6]
            let newobj=obj.map(function(itme,index){
                //给obj的每一项加一
                return itme+1
            })
            let newobjb=obj
            console.log(obj)// [1, 2, 3, 4, 5, 6]
            //深拷贝
            console.log(newobj)//[2, 3, 4, 5, 6, 7]
```

2、将数组先转成JSON字符串，再转成JSON对象，实现深拷贝。
            

```javascript
let objc=[1,2,3,4]
            let objv=JSON.parse(JSON.stringify(objc))
            console.log(objc)
            objv.push(100)//[1, 2, 3, 4]
            console.log(objv)//[1, 2, 3, 4, 100]
```



### 50.什么时候用深拷贝 /浅拷贝

无论深浅，都是需要的。当深拷贝发生时，通常表明存在着一个“聚合关系”，而浅拷贝发生时，通常表明存在着一个“相识关系”。  
举个简单的例子：  
当你实现一个Composite  Pattern，你通常都会实现一个深拷贝(如果需要拷贝的话)，很少有要求同的Composite共享Leaf的；  
而当你实现一个Observer  Pattern时，如果你需要拷贝Observer,你大概不会去拷贝Subject，这时就要实现个浅拷贝。  
是深拷贝还是浅拷贝，并不是取决于时间效率、空间效率或是语言等等，而是取决于哪一个是逻辑上正确的。  

### 51.如何遍历一个多维数组

```javascript
        //遍历多维数组
            var newarr =[] ;
            function demo(arr){
                for(let i=0;i<arr.length;i++){
                    if(typeof arr[i] !=="object"){
                        console.log(arr[i])
                        newarr.push(arr[i])
                    }else{
                        demo(arr[i])
                    }
                }
                return newarr
            }
            console.log(demo([1,2,3,4,[5],[6,7,[8,9,[10,11]]]]))//[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11]
```

