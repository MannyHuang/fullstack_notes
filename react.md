# React

## React 核心流程

- reconciliation: compute which part has changed

  - 更新 state 与 props；
  - 调用生命周期钩子；
  - 生成 virtual dom；
    - 这里应该称为 Fiber Tree 更为符合；
  - 通过新旧 vdom 进行 diff 算法，获取 vdom change；
  - 确定是否需要重新渲染

- rendering: 渲染画面
  - 如需要，则操作 dom 节点更新

## Virtual DOM 原理

- 根据 DOM 的树状结构生成 JS 的表达，即虚拟 DOM
- 根据数据的变化生成新的 virtual dom
- 将两个 virtual dom 进行 diff，根据变化的部分修改真正的 dom

## 当组件的 setState 函数被调用之后，发生了什么？

- 把传递给 setState 的参数对象合并到组件原先的 state
- React 会构建一个 React 元素树，它会找出这棵新树和旧树的不同之处
- React 能够相对精确地找出哪些位置发生了改变以及如何发生了什么变化
- 并且知道如何只通过必要的更新来最小化重渲染。

## React 生命周期

```js
// mounting
constructor()
static getDerivedStateFromProps()
render()
componentDidMount()

// updating
static getDerivedStateFromProps()
shouldComponentUpdate()
render()
getSnapshotBeforeUpdate()
componentDidUpdate()

// unmount
componentWillUnmount()
```

## React 中 key 的作用

- key 作为元素的唯一标识用来表示元素的唯一性
- 帮助跟踪 virtualDOM 中哪些元素被改变/添加/移除
- 进行 diff 算法比较时，通过 key 避免不必要的渲染，实现高效的视图更新机制。

## react 中 refs 的作用

- 访问 DOM 元素实例的句柄 (本质是一个函数）)

## 受控组件(Controlled Component)与非受控组件(Uncontrolled Component)的区别

- 受控组件由 react 侦测改变和管理 value
- 非受控组件由 dom 自己管理 value

## 什么时候用 Class component，什么时候用 Functional component？

- Class component：用到了 state，生命周期函数
- Functional component：其它情况

## 并不是父子关系的组件，如何实现相互的数据通信？

- redux

## React 中 setState 什么时候是同步的，什么时候是异步的？

- 在 合成事件 和 生命周期钩子(除 componentDidUpdate) 中，setState 是"异步"的；
- 在 原生事件 和 setTimeout 中，setState 是同步的，可以马上获取更新后的值；

## 什么是 HoC（Higher-Order Component）？

- 高阶组件不是组件，是 增强函数，可以输入一个元组件，返回出一个新的增强组件；
- 高阶组件的主要作用是 代码复用，操作 状态和参数；

- 属性代理 (Props Proxy): 给元组件添加 props

```js
function withOnChange(Comp) {
  return class extends React.Component {
    constructor(props) {
      super(props);
      this.state = {
        name: ""
      };
    }
    onChangeName = () => {
      this.setState({
        name: "dongdong"
      });
    };
    render() {
      const newProps = {
        value: this.state.name,
        onChange: this.onChangeName
      };
      return <Comp {...this.props} {...newProps} />;
    }
  };
}
```

```js
const NameInput = props => <input name="name" {...props} />;
export default withOnChange(NameInput);
```

- 渲染劫持: 通过抽象逻辑，统一对页面进行权限判断，按不同的条件进行页面渲染

```js
function withAdminAuth(WrappedComponent) {
  return class extends React.Component {
    constructor(props) {
      super(props);
      this.state = {
        isAdmin: false
      };
    }
    async componentWillMount() {
      const currentRole = await getCurrentUserRole();
      this.setState({
        isAdmin: currentRole === "Admin"
      });
    }
    render() {
      if (this.state.isAdmin) {
        return <Comp {...this.props} />;
      } else {
        return <div>您没有权限查看该页面，请联系管理员！</div>;
      }
    }
  };
}
```

## Redux 使用流程

- Redux 介绍

  - redux 是 react 应用的状态管理机制
  - 为了解决多页面多组件之间的数据通信
  - 单一数据源: 所有 state 最终维护在一个根级 Store
  - 状态只读: 数据无法被直接修改
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

## react hooks



## vallina react (VVM)
View-Model (VM): Component-related code that manages simple state, passes data directly onto View, potentially passes data directly back from View

View (V): How the visuals look (JSX, CSS)

## react + redux
"MVVM"/"MVC"

## react hook
- Only call Hooks at the top level. 
  - Don’t call Hooks inside loops, conditions, or nested functions
- Only call Hooks from React function components
state hook
effect hook
  - runs the effects after every render
  - have access to its props and state
  -  If returns a function, React will run it when  clean up:
  - replace: 
    - componentDidMount, componentDidUpdate, and componentWillUnmount

## side effects
data fetching
manually changing DOM

# pattern: render props

```js
<DataProvider render={data => (
  <h1>Hello {data.target}</h1>
)}/>
```