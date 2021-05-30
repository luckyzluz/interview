### 1.说说React的理解

1. **什么**

      动态构建用户界面的JS库

2. **React的特点**

      Declarative(*声明式*编码)

      Component-Based(`组件化`编码)

      Learn Once, Write Anywhere(支持客户端与服务器渲染/编写原跨平台生应用)

      高效

3. **React高效的原因**

   虚拟(virtual)DOM, 不总是直接操作真实DOM(批量更新, 减少更新的次数) 

   高效的DOM Diff算法, 最小化页面重绘(减小页面更新的区域)

### 2.使用2种方式定义一个简单组件

```react
//1). 方式1: 工厂函数(简单/无状态组件)
   function MyComponent1(props) {
      return <h1>自定义组件标题11111</h1>
   }
//2). 方式2: ES6类(复杂/有状态组件)
   class MyComponent2 extends React.Component {
      render () { // 回调函数, 为组件对象提供虚拟DOM
        return <h1>自定义组件标题33333</h1>
      }
   }
ReactDOM.render(<MyComponent1/>, domContainer)
```

### 3.区别类组件和函数式组件

1. **类组件**: 使用class定义的组件, 会产生组件对象, 可以有自身的状态和生命周期勾子
2. **函数组件**: 使用function定义的组件, 不会产生组件对象, 没有自身的状态和生命周期勾子

### 4.说说组件对象的3大属性

1. **state**: 值为容器对象, 保存的是组件内可变的数据,组件根据state中的数据显示, 要更新界面只要更新state即可 
2. **props**: 值为容器对象, 保存的是从组件外传递过来的数据, 当前组件只读, 父组件修改了自动显示新数据
3. **refs**: 值为容器对象, 保存的是n个有ref属性的dom元素对象, 属性名是ref指定的标识名称, 值为对应的dom元素

### 5.React组件化编码的3步与2个重要问题

**编码的3步**

1.    拆分组件

2.    实现静态组件

3.    实现动态组件
         a. 动态显示初始化数据
         b.类型
         c.保存在哪个组件

**2个重要问题**

1. **状态数据保存在哪个组件**?  看是某个组件需要, 还是某些组件需要(给父组件)
2. **更新状态数据的行为在哪个组件**? 状态在哪个组件, 行为就定义在哪个组件

### 6.组件的生命周期及勾子

1. 初始化阶段：ReactDOM.render(<Xxx/>, containDom)
      constructor(): 创建组件对象的初始化方法
      componentWillMount：组件即将被装载、渲染到页面上
      render:组件在这里生成虚拟的DOM节点
      componentDidMount:组件真正在被装载之后
2. 更新阶段：`this.setState({})`
      componentWillReceiveProps:组件将要接收到属性的时候调用
      shouldComponentUpdate:组件接受到新属性或者新状态的时候（可以返回false，接收数据后不更新，阻止render调用重绘）
      componentWillUpdate:组件即将更新不能修改属性和状态
      render:组件重新描绘
      componentDidUpdate:组件已经更新
3. 销毁阶段：`ReactDOM.unmountComponentAtNode(div)`
      componentWillUnmount:组件即将销毁

### 7.关于设计state数据的3个问题

### 8.说说react应用中如何与后台通信?

### 9.比较react中组件间3种通信方式

### 10.说说对react-router的理解

### 11.区别UI组件与容器组件

### 12.说说你对redux的理解

### 13.redux结构图

### 14.redux的基本编码

### 15.React组件的二种分类

### 16.eact性能优化是哪个周期函数?

### 17.为什么虚拟dom会提高性能?

### 18.Dom Diff算法

### 19.调用 setState 之后发生了什么？

### 20.React 中 keys 的作用是什么？

### 21.概述下 React 中的事件处理逻辑

### 22.传入 setState 函数的第二个参数的作用是什么？

### 23.何为受控组件(controlled component)

### 24.何为高阶组件(higher order component)

### 25.了解 redux么，说一下redux吧

### 26.详细说说redux