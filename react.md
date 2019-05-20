# React


## React 核心流程
* reconciliation (调度算法，也可称为 render):

  * 更新 state 与 props；
  * 调用生命周期钩子；
  * 生成 virtual dom；
    * 这里应该称为 Fiber Tree 更为符合；
  * 通过新旧 vdom 进行 diff 算法，获取 vdom change；
  * 确定是否需要重新渲染
* commit:
  * 如需要，则操作 dom 节点更新


## React 生命周期

* 初始化过程
  * componentWillMount
  * componentDidMount 《= 发出Ajax请求

* 更新过程
  * componentWillUpdate
  * render
  * componentDidUpdate
  * 
* 卸载过程
  componentWillUnmount


## 什么是HoC（Higher-Order Component）？

* 高阶组件就是一个 React 组件包裹着另外一个 React 组件

## 为什么循环产生的组件中要利用上key这个特殊的prop？

* Keys负责帮助React跟踪virtualDOM中哪些元素被改变/添加/移除

## 什么时候用Class component，什么时候用Functional component？

* Class component：用到了state，生命周期函数
* Functional component：其它情况


## 并不是父子关系的组件，如何实现相互的数据通信？

* 使用父组件，通过props将变量传入子组件


## 当组件的setState函数被调用之后，发生了什么？

* 把传递给setState的参数对象合并到组件原先的state
* React会构建一个React元素树，它会找出这棵新树和旧树的不同之处
* React能够相对精确地找出哪些位置发生了改变以及如何发生了什么变化
  
并且知道如何只通过必要的更新来最小化重渲染。

## 受控组件(Controlled Component)与非受控组件(Uncontrolled Component)的区别

## refs 是什么?
* Refs是能访问DOM元素或组件实例的一个函数；


## React 中 setState 什么时候是同步的，什么时候是异步的？