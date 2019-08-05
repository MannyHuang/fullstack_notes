# React

## React 核心流程

- reconciliation (调度算法，也可称为 render):

  - 更新 state 与 props；
  - 调用生命周期钩子；
  - 生成 virtual dom；
    - 这里应该称为 Fiber Tree 更为符合；
  - 通过新旧 vdom 进行 diff 算法，获取 vdom change；
  - 确定是否需要重新渲染

- commit:
  - 如需要，则操作 dom 节点更新

## Virtual DOM 原理

- 根据 DOM 的树状结构生成 JS 的表达，即虚拟 DOM
- 根据数据的变化生成新的 virtual dom
- 将两个 virtual dom 进行 diff，根据变化的部分修改真正的 dom

## React 生命周期

- 初始化过程

  - componentWillMount
  - componentDidMount 《= 发出数据请求

- 更新过程

  - componentWillUpdate
  - render
  - componentDidUpdate
  - shouldComponentUpdate 《= 通过条件判断返回布尔值确定是否更新视图
  - componentWillReceiveProps

- 卸载过程
  - componentWillUnmount

## Redux 使用流程

- Redux 介绍

  - redux 是 react 应用的状态管理机制
  - 为了解决多页面多组件之间的数据通信
  - 主要有 Store、Action、Reducer 三部分组成
    - component 发起 action 操作修改 store 中 的 state
    - reducers 根据 action 和当前的 state 获得新的 state
    - redux 使用 getState 方法通知页面更新视图

- Redux Data loading cycle

  - component rendered
  - componentDidMount called
  - call actionCreator from componentDidMount
  - call api in actionCreator
  - api responds with data
  - action creater returns actions with data in payload of action
  - some reducer parse and return the data
  - react-redux rerender the app

- Rules of redux reducers
  _ must not return undefined
  _ must produce state based only on preState and action
  _ must not reach out itself to get data
  _ must not mutate input

## redux 缺点

- verbose
- code locality

## React 中 key 的作用

- key 作为元素的唯一标识用来表示元素的唯一性，在进行 diff 算法比较时，通过 key 避免不必要的渲染，实现高效的视图更新机制。

## react 中 refs 的作用

- 访问 DOM 元素实例的句柄 (本质是一个函数）)

## 什么是 HoC（Higher-Order Component）？

- 高阶组件就是一个 React 组件包裹着另外一个 React 组件

## 为什么循环产生的组件中要利用上 key 这个特殊的 prop？

- Keys 负责帮助 React 跟踪 virtualDOM 中哪些元素被改变/添加/移除

## 什么时候用 Class component，什么时候用 Functional component？

- Class component：用到了 state，生命周期函数
- Functional component：其它情况

## 并不是父子关系的组件，如何实现相互的数据通信？

- 使用父组件，通过 props 将变量传入子组件

## 当组件的 setState 函数被调用之后，发生了什么？

- 把传递给 setState 的参数对象合并到组件原先的 state
- React 会构建一个 React 元素树，它会找出这棵新树和旧树的不同之处
- React 能够相对精确地找出哪些位置发生了改变以及如何发生了什么变化

并且知道如何只通过必要的更新来最小化重渲染。

## 受控组件(Controlled Component)与非受控组件(Uncontrolled Component)的区别

- 受控组件由 react 侦测改变和管理 value
- 非受控组件由 dom 自己管理 value

## React 中 setState 什么时候是同步的，什么时候是异步的？
