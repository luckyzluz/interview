### 1.doctype的作⽤是什么?✨

- DOCTYPE是html5标准⽹⻚声明，且必须声明在HTML⽂档的第⼀⾏。来告知浏览器的解析器⽤什么⽂档标准解析这个⽂档，不同的渲染模式会影响到浏览器对于 CSS 代码甚⾄ JavaScript 脚本的解析
- ⽂档解析类型有：

BackCompat：怪异模式，浏览器使⽤⾃⼰的怪异模式解析渲染⻚⾯。（如果没有声明DOCTYPE，默认就是这个模式）

CSS1Compat：标准模式，浏览器使⽤W3C的标准解析渲染⻚⾯。

> IE8还有⼀种介乎于上述两者之间的近乎标准的模式，但是基本淘汰了。

### 2.这三种模式的区别是什么? 

![img](wps4-1619095148348.png)![img](wps5-1619095148349.png)标准模式(standards mode)：⻚⾯按照 HTML 与 CSS 的定义渲染怪异模式(quirks mode)模式： 会模拟更旧的浏览器的⾏为

![img](wps6.png)近乎标准(almost standards)模式： 会实施了⼀种表单元格尺⼨的怪异⾏为（与IE7之前的单元格布局⽅式⼀致）， 除此之外符合标准定义

### HTML、XHTML、XML有什么区别?

 

![img](wps7.png)HTML(超⽂本标记语⾔): 在html4.0之前HTML先有实现再有标准，导致HTML⾮常混乱和松散

![img](wps8.png)XML(可扩展标记语⾔): 主要⽤于存储数据和结构，可扩展，⼤家熟悉的JSON也是相似的作⽤，但是更加轻量⾼效，所以XML现在市场越来越⼩了

![img](wps9.png)XHTML(可扩展超⽂本标记语⾔): 基于上⾯两者⽽来，W3C为了解决HTML混乱问题⽽⽣，并基于此诞⽣了

HTML5，开头加⼊ <!DOCTYPE html> 的做法因此⽽来，如果不加就是兼容混乱的HTML，加了就是标准模式。

### 3.什么是data-属性？

HTML的数据属性，⽤于将数据储存于标准的HTML元素中作为额外信息,我们可以通过js访问并操作它，来达到操作数据的⽬的。

```html
<article id="electriccars" data-columns="3"
data-index-number="12314" data-parent="cars">
...
</article>
```

