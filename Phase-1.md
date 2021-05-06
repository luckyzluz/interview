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

**⑴border-box**IE盒模型（怪异模式）

**width || height = content + padding + border**

> - 比如设定元素`width = 300px，padding = 20px，border=20px`，那么实际的内容区域宽度为`content = 300 - 20 * 2 - 20 * 2 = 220px`，整个盒子的宽度也就是它自己本身的`width = 300px`，也就是固定宽度后，如果增大border或者padding会压缩内容区的宽度；
> - **整个盒子实际宽度和高度**就是我们设置的盒子的宽度和高度，只是padding和border自动限制到div内，实际的**内容**区域宽度和高度自适应改变了，但总宽度、高度不变。
> - box-sizing:border-box是非常好用的样式属性，解脱了我们设置宽度和高度后再设置padding和border时重新计算设置宽度、高度的问题（因为我们可能需要保证整个盒子大小不变）。
> - 占的总的位置大小为：margin + width || height

**（2）content-box**W3C标准盒模型

**width || height = content 内容区域**

> - 比如设定元素`width = 300px，padding = 20px，border=20px`，那么实际的**内容**区域宽度为`content = 300px`；**整个盒子的宽度**为`300+20*2+20*2 = 380px`，也就是设定额外的padding或border会向外扩张元素的大小；
> - 占的总的位置大小为：margin + border + padding + width || height（width || height 为 content 内容区域 ）
> - 即若想占的总的位置大小不变，增加padding就得较少width || height

**区别：**

**content-box 的 width 不包括 padding 和 border**

**border-box 的 width 包括 padding 和 border**

### 11.元素垂直居中

**分成 块级元素 和 行内元素 进行总结**

**(1)块级元素**

①**flex布局**

  具体的做法就是把父元素的属性：align-items(交叉轴单行对齐) 的值设置为 center

②**绝对定位**

（position: absolute）+ 负margin（这种方式需要知道元素的高）;

（position: absolute）+ transform: translate()属性。

**总结**： 

  其实后面两种原理是相同的，通过绝对定位设置top为50%之后，再考虑处理元素自身的宽高；区别是负margin的方式需要知道具体的值才能设置，而transform: translate()设置百分比就可以，不需要知道具体的值。

④**其他**

如果只需要水平居中：给对应的块级元素设置 margin: 0 auto; 即可

**（2）行内元素**

①在父元素上设置：设置元素的 line-height 的值等于父元素的 height 的值实现垂直居中

②在父元素上设置：display: table; 

行内元素设置 display: table-cell; vertical-align: middle; 实现垂直居中

③给行内元素一个没有宽高的父元素，利用 flex 布局使其父元素水平垂直居中即可

### 12.如何让chrome浏览器显示小于12px的文字

 针对谷歌浏览器内核，加webkit前缀，用transform:scale()这个属性进行缩放！

```html
<style>
    p span{
        font-size:10px;
        -webkit-transform:scale(0.8);
        display:block;
    }
</style>
<p><span>测试10px</span></p>
```

### 13.Css选择器有哪些，那些属性可以继承，优先级如何计算？Css3新增的伪类有哪些

**CSS 选择符：**

1.id选择器(# myid)

2.类选择器(.myclassname)

3.标签选择器(div, h1, p)

4.相邻选择器(h1 + p)

5.子选择器(ul > li)

6.后代选择器(li a)

7.通配符选择器( * )

8.属性选择器(a[rel = "external"])

9.伪类选择器(a: hover, li:nth-child)

可继承的样式：

1.font-size

2.font-family

3.color

4.text-indent

**不可继承的样式：**

1.border

2.padding

3.margin

4.width

5.height

**优先级算法：**

1.优先级就近原则，同权重情况下样式定义最近者为准;

2.载入样式以最后载入的定位为准;

3.!important >  id > class > tag  

4.important 比 内联优先级高，但内联比 id 要高

**CSS3新增伪类举例：**

**p:first-of-type** 选择属于其父元素的首个p元素。

**p:last-of-type**  选择属于其父元素的最后 p元素。

**p:only-of-type**  选择属于其父元素唯一的子元素的每个p元素。

**p:only-child**   选择属于其父元素的唯一子元素的每个p元素。

**p:nth-child(2)**  选择属于其父元素的第二个子元素的每个p元素。

**:enabled**  选择启用的（常规）表单字段

**:disabled **选择禁用的表单字段（`disabled=true`）

**:checked** 选择已选中的表单字段（实际上只有复选框和单选按钮）。

### 14.网页中有大量图片加载很慢 你有什么办法进行优化？

1. 图片懒加载，滚动到相应位置才加载图片。原理是这个可以用js监控滚动的位置，当初图片位置出现或者即将出现在可视区域时，进行加载。
2. 图片预加载，如果为幻灯片、相册等，将当前展示图片的前一张和后一张优先下载。
3. 使用CSSsprite，SVGsprite，Iconfont、Base64等技术，如果图片为css图片的话。
4. 如果图片过大，可以使用特殊编码的图片，加载时会先加载一张压缩的特别厉害的缩略图，以提高用户体验。

------

### 15.行内元素/块级元素有哪些？

**（1）行内元素：**一个行内元素只占据它**对应标签的边框所包含的空间。**

<table>
    <tr>
        <td colspan="2"  style="text-align:center">行内元素</td>
    </tr>
    <tr>
        <td>a</td><td>锚点</td>
    </tr>
    <tr>
        <td>abbr</td><td>缩写</td>
    </tr>
    <tr>
        <td>acronym</td><td>首字</td>
    </tr>
    <tr>
        <td>b</td><td>粗体(不推荐)</td>
    </tr>
    <tr>
        <td>cite</td><td>引用</td>
    </tr>
    <tr>
        <td>br</td><td>换行</td>
    </tr>
    <tr>
        <td>em</td><td>强调</td>
    </tr>
    <tr>
        <td>font</td><td>字体设定(不推荐)</td>
    </tr>
    <tr>
        <td>i</td><td>斜体</td>
    </tr>
    <tr>
        <td>img</td><td>图片</td>
    </tr>
    <tr>
        <td>input</td><td>输入框</td>
    </tr>
    <tr>
        <td>label</td><td>表格标签</td>
    </tr>
    <tr>
        <td>span</td><td>常用内联容器，定义文本内区块</td>
    </tr>
    <tr>
        <td>strong</td><td>粗体强调</td>
    </tr>
    <tr>
        <td>sub</td><td>下标</td>
    </tr>
    <tr>
        <td>sup</td><td>上标</td>
    </tr>
    <tr>
        <td>textarea</td><td>多行文本输入框</td>
    </tr>
    <tr>
        <td>u</td><td>下划线</td>
    </tr>
</table>

**(2)块级元素：** **占据其父元素（容器）的整个空间**，因此创建了一个“块”。通常浏览器会在块级元素前后另起一个**新行**。 |

<table>
    <tr>
        <td colspan="2"  style="text-align:center">块级元素</td>
    </tr>
    <tr>
        <td>div</td><td>常用块级容器，也是CSS layout的主要标签</td>
    </tr>
    <tr>
        <td>dl</td><td>定义列表</td>
    </tr>
    <tr>
        <td>form</td><td>交互表单</td>
    </tr>
    <tr>
        <td>h1-h6</td><td>大、副、3、4、5、6标题</td>
    </tr>
    <tr>
        <td>hr</td><td>水平分隔线</td>
    </tr>
    <tr>
        <td>ol</td><td>有序表单</td>
    </tr>
    <tr>
        <td>p</td><td>段落</td>
    </tr>
    <tr>
        <td>table</td><td>表格</td>
    </tr>
    <tr>
        <td>ul</td><td>无序列表</td>
    </tr>
    <tr>
        <td>center</td><td>居中对齐块</td>
    </tr>
    <tr>
        <td>dir</td><td>目录列表</td>
    </tr>
    <tr>
        <td>fieldset</td><td>form控制组</td>
    </tr>
</table>

**空元素**：< hr/> < br/> < img/> < input/> < link/> < meta/>
< area>< base>< col>< command> < embed>< keygen>< param>< source>< track>< wbr>

------

### 16.浏览器的标准模式和怪异模式区别？

**标准模式：**是浏览器按照W3C标准解析执行代码，这样用规定的语法去渲染，就可以兼容各个浏览器，保证以正确的形式展示网页。
**怪异模式：**是使用浏览器自己的方式解析执行代码，因为不同浏览器解析执行的方式不一样，所以我们称之为怪异模式。这样的弊端就是网页在各个浏览器显示的效果不一样，很难统一。

------

### 17.Margin和padding在什么场合下使用

- margin是用来隔开元素与元素的间距，padding是用来隔开元素与内容的间隔。
- margin用来布局分开元素，使得元素与元素之间互不相干。
- padding用来布局元素与内容之间的间隔，让内容（文字）与（包裹）元素之间有一段空间。

**使用margin的场景：**
1.若需要在border外侧添加空白时。
2.空白处不需要背景（色）时。

注：上下相连的两个盒子之间的空白，需要相互抵消时。如15px + 20px的margin，将得到20px的空白。

**使用padding的场景：**
1.需要在border内测添加空白时。
2.空白处需要背景（色）时。

注：上下相连的两个盒子之间的空白，希望等于两者之和时。如15px + 20px的padding，将得到35px的空白。

**margin使用时应该注意：**

  margin在垂直方向上相邻的值相同时会发生叠加，水平方向上相邻的值会相加。margin取负值时，在垂直方向上，两个元素的边界仍然会重叠。但是，此时一个为正值，一个为负值，并不是取其中较大的值，而是用正边界减去负边界的绝对值，也就是说，把正的边界值和负的边界值相加。

------

### 18.弹性盒子布局属性有那些请简述?

**（1）容器的属性**

*<1>主轴的方向*

```css
flex-direction: row | row-reverse | column | column-reverse;
row（默认值）：主轴为水平方向，起点在左端。
row-reverse：主轴为水平方向，起点在右端。
column：主轴为垂直方向，起点在上沿。
column-reverse：主轴为垂直方向，起点在下沿。
```

*<2>换行属性*

```css
flex-wrap: nowrap | wrap | wrap-reverse;
nowrap：//（默认）不换行。
wrap：//换行，第一行在上方。
wrap-reverse：//换行，第一行在下方。
//简写：方向 + 换行
flex-flow: <flex-direction> || <flex-wrap>;
```

*<3>主轴对齐方式*

```css
justify-content: flex-start | flex-end | center | space-between | space-around;
flex-start（默认值）：左对齐
flex-end：右对齐
center： 居中
space-between：两端对齐，项目之间的间隔都相等。
space-around：每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍。
```

*<4>交叉轴对齐方式*

```css
align-items: flex-start | flex-end | center | baseline | stretch;
flex-start：交叉轴的起点对齐。
flex-end：交叉轴的终点对齐。
center：交叉轴的中点对齐。
baseline: 项目的第一行文字的基线对齐。
stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。
```

*<5>多根轴线对齐方式*

```css
align-content: flex-start | flex-end | center | space-between | space-around | stretch;
flex-start：与交叉轴的起点对齐。
flex-end：与交叉轴的终点对齐。
center：与交叉轴的中点对齐。
space-between：与交叉轴两端对齐，轴线之间的间隔平均分布。
space-around：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。
stretch（默认值）：轴线占满整个交叉轴。
```



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