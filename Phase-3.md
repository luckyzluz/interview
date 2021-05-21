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

> ​		`key` 的特殊属性主要用在 Vue 的虚拟 DOM 算法，在新旧 nodes 对比时辨识 VNodes。如果不使用 key，Vue 会使用一种最大限度减少动态元素并且尽可能的尝试修复/再利用相同类型元素的算法。使用 key，它会基于 key 的变化重新排列元素顺序，并且会移除 key 不存在的元素。
>
> ​		什么意思呢？就是说，key值的存在保证了唯一性，可以用于dom的重新渲染或是就地复用。
>
> ​		vue在执行时，会对节点进行检查，如果没有key值，那么，vue检查到这里有dom节点，则会对内容进行清空，并且赋予新值；如果有key值的存在，那么vue会对`oldnode`和`newnode`进行对比，发现两者key值是否相同，进行调换位置或是删除操作。

**更精准-->在虚拟dom节点中赋予key值，会更加快速的拿到需要的目标节点，不会造成就地复用的情况，对于节点的把控更加精准。**

### 8.什么是计算属性

**可以理解为能够在里面写一些计算逻辑的属性。**
**作用:**

1. 减少模板中的计算逻辑
2. 数据缓存。当我们的数据没有变化时，不在执行计算的过程
3. 依赖固定的数据类型（响应式数据），不能是普通的传入的一个全局数据

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

### Vuex是什么？怎么使用？在那种场景下使用

### Vue中路由跳转方式（声明式/编程式）

### 跨域的解决方式

### Vue的生命周期请简述

### Vue生命周期的作用

### DOM渲染在那个生命周期阶段内完成

### Vue路由的实现

### Vue路由模式***\*hash和history，简单讲一下\****

### Vue路由传参的两种方式，prams和query方式与区别

 

### Vue数据绑定的几种方式

 

### Vue注册一个全局组件

 

Vue的路由钩子函数/路由守卫有哪些

Vue中如何进行动态路由设置？有哪些方式？怎么获取传递过来的数据？

Elementui中的常用组件有哪些？请简述你经常使用的 并且他们的属性有哪些？

Vue-cli中如何自定义指令

Vue中指令有哪些

Vue如何定义一个过滤器

对vue 中keep-alive的理解

如何让组件中的css在当前组件生效

Vue生命周期一共几个阶段

Mvvm与mvc的区别

Vue组件中的data为什么是函数

Vue双向绑定的原理

Vue中组件怎么传值

Bootstrap的原理

Vue兄弟组件传值

如果一个组件在多个项目中使用怎么办

槽口请简述

Watch请简述

Vantui请简述下

计算属性与watch区别

mvvm框架是什么？它和其它框架（jquery）的区别是什么？哪些场景适合？

Vue首屏加载慢的原因，怎么解决的，白屏时间怎么检测，怎么解决白屏问题

Vue双数据绑定过程中，这边儿数据改变了怎么通知另一边改变

Vuex流程

Vuex怎么请求异步数据

Vuex中action如何提交给mutation的

Route与router区别

vuex有哪几种状态和属性

vuex的State特性是？

vuex的Getter特性是？

vuex的Mutation特性是？

vuex的actions特性是？

### vuex 是什么？怎么使用？哪种功能场景使用它

vuex的优势

### Vue路由懒加载（按需加载路由）

 

v-for与v-if优先级

首先不要把v-if与用在同一个元素上，原因：v-for比v-if优先，如果每一次都需要遍历整个数组，将会影响速度，尤其是当之需要渲染很小一部分的时候。

v-for 比 v-if 具有更高的优先级

 