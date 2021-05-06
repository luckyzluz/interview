### 1.网络中使用最多的图片格式有哪些

JPEG、GIF、PNG以及最近网页常见的webp

------

### 2.请简述css盒子模型

CSS盒子模型也叫做框模型，具备内容(content)、填充(padding)、边框(border)、边界(margin)这些属性。在CSS中，每一个元素都被视为一个框，而每个框都有三个属性：

> border:元素的边框（可能不可见），用于将框的边缘与其他框分开；
> margin：外边距，表示框的边缘与相邻框之间的距离，也称为页边空白；
> padding:内边距，表示框内容和边框之间的空间。

------

### 3.视频/音频标签的使用

(1)**视频video**

```html
<video
   src=”视频的路径”
   controls=”控制播放、暂停、音量等”
   autoplay=”自动播放”
   loop=”循环播放”
   width=”视频播放器的宽度”
   height=”视频播放器的高度”
</video>
```

还有做浏览器兼容的方式：


```html
          <video  controls autoplay loop width="500" height="500">
          <source src="video/hhxd.mp4" type="video/mp4"></source>
          <source src="video/ghsy.ogg" type="audio/ogg"></source>
     //flash支持
    //当所有不支持时，就提供一个下载路径。
    </video>
```

   (2)**音频audio**

```html
   <audio
      src=”音频的路径”
      controls=”控制播放、暂停、音量等”
      autoplay=”自动播放”
      loop=”循环播放”
   ></audio>
   //兼容类似视频方式
```

------

### 4.HTML5新增的内容有哪些

**语义化标签**：header，main，aside，nav，footer，section等

**增强型表单**：password number tel url file range color datatime date time week month 等

**新的表单属性**：placeholder list datalist min max autofocus等

**视频音频**：audio video

**Geolocation**：可以请求用户共享他们的位置

**Communication**：跨文档消息通信，可以确保iframe、标签页、窗口间安全地进行跨源通信。

**XMLHttpRequest Level2**：改进了跨源XMLHttpRequest和进度事件，XMLHttpRequest Level2通过CORS实现了跨源XMLHttpRequest。跨源HTTP请求包含一个Origin头部，它为服务器提供HTTP请求的源信息。

**WebSockets**：要连接远程主机，只需新建一个WebSocket实例，提供希望连接的对端URL。

**拖放API**：draggable属性、拖放事件(dragstart、drag、dragenter、dragleave、dragover、drap、dragend)、dataTransfer对象

**Web Workers API**：Web Workers可以让Web应用程序具备后台处理能力，对多线程的支持性非常好。但是在Web Workers中执行的脚本不能访问该页面的window对象，也就是Web Workers不能直接访问Web页面和DOM API。虽然Web Workers不会导致浏览器UI停止响应，但是仍然会消耗CPU周期，导致系统反应速度变慢。

**Web Storage API**：sessionStorage(保存在session中，浏览器关闭，数据消失)、localStorage(保存在客户端本地，除非手动删除，否则一直保存)

------

### 5.Html5 新增的语义化标签有哪些

**新的标签带来的是网页布局的改变及提升对搜索引擎的友好**

```html
<article> 定义文章 
<aside> 定义文章的侧边栏
<figure> 一组媒体对象以及文字 
<figcaption> 定义 figure 的标题
<footer>定义页脚 
<header>定义页眉
<hgroup>定义对网页标题的组合 
<nav>定义导航
<section> 定义文档中的区段 
<time>定义日期和时间
<dialog>定义一个对话框
<header></header>
<footer></footer>
<nav></nav>
<section> <section> 页面上的版块
用于划分页面上的不同区域,或者划分文章里不同的节
<article></ article > 
用来在页面中表示一套结构完整且独立的内容部分，可以用来呈现论坛的一个帖子，杂志或报纸中的一篇文章，一篇博客，用户提交的评论内容等。
<figure> 标签规定独立的流内容（图像、图表、照片、代码等等）。
<figcaption> figure的子元素 用于对figure的内容 进行说明
<time></time>
<datalist></datalist>选项列表。与 input 元素配合使用，来定义 input 可能的值。
<mark></mark> 需要标记的词或句子
<details></details>用于描述文档或文档某个部分的细节
< summary></summary> details 元素的标题
该元素用于摘录引用等 应该与页面的主要内容区分开的其他内容
Open 属性默认展开
```

**状态交互元素** 

```html
progress元素 ：标签定义运行中的进度（进程）
 <progress  value="0" max="100"></progress> 
meter元素 ：标签定义度量衡。仅用于已知最大和最小值的度量。
 <meter  value="70" max="100" min="0"></meter>
Forms
email  :  电子邮箱文本框，跟普通的没什么区别,当输入不是邮箱的时候，验证通不过.移动端的键盘会有变化
tel   :   电话号码,移动端的键盘
url   :   网页的URL
search  :  搜索引擎
range  :  特定范围内的数值选择器
min、max、step( 步数 )、value
用JS来显示当前数值
```

 **新的表单特性和函数**

```html
placeholder //输入框提示信息(密码框提示)
autocomplete //是否保存用户输入值默认为on，关闭提示选择off
autofocus //指定表单获取输入焦点
list和datalist //为输入框构造一个选择列表(list值为datalist标签的id)
required //此项必填，不能为空带有必填字段的表单
Pattern //正则验证  pattern="\d{1,5}“
formaction //在submit里定义提交地址
```

------

### 6.Css3新增的特性

**（1）新选择器**

>  E:nth-child(n) 选择器匹配其父元素的第n个子元素，不论元素类型，n可以使数字，关键字，或公式

>  E:nth-of-type(n) 选择与之其匹配的父元素的第N个子元素

> E:frist-child 相对于父级做参考，“所有”子元素的第一个子元素，并且“位置”要对应

> E：frist-of-type 相对于父级做参考，“特定类型”（E）的第一个子元素

> E：empty 选择没有子元素的每个E元素

> E:target 选择当前活动的E元素

> ::selection 选择被用户选取的元素部分

> 属性选择器
>
> E[abc*="def"] 选择adc属性值中包含子串"def"的所有元素

**（2）文本**

 **text-shadow**:2px 2px 8px #000;

参数1为向右的偏移量，参数2为向左的偏移量，参数3为渐变的像素，参数4为渐变的颜色

**text-overflow**:规定当文本溢出包含元素时发生的事情

**text-overflow**:ellipsis(省略)

**text-wrap**:规定文本换行的规则

**word-break** :规定非中日韩文本的换行规则

**word-wrap** :对长的不可分割的单词进行分割并换行到下一行

**white-space**: 规定如何处理元素中的空白  white-**space:nowrap** 规定段落中的文本不进行换行

**(3)边框**

**border-raduis**:50%边框的圆角

**border-image** 边框图片

```css
.border-image {
    border-image-source:url(images/border.png);
​    boder-image-slice:27;
​    border-image-width:10px;
​    border-iamge-repeat:round; 
//(round平铺) 平铺效果不作用于四角，只适应与四边  
}
```

**(4)背景**

**rgba(0,0,0,0.3)**

**backgrounnd-size**:cover/contain

**background-size：cover**，会使“最大”边进行缩放，另一边同比缩放，铺满容器，超出部分会溢出。

**background-size:contain**，会使“最小”边进行缩放，另一边同比缩放，不一定铺满容器，会完整显示图片

**(5)渐变**

**linear-gradient()**:用于创建一个表示两种或多种颜色线性渐变的图片

background-image:linear-gradient(90deg,yellow 20%,green 80%)

渐变轴为90度，从黄色渐变到绿色

**radial-gradient()**:用径向渐变创建 "图像"

background-image:radial-gradient(120px at center center,yellow,green)

**(6)多列布局**

**column-count**:属性规定元素被分配列数

**column-width**:属性指定列的宽度

**column-gap**:列之间间隔

**column-rule**:列之间宽度样式和颜色规则，所有 column-rule-* 属性的简写

**(7)对象变换时的过渡效果transition**

**transition-property**:width       

**property**为定义过渡的css属性列表，列表以逗号分隔

**transition-duration**:2s;   过渡持续的时间

**transition-timing-function**:ease;  过渡的类型

**transition-delay**:5s;   延迟过渡的时间

**(8)动画、旋转**

**Animation动画特效**

**transform** ：translate（x,y) rotate(deg) scale(x,y)

**translate**:定义 2D 转换

**scale**:定义 2D 缩放转换

**rotate**:定义 2D 旋转，在参数中规定角度

**skew**（倾斜）:定义沿着 X 和 Y 轴的 2D 倾斜转换

**(9)flex布局**

**(10)@media媒体查询**

------

### 7.清除浮动的方式有哪些？请说出各自的有特点

**(1)给父元素单独定义高度**
　　优点：简单快速、代码少。
　　缺点：无法进行响应式布局。

**(2)在标签结尾处加空div标签**

```html
<div style="clear: both"></div>
```

　　优点：简单快速、代码少，兼容性较高。
　　缺点：增加空标签，不利于页面优化。

**(3)父级定义overflow:hidden**
　　优点：简单快速、代码少，兼容性较高。
　　缺点：超出部分被隐藏了，在布局的时候要注意。

**(4)父级定义class="clearfix"，使用after伪类和zoom**

```css
.clearfix:after{
    content:"";
    display:block;
    clear:both;
    height:0;
    overflow:hidden;
    visibility:hidden;
}
.clearfix{
    zoom:1;
}
```

　　优点：写法固定，没有多余结构，兼容性高。
　　缺点：代码多。

------

### 8.定位的属性值有何区别

**两个方面的比较**

- 是否脱离文档流（标准流）
- 相对于谁定位

**比较**

1. **Position** 有四个属性值：relative absolute fixed static
2. **Relative** 相对定位 不脱离文档流，相对于自身定位
3. **Absolute** 绝对定位，脱离文档流 相对于父级定位
4. **Fixed** 固定定位，脱离文档流，相对于浏览器窗口定位
5. **Static** 默认值，元素出现在正常的流中

------

### 9.子元素如何在父元素中居中

**分成 块级元素 和 行内元素 进行总结**

**(1)块级元素**

①**flex布局**

  具体的做法就是把父元素的属性： jusity-content(主轴对齐方式) 和 align-items(交叉轴单行对齐) 的值设置为 center

②**绝对定位**

（position: absolute）+ 负margin（这种方式需要知道元素的宽高）;

（position: absolute）+ transform: translate()属性。

**总结**： 

  其实后面两种原理是相同的，通过绝对定位设置top和left为50%之后，再考虑处理元素自身的宽高；区别是负margin的方式需要知道具体的值才能设置，而transform: translate()设置百分比就可以，不需要知道具体的值。

④**其他**

如果只需要水平居中：给对应的块级元素设置 margin: 0 auto; 即可

**（2）行内元素**

①在父元素上设置：text-align: center; 实现水平居中；设置元素的 line-height 的值等于父元素的 height 的值实现垂直居中，这应该是我们平时用的比较多的一种

②在父元素上设置：text-align: center; 实现水平居中；再给父元素设置 display: table; 行内元素设置 display: table-cell; vertical-align: middle; 实现垂直居中

③给行内元素一个没有宽高的父元素，利用 flex 布局使其父元素水平垂直居中即可

### 10.Border-box与content-box的区别



### 11.元素垂直居中

### 12.如何让chrome浏览器显示小于12px的文字

### 13.Css选择器有哪些，那些属性可以继承，优先级如何计算？Css3新增的伪类有哪些

### 14.网页中呦大量图片加载很慢 你有什么办法进行优化？

### 15.行内元素/块级元素有哪些？

### 16.浏览器的标准模式和怪异模式区别？

### 17.Margin和padding在什么场合下使用

### 18.弹性盒子布局属性有那些请简述?

### 19.怎么实现标签的禁用

### 20.Flex布局原理

### 21.Px与rem的区别

### 22.网页的三层结构有哪些

### 23.请简述媒体查询

### 24.Rem缺点

### 25.常见的兼容性一阶段内容中记几个

### 26.垂直与水平居中的方式

### 27.三栏布局方式两边固定中间自适应

### 28.Doctype作用