## 一.jq引入

```
jQuery是一个简洁高效的且功能丰富的JavaScript工具库，是对原生JavaScript二次封装的工具函数集合

开源 | 简洁的选择器 | 简化的Ajax操作 | 良好的浏览器兼容 | 强大的链式操作

官网下载：https://jquery.com/download/ 
```

#### 1.1使用jq

```
// 本地
<script src="js/jquery-3.3.1.js"></script>
// CDN 实际开发中一定要采用CDN这种方法
<script src="https://cdn.bootcss.com/jquery/3.3.1/jquery.js"></script>
```

#### 1.2jq对象

```
jq选择器获取的对象(是对页面元素对象的二次封装)，可以使用jq封装提供的工具函数

jQuery | $
```

![img](https://images.cnblogs.com/OutliningIndicators/ContractedBlock.gif) jq引入的相关代码

[回到顶部](https://www.cnblogs.com/wangmiaolu/articles/10324649.html#_labelTop)

## 二.jq选择器

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
// 获取满足条件的所有页面元素jq对象
$('css3选择器语法');

// 拿到指定索引的页面元素jq对象
$('css3选择器语法').eq(index);

// 拿到指定索引的页面元素js对象 (jq对象转js对象)
$('css3选择器语法').get(index);

// js对象转jq对象
$(js对象);
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

![img](https://images.cnblogs.com/OutliningIndicators/ContractedBlock.gif) jq选择器相关代码

[回到顶部](https://www.cnblogs.com/wangmiaolu/articles/10324649.html#_labelTop)

## 三.jq文档加载

pass

[回到顶部](https://www.cnblogs.com/wangmiaolu/articles/10324649.html#_labelTop)

## 五.盒子信息

pass

[回到顶部](https://www.cnblogs.com/wangmiaolu/articles/10324649.html#_labelTop)

## 六.jq事件

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
// 绑定事件：事件,委派,参数,函数
on(eve,[sel],[data],fn)

// 取消冒泡
ev.stopPropagation();

// 取消默认事件
ev.preventDefault();
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

#### 6.1点击事件

![img](https://images.cnblogs.com/OutliningIndicators/ContractedBlock.gif) js对象使用相关代码

![img](https://images.cnblogs.com/OutliningIndicators/ContractedBlock.gif) jq对象使用相关代码一

![img](https://images.cnblogs.com/OutliningIndicators/ContractedBlock.gif) jq对象使用相关代码二(主要方法)

#### 6.2jq事件(传参)



#### 6.3jq事件(委派)

pass

 



## 七.jq动画

#### 7.1jq动画



```
animate(params,[speed],[easing],[fn])

params:一组包含作为动画属性和终值的样式属性和及其值的集合
speed:三种预定速度之一的字符串("slow","normal", or "fast")或表示动画时长的毫秒数值(如：1000)
easing:要使用的擦除效果的名称(需要插件支持).默认jQuery提供"linear" 和 "swing".
fn:在动画完成时执行的函数，每个元素执行一次。
```







## 八.jq结合css动画



```
<style>
    .box { /*第一状态*/
        width: 200px;
        height: 200px;
        background-color: brown;
        margin: 100px auto;
        transition: 1s;
    }
    .box.move { /*第二状态*/
        margin-top: 50px;
        width: 300px;
        height: 300px;
        background-color: yellow;
    }
</style>
<body>
    <div class="box"></div>
</body>
<script src="js/jquery-3.3.1.js"></script>

<script>
    $('.box').on('mouseenter', function () {
        $(this).addClass('move'); // 添加了move类名,从第一状态动画到第二状态
    })

    $('.box').on('mouseleave', function () {
        $(this).removeClass('move'); // 删除了move类名,从第二状态动画到第一状态
    })

</script>
```



![img](https://images.cnblogs.com/OutliningIndicators/ContractedBlock.gif) jq结合css动画的相关代码



## 九.轮播图布局

pass



## 十.轮播图动画

pass



##  十一.标签结构关系

#### 11.1结构



```
孩子们：children()
父级：parent()
父级们：parents()
下一个：next()
下方所有：nextAll()
上一个：prev()
上方所有：prevAll()
兄弟们：siblings()
```



## 十二.jq的dom操作

#### 12.1dom操作



```
父加子最后：append(content|fn)
子加到父最后：appendTo(content)
父加子最前：prepend(content|fn)
子加到父最前：prependTo(content)

参数加到后：after(content|fn)
参数加到前：before(content|fn)
插入到参数后：insertAfter(content)
插入到参数前：insertBefore(content)

原来替换成参数：replaceWith(content|fn)  前者替换成后者
参数替换原来：replaceAll(selector)　　　　所有的替换成原来

清空：empty()
不保留事件删除：remove()
保留事件删除：detach()
```

```
'''
// sup.append(sub); 在sup的最后方添加sub
// $('body').append($box);

// sub.appendTo(sup); 将sub插入到sup的最后放
// $box.appendTo($('body'));

// sup.prepend(sub); 在sup的最前方添加sub
// $('body').prepend($box);

// 在wrapper后添加box
// $('.wrapper').after($box);

// box插入到wrapper前
// $box.insertBefore($('.wrapper'))

// 所有wrapper被box替换
// $('.wrapper').replaceWith($box)

// 用box把所有的wrapper替换掉
// $box.replaceAll($('.wrapper'))

// $('.wrapper').empty();
// $('.wrapper').html("");

$('.ele').click(function () {
    alert($(this).text())
});

// 自删: remove()不保留事件  detach()保留事件
// var $ele = $('.ele').remove();
var $ele = $('.ele').detach();

'''
```

## 十三.表单元素

```
​```html
<!-- action: 请求的后台链接地址 -->
<!-- method: 请求方式 get | post -->
<form action="" method="post">
    <!--可以提交给后台的数据: 必须有唯一标识, 用name属性来标识-->

    <!--表单元素对象input通过设置type来实现不同的功能-->
    <div>
        <label for="usr">用户名:</label>
        <input type="text" id="usr" name="usr" value="000">
    </div>
    <div>
        <label for="pwd">密码:</label>
        <input type="password" id="pwd" name="pwd" placeholder="请输入密码">
    </div>
    
    <!--文本域-->
    <textarea></textarea>
    
    <!--列表-->
    <select name="sex">
        <option value="male">男</option>
        <option value="female">女</option>
        <option value="other">哇塞</option>
    </select>

    <!--单选框, name来关联, checked为默认选中项-->
    <div>
        男<input type="radio" name="gender">
        女<input type="radio" name="gender" checked>
    </div>

    <!--复选框, name来关联-->
    <div>
        爱好:
        男<input type="checkbox" name="like" value="male">
        女<input type="checkbox" name="like" value="female" checked>
    </div>
    
    <div>
        <button type="button">普通按钮</button>
        <button type="reset">重置</button>
        <button type="submit">提交</button>
        <input type="submit" value="我也是提交">
    </div>
</form>
```

## 十四.flask简易后台

#### 14.1安装flask的包

 



## 十五.form表单请求

pass



## 十六.ajax请求

pass