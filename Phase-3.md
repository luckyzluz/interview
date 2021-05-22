## **Vue相关的**

### 1.Vue的核心是什么

**数据驱动、组件系统**

**数据驱动:**ViewModel，保证数据和视图的一致性。

**组件系统:**应用类UI可以看作全部是由组件树构成的。

### 2.请简述你对vue的理解

**简单易学**:国人开发,中文文档,不存在语言障碍,易于理解和学习

**轻量级框架**:只关注视图层,是一个构建数据的视图集合,大小只有几十kb。Vue.js通过简洁的API提供高效的数据绑定和灵活的组件系统

**双向数据绑定**:vue.js通过MVVM思想实现数据的双向绑定，让开发者不用再操作dom对象，有更多的时间去思考业务逻辑。

**视图,数据,结构分离**:使数据的更改更为简单,不需要进行逻辑代码的修改,只需要操作数据就能完成相关操作

**虚拟DOM**:传统开发中，用JQuery或者原生的JavaScript DOM操作函数对DOM进行频繁操作的时候，浏览器要不停的渲染新的DOM树，导致页面看起来非常卡顿。

> 比如:一个ul标签下有很多个li标签，其中只有一个li标签有变化，这种情况下如果使用新的ul去替代旧的ul，会因为这些不必要的DOM操作而造成性能上的浪费。

虚拟DOM在Vue.js中主要做了两件事情：

- 提供与真实DOM节点所对应的**虚拟节点VNode**
- 将虚拟节点VNode和旧虚拟节点oldVNode进行对比，然后更新视图

### 3.请简述vue的单向数据流

**单向数据流:**父级`prop`的更新会向下流动到子组件中，每次父级组件发生更新时，子组件中所有的`prop`都将会刷新为最新的值

### 4.Vue常用的修饰符有哪些

**修饰符**是用于限定类型以及类型成员的声明的一种符号

vue中修饰符分为以下五种：

1. **表单修饰符**

   填写表单的时候用得最多的是input标签，指令用得最多的是`v-model`

   关于表单的修饰符有如下：

   - **lazy:**在我们填完信息，光标离开标签的时候，才会将值赋予给value，也就是在change事件之后再进行信息同步

     ```vue
     <input type="text" v-model.lazy="value">
     <p>{{value}}</p>
     ```

   - **trim:**自动过滤用户输入的首空格字符，而中间的空格不会过滤

     ```vue
     <input type="text" v-model.trim="value">
     ```

   - **number:**自动将用户的输入值转为数值类型，但如果这个值无法被parseFloat解析，则会返回原来的值

     ```vue
     <input v-model.number="age" type="number">
     ```

2. **事件修饰符**

   **事件修饰符**是对事件捕获以及目标进行了处理，有如下修饰符：

   - **stop:**阻止了事件冒泡，相当于调用了event.stopPropagation方法

     ```vue
     <div @click="shout(2)">
       <button @click.stop="shout(1)">ok</button>
     </div>
     //只输出1
     ```

   - **prevent:**阻止了事件的默认行为，相当于调用了event.preventDefault方法

     ```vue
     <form v-on:submit.prevent="onSubmit"></form>
     ```

   - **self:**只当在 event.target 是当前元素自身时触发处理函数

     ```
     <div v-on:click.self="doThat">...</div>
     ```

     > 使用修饰符时，顺序很重要；相应的代码会以同样的顺序产生。因此，用 v-on:click.prevent.self 会阻止所有的点击，而 v-on:click.self.prevent 只会阻止对元素自身的点击

   - **once:**绑定了事件以后只能触发一次，第二次就不会触发

     ```vue
     <button @click.once="shout(1)">ok</button>
     ```

   - **capture:**使事件触发从包含这个元素的顶层开始往下触发

     ```vue
     <div @click.capture="shout(1)">
         obj1
     <div @click.capture="shout(2)">
         obj2
     <div @click="shout(3)">
         obj3
     <div @click="shout(4)">
         obj4
     </div>
     </div>
     </div>
     </div>
     // 输出结构: 1 2 4 3 
     ```

   - **passive:**在移动端，当我们在监听元素滚动事件的时候，会一直触发onscroll事件会让我们的网页变卡，因此我们使用这个修饰符的时候，相当于给onscroll事件整了一个.lazy修饰符

     ```vue
     <!-- 滚动事件的默认行为 (即滚动行为) 将会立即触发 -->
     <!-- 而不会等待 `onScroll` 完成  -->
     <!-- 这其中包含 `event.preventDefault()` 的情况 -->
     <div v-on:scroll.passive="onScroll">...</div>
     ```

     > 不要把 .passive 和 .prevent 一起使用,因为 .prevent 将会被忽略，同时浏览器可能会向你展示一个警告。
     > passive 会告诉浏览器你不想阻止事件的默认行为

   - **native:**让组件变成像html内置标签那样监听根元素的原生事件，否则组件上使用 v-on 只会监听自定义事件

   ```vue
   <my-component v-on:click.native="doSomething"></my-component>
   ```

   > 使用.native修饰符来操作普通HTML标签是会令事件失效的

3. **鼠标按键修饰符**

   鼠标按钮修饰符针对的就是左键、右键、中键点击，有如下：

   - left 左键点击
   - right 右键点击
   - middle 中键点击

   ```vue
   <button @click.left="shout(1)">ok</button>
   <button @click.right="shout(1)">ok</button>
   <button @click.middle="shout(1)">ok</button>
   ```

4. **键值修饰符**

   键盘修饰符是用来修饰键盘事件（onkeyup，onkeydown）的，有如下：

   keyCode存在很多，但vue为我们提供了别名，分为以下两种：

   - 普通键（enter、tab、delete、space、esc、up…）
   - 系统修饰键（ctrl、alt、meta、shift…）

   ```vue
   // 只有按键为keyCode的时候才触发
   <input type="text" @keyup.keyCode="shout()">
   ```

   还可以通过以下方式自定义一些全局的键盘码别名

   ```vue
   Vue.config.keyCodes.f2 = 113
   ```

5. **v-bind修饰符**

v-bind修饰符主要是为属性进行操作，用来分别有如下：

**sync:**能对props进行一个双向绑定

```vue
//父组件
<comp :myMessage.sync="bar"></comp> 
//子组件
this.$emit('update:myMessage',params);
```

以上这种方法相当于以下的简写

```vue
//父亲组件
<comp :myMessage="bar" @update:myMessage="func"></comp>
func(e){
 this.bar = e;
}
//子组件js
func2(){
  this.$emit('update:myMessage',params);
}
```

使用sync需要注意以下两点：

- 使用sync的时候，子组件传递的事件名格式必须为update:value，其中value必须与子组件中props中声明的名称完全一致
- 注意带有 .sync 修饰符的 v-bind 不能和表达式一起使用
- 将 v-bind.sync 用在一个字面量的对象上，例如 v-bind.sync=”{ title: doc.title }”，是无法正常工作的

**props:**设置自定义标签属性，避免暴露数据，防止污染HTML结构

**camel:**将命名变为驼峰命名法，如将view-Box属性名转换为 viewBox

```vue
<svg :viewBox="viewBox"></svg>
```

==**应用场景**==

根据每一个修饰符的功能，我们可以得到以下修饰符的应用场景：

- .stop：阻止事件冒泡

- .native：绑定原生事件
- .once：事件只执行一次
- .self ：将事件绑定在自身身上，相当于阻止事件冒泡
- .prevent：阻止默认事件
- .caption：用于事件捕获
- .once：只触发一次
- . keyCode：监听特定键盘按下
- .right：右键

### 5.v-text与{{}}区别

`{{message}}`：将数据解析为纯文本，不能输出真正的html，在页面加载时显示{{}}，所以通常使用v-html和v-text代替，且花括号方式在以后可能被取消

`v-html="html"`：用于输出html，它与v-text区别在于v-text输出的是纯文本，浏览器不会对其再进行html解析，但v-html会将其当html标签解析后输出。

`v-text="text"`：将数据解析为纯文本，不能输出真正的html，与花括号的区别是在页面加载时不显示{{}}

### 6.v-on可以绑定多个方法吗

```vue
<input
     type="text"
     v-on="{
     input:onInput,
     focus:onFocus,
     blur:onBlur,
     }"
   />
//--------------------------------------
<input type="text" :value="name" @input="onInput" @focus="onFocus" @blur="onBlur" />
```

### 7.Vue循环的key作用

**答:**

当 Vue.js 用 v-for 正在更新已渲染过的元素列表时，它默认用“就地复用”策略。

如果数据项的顺序被改变，Vue 将不会移动 DOM 元素来匹配数据项的顺序， 而是简单复用此处每个元素，并且确保它在特定索引下显示已被渲染过的每个元素。

**key的作用**主要是为了高效的更新虚拟DOM。

> ​		`key` 的特殊属性主要用在 Vue 的虚拟 DOM 算法，在新旧 nodes 对比时辨识 VNodes。如果不使用 key，Vue 会使用一种最大限度减少动态元素并且尽可能的尝试修复/再利用相同类型元素的算法。使用 key，它会基于 key 的变化重新排列元素顺序，并且会移除 key 不存在的元素。
>
> ​		什么意思呢？就是说，key值的存在保证了唯一性，可以用于dom的重新渲染或是就地复用。
>
> ​		vue在执行时，会对节点进行检查，如果没有key值，那么，vue检查到这里有dom节点，则会对内容进行清空，并且赋予新值；如果有key值的存在，那么vue会对`oldnode`和`newnode`进行对比，发现两者key值是否相同，进行调换位置或是删除操作。

### 8.什么是计算属性

**可以理解为能够在里面写一些计算逻辑的属性。**
**作用:**

1. 使得数据处理结构清晰；
2. 依赖于数据，数据更新，处理结果自动更新；
3. 计算属性内部this指向vm实例；
4. 在template调用时，直接写计算属性名即可；
5. 常用的是getter方法，获取数据，也可以使用set方法改变数据；
6. 相较于methods，不管依赖的数据变不变，methods都会重新计算，但是依赖数据不变的时候computed从缓存中获取，不会重新计算。

> **PS:计算属性和方法**
> 值不是直接渲染到页面，也是通过计算之后再渲染到页面，可以使用计算属性computed
>
> 1. methods中的方法在模板中被调用，如果这个方法依赖data，data的值发生了变化，这个方法就会重新执行；计算属性也具备这个特性。保证data中数据与页面中显示的数据保持一致！
> 2. 计算属性计算出来的结果会被缓存起来，下次无需计算直接显示，而方法不是，每次调用都会重新执行。

### 9.Vue单页面的优缺点

**单页面应用（SPA）**

单页面应用（SPA），通俗一点说就是指只有一个主页面的应用，浏览器一开始要加载所有必须的 html, js, css。所有的页面内容都包含在这个所谓的主页面中。但在写的时候，还是会分开写（页面片段），然后在交互的时候由路由程序动态载入，单页面的页面跳转，仅刷新局部资源。多应用于pc端。

**多页面应用（MPA）**

多页面（MPA），就是指一个应用中有多个页面，页面跳转时是整页刷新。

**单页面的优点：**

- 用户体验好，快，内容的改变不需要重新加载整个页面，基于这一点spa对服务器压力较小。
- 前后端分离。
- 页面效果会比较炫酷（比如切换页面内容时的专场动画）。

**单页面缺点：**

- 不利于seo。
- 导航不可用，如果一定要导航需要自行实现前进、后退。（由于是单页面不能用浏览器的前进后退功能，所以需要自己建立堆栈管理）。
- 初次加载时耗时多。
- 页面复杂度提高很多。

### 10.Vuex是什么？怎么使用？在那种场景下使用

**vuex**是通过创建一个集中的数据存储，方便程序中的所有组件进行访问。

**总结**：Vuex就是状态管理工具，数据管理工具

<img src="images/vuex1.jpg" alt="img" style="zoom:67%;" />

**使用:**

**安装vuex**
npm install vuex --save
配置vuex文件创建在src中创建store文件夹与store.js

==在main.js引入store，注入==

**1、创建vuex实例**：（如下图vscod已经帮我们创建好了，下面只是稍微改动了一下）：
将vux赋值给一个变量并暴露出去

**vuex中的数据源state**，我们需要保存的数据就保存在这里。

<img src="images/vuex.jpg" alt="img" style="zoom: 67%;" />

**2、vuex–使用数据源**：
要使用首先在全局main.js引入vuex。
<img src="images/vuex2.jpg" alt="在这里插入图片描述" style="zoom: 67%;" />

**2.1**
**vuex中的数据源state**，我们需要保存的数据就保存在这里。
将数据放在state中
<img src="images/vuex3.jpg" alt="在这里插入图片描述" style="zoom:67%;" />
在需要使用这些数据的文件中可以使用$store.state.xx调用数据
<img src="images/vuex4.jpg" alt="在这里插入图片描述" style="zoom:67%;" />
页面效果：
<img src="images/vuex5.jpg" alt="在这里插入图片描述" style="zoom:67%;" />

### 11.Vue中路由跳转方式（声明式/编程式）

**(1)使用 标签实现路由打开 (声明式导航)：**

router-link标签会自动渲染成a标签，该组件的属性有：

`to 、 tag、target、 active-class、exact-active-class、exact 、event 、 replace、 append`

1. to（必选参数）指定要跳转的路由路径：类型string/location

   ```vue
   <!--直接写对用的路由名-->
   <router-link to="/about">About</router-link>
   
   <!--可以写对象  根据path路径指定跳转-->
   <router-link :to="{path:'one'}">路由一</router-link>
   <!--可以写对象  根据路由命名指定跳转-->
   <router-link :to="{name:'Two'}">路由二</router-link>
   ```

   ```vue
   <!--路由携带查询参数 params方法-->
   <router-link :to="{name:'Three',params: {number: '3' }}">路由三</router-link>
   <!--使用path 带路由参数params，params 不生效-->
   <router-link :to="{path:'/three',params: {number: '3' }}">路由三</router-link>
   ```

   在被跳转到路由页面中获取传递参数

   ```vue
   created(){
   	//获取params传递的参数
   	console.log(this.$route.params.number)
   }
   ```

   ```vue
   <!--路由携带查询参数 query方法-->
   <!--query传参会 地址栏变成 /Four?number=4-->
   <router-link :to="{path:'Four',query: {number: '4' }}">路由四</router-link>
   <router-link :to="{name:'Four',query: {number: '4' }}">路由四</router-link>
   ```

   改变地址拼接传递参数

   ![img](images/router1.jpg)

   在被跳转到路由页面中获取传递参数

   ```vue
   created(){
   	//获取query传递的参数
   	console.log(this.$route.query.number)
   }
   ```

2. tag：类型: string 可以指定当前标签渲染为其他某种标签,默认值: “a” ,

   ```vue
   <!--tag属性 会指定渲染标签-->
    <router-link to="/about">About</router-link>
   <router-link to="/about" tag='div'>About</router-link>
   <router-link to="/about" tag='title'>About</router-link>
   <router-link to="/about" tag='abbr'>About</router-link>
   ```

   这是前端渲染 默认为a标签

   ![img](images/router2.jpg)

3. target 属性规定在何处打开链接文档 默认值_self:在相同的框架中打开被链接文档 _parent:在父框架集中打开被链接文档。 _top:在整个窗口中打开被链接文档。 _blank:在新窗口中打开被链接文档 (只有tag=“a"模式下 target=”_blank" 属性才会生效。)

4. active-class 类型: string 默认值: “router-link-active” 设置 链接激活时使用的 CSS 类名。默认值可以通过路由的构造选项 linkActiveClass 来全局配置。

5. exact-active-class 类型: string 默认值: “router-link-exact-active” 配置当链接被精确匹配的时候应该激活的 class。注意默认值也是可以通过路由构造函数选项 linkExactActiveClass 进行全局配置的

6. exact 类型: boolean 默认值: false按照这个规则，每个路由都会激活< router-link to="/" >！想要链接使用 “exact 匹配模式”，则使用 exact 属性

7. event 类型: string | Array< string > 默认值: ‘click’ 声明可以用来触发导航的事件。可以是一个字符串。

8. replace 类型: boolean 默认值: false 设置 replace 属性的话，当点击时，会调用 router.replace() 而不是 router.push()，于是导航后不会留下 history 记录。

9. append 类型: boolean 默认值: false 设置 append 属性后，则在当前 (相对) 路径前添加基路径

**(2)可以借助 router 的实例方法，通过编写代码来实现 (编程式导航)：**

在Vue实例内部，你可以通过`router`访问路由实例 。因 此你可以 调 用this.router访问路由实例。因此你可以调用this.router访问路由实例。因此你可以调用`this.router.push`。

想要导航到不同的URL，则使用`router.push`方法。这个方法会向history栈添加一个新的记录，所以，当用户点击浏览器后退按钮时，则回到之前的URL。

点击事件

```vue
<!--编程式导航-->
<div @click="goRouter">跳转路由</div>
```

methods下的函数

```js
methods:{
	goRouter(){
		// 字符串
		this.$router.push('four')
		
		// 对象
		this.$router.push({ path: 'four' })

		// 命名的路由
		this.$router.push({ name: 'Four', params: { number: '123' }})
		//如果提供了 path，params 会被忽略，上述例子中的 query 并不属于这种情况。取而代之的是下面例子的做法，你需要提供路由的 name 或手写完整的带有参数的 path：
		this.$router.push({ path: '/four', query: { number: '123' }})
		
		const number = '1234'
		this.$router.push({ path: `/four/${number}`})
		
		//this.$router.replace 使用方法同this.$router.push  但是history栈中不会有记录，点击返回会跳转到上上个页面

		//回退方法 这个方法的参数是一个整数，意思是在 history 记录中向前或者后退多少步，类似 window.history.go(n)。
		this.$router.go(1)
	}
}
```

有时候需要在编程式导航中在浏览器中打开一个新的页面窗口 使用 $router.resolve 这种方法能够实现新窗口打开，

```js
let routeData = this.$router.resolve({
	name: "Four",
	query:{number:'123456'}
});
window.open(routeData.href, '_blank');
```

### 12.跨域的解决方式

### 13.请简述Vue的生命周期以及作用

vue实例从开始创建、初始化数据，编译模板、挂载DOM 渲染、更新、卸载等一系列过程，称为Vue的生命周期，可以分为创建前后、载入前后、更新前后、销毁前后。

**可以理解vue生命周期就是指vue实例从创建到销毁的过程**

**创建前后：** **BeforeCreate** 、 **Created**

1、`beforeCreate`：这个阶段实例已经初始化，只是数据观察与事件机制尚未形成，不能获取DOM节点`（没有data，没有el）`
 `使用场景：因为此时data和methods都拿不到，所以通常在实例以外使用`
 2、`created`：实例已经创建，仍然不能获取DOM节点`（有data，没有el）`
 `使用场景：模板渲染成html前调用，此时可以获取data和methods，so 可以初始化某些属性值，然后再渲染成视图，异步操作可以放在这里`

**载入前后：** **BeforeMount 、Mounted**

1、`beforeMount`：是个过渡阶段，此时依然获取不到具体的DOM节点，但是vue挂载的根节点已经创建`（有data，有el）`
 2、`mounted`：数据和DOM都已经被渲染出来了
 `使用场景：模板渲染成html后调用，通常是初始化页面完成后再对数据和DOM做一些操作，需要操作DOM的方法可以放在这里`

**更新前后：** **BeforeUpdate** 、 **Update**

1、`beforeUpdate`：检测到数据更新时，但在DOM更新前执行
2、`updated`：更新结束后执行
`使用场景：需要对数据更新做统一处理的；如果需要区分不同的数据更新操作可以使用$nextTick`

**销毁前后：** **BeforeDestory** 、 **Destroyed**

1、`beforeDestroy`：当要销毁vue实例时，在销毁前执行
2、`destroyed`：销毁vue实例时执行

**第一次页面加载会触发哪些钩子**

`beforeCreate`、`created`、`beforeMount`、`mounted`

<img src="images/990427-20200806100459811-935629357.png" alt="图片" style="zoom:67%;" />

**作用:它的生命周期中有多个事件钩子，让我们在控制整个Vue实例的过程时更容易形成好的逻辑。**

### 14.DOM渲染在那个生命周期阶段内完成

DOM 渲染在 mounted 中就已经完成了。

### 15.Vue路由的实现

**vue-router是专为Vue打造的路由管理工具**

**1，hash模式**

默认模式，在浏览器中符号“#”，#以及#后面的字符称之为hash，用window.location.hash读取；

特点：hash虽然在URL中，但不被包括在HTTP请求中；用来指导浏览器动作，对服务端安全无用，hash不会重加载页面。

hash 模式下，仅 hash 符号之前的内容会被包含在请求中，如 http://www.xxx.com，因此对于后端来说，即使没有做到对路由的全覆盖，也不会返回 404 错误。

**2，history模式**

history采用HTML5的新特性；且提供了两个新方法：pushState()，replaceState()可以对浏览器历史记录栈进行修改，以及popState事件的监听到状态变更。

history 模式下，前端的 URL 必须和实际向后端发起请求的 URL 一致，如 http://www.xxx.com/items/id。后端如果缺少对 /items/id 的路由处理，将返回 404 错误。

**3，abstract模式**

支持javascript的所有运行环境，常指Node.js服务器环境

### 16.Vue路由模式***hash和history，简单讲一下***



### 17.Vue路由传参的两种方式，prams和query方式与区别

 

### 18.Vue数据绑定的几种方式

 

### 19.Vue注册一个全局组件

 

### 20.Vue的路由钩子函数/路由守卫有哪些

### 21.Vue中如何进行动态路由设置？有哪些方式？怎么获取传递过来的数据？

### 22.Elementui中的常用组件有哪些？请简述你经常使用的 并且他们的属性有哪些？

### 23.Vue-cli中如何自定义指令

1. 创建局部指令

   ```js
   var app = new Vue({
   el: '#app', data: {}, // 创建指令(可以多个)
   directives: {// 指令名称        
   	dir1: {
   		inserted(el) {
   		// 指令中第一个参数是当前使用指令的DOM
   		console.log(el);
   		console.log(arguments);//对DOM进行操作                
   	el.style.width = '200px';
       el.style.height = '200px';
   	el.style.background = '#000';
   				}
   			}
   		}
   	})
   ```

2. 全局指令

   ```js
   Vue.directive(
   'dir2', {    
   inserted(el) {        
   console.log(el);    
   }})
   ```

3. 指令的使用

```xml
<div id="app">    
    <div v-dir1></div>    
    <div v-dir2></div>
</div>
```

### 24.Vue中指令有哪些

### 25.Vue如何定义一个过滤器

**html代码:**

```html
<div id="app">     
    <input type="text" v-model="msg" />     	{{msg| capitalize }}
</div>
```

**JS代码:**

```js
var vm = new Vue({
		el: "#app",
		data: {
			msg: ''
		},
		filters: {
			capitalize: function (value) {
				if (!value) return ''
				value = value.toString()
				return value.charAt(0).toUpperCase() + value.slice(1)
			}
		}
	})
```

全局定义过滤器:

```js
Vue.filter('capitalize', function (value) {
		if (!value) return ''
		value = value.toString()
		return value.charAt(0).toUpperCase() + value.slice(1)
	})
```

过滤器接收表达式的值 (msg) 作为第一个参数。capitalize 过滤器将会收到 msg的值作为第一个参数。

### 26.对vue 中keep-alive的理解

keep-alive是 Vue 内置的一个组件，可以使被包含的组件保留状态，或避免重新渲染。
在vue 2.1.0 版本之后，keep-alive新加入了两个属性: include(包含的组件缓存) 与 exclude(排除的组件不缓存，优先级大于include) 。

```vue
<keep-alive include='include_components' exclude='exclude_components'>
    <component>    
        <!-- 该组件是否缓存取决于include和exclude属性 -->  
    </component>
</keep-alive>
```

**参数解释**
include - 字符串或正则表达式，只有名称匹配的组件会被缓存
exclude - 字符串或正则表达式，任何名称匹配的组件都不会被缓存
include 和 exclude 的属性允许组件有条件地缓存。二者都可以用“，”分隔字符串、正则表达式、数组。当使用正则或者是数组时，要记得使用v-bind 。

**使用示例**

```vue
<!-- 逗号分隔字符串，只有组件a与b被缓存。-->
<keep-alive include="a,b">
    <component></component>
</keep-alive>
<!-- 正则表达式 (需要使用 v-bind，符合匹配规则的都会被缓存) -->
<keep-alive :include="/a|b/">
    <component></component>
</keep-alive>
<!-- Array (需要使用 v-bind，被包含的都会被缓存) -->
<keep-alive :include="['a', 'b']">  <component></component>
</keep-alive>
```

### 27.如何让组件中的css在当前组件生效

在style标签中写入scoped即可 例如：`<style scoped></style>`

### 28.Vue生命周期一共几个阶段

### 29.Mvvm与mvc的区别

### 30.Vue组件中的data为什么是函数

### 31.Vue双向绑定的原理

### 32.Vue中组件怎么传值

### 33.Bootstrap的原理

### 34.Vue兄弟组件传值

### 35.如果一个组件在多个项目中使用怎么办

### 36.槽口请简述

### 37.Watch请简述

### 38.Vantui请简述下

### 39.计算属性与watch区别

### 40.mvvm框架是什么？它和其它框架（jquery）的区别是什么？哪些场景适合？

### 41.Vue首屏加载慢的原因，怎么解决的，白屏时间怎么检测，怎么解决白屏问题

### 42.Vue双数据绑定过程中，这边儿数据改变了怎么通知另一边改变

### 43.Vuex流程

### 44.Vuex怎么请求异步数据

### 45.Vuex中action如何提交给mutation的

### 46.Route与router区别

### 47.vuex有哪几种状态和属性

### 48.vuex的State特性是？

### 49.vuex的Getter特性是？

### 50.vuex的Mutation特性是？

### 51.vuex的actions特性是？

### 52.vuex 是什么？怎么使用？哪种功能场景使用它

### 53.vuex的优势

### 54.Vue路由懒加载（按需加载路由）

 

### 55.v-for与v-if优先级

首先不要把v-if与用在同一个元素上，原因：v-for比v-if优先，如果每一次都需要遍历整个数组，将会影响速度，尤其是当之需要渲染很小一部分的时候。

v-for 比 v-if 具有更高的优先级

 