# JavaScript

## 什么是 JavaScript？

- 一个
- single-threaded
- garbage-collected
- interepted or JIT compiled
- prototype-based
- multi-paradigmed
- dynamic
- weakly-typed 的语言, 且拥有一个
- non-blocking event loop

## 数据类型

- 原始数据类型存在栈（stack）中
  - Undefined，Null, Boolean, Number, String，Symbol
- 引用数据类型存在堆(heap)中
  - Object, Array, Function

## 原始数据类型 和 引用数据类型 的区别 ？

- 存储位置不同
- 原始数据类型直接存储在栈(stack)中的简单数据段，占据空间小、大小固定，属于被频繁使用数据，所以放入栈中存储
- 引用数据类型存储在堆(heap)中的对象, 占据空间大、大小不固定。如果存储在栈中，将会影响程序运行的性能；
- 引用数据类型在栈中存储了指针，该指针指向堆中该实体的起始地址。当解释器寻找引用值时，会首先检索其在栈中的地址，取得地址后从堆中获得实体

## 内置函数(原生函数)

- String
- Number
- Boolean
- Object
- Function
- Array
- Date
- RegExp
- Error
- Symbol

## null 和 undefined 的区别

- null 表示“没有值”
- undefined 表示一个变量声明了但没有初始化
- undefined 不是一个有效的 JSON，而 null 是
- undefined 的类型(typeof)是 undefined
- null 的类型(typeof)是 object
- 在验证 null 时，一定要使用　=== ，因为 == 无法分别 null 和　 undefined

## Javascript 作用链域?

- 全局函数无法查看局部函数的内部细节
- 局部函数可以查看其上层的函数细节，直至全局细节

## 如何确定 this 指向

1. 由 new 调用：绑定到新创建的对象
2. 由 call，apply，bind 调用：绑定到指定的对象
3. 函数作为对象里的方法被调用：函数内的`this`是调用该函数的对象
4. 默认：在严格模式下绑定到 undefined ，否则绑定到全局对象。
5. 箭头函数忽略以上规则，直接继承外层函数调用的 this 绑定
6. 在事件中，this 指向触发这个事件的对象

## bind, call, apply 的区别

- bind, call, apply 都是改变调用者的 this 指向
- call 和 apply 都是在调用时生效
- bind 不是在调用时生效，而是返回一个新函数
- call 和 apply 唯一区别就在于传参的形式
  - call:一个一个传
  - apply: 一个数组的方式来传
- 是一个一个传或者是以一个数组的方式来传

```js
let fruit = { name: 'Apple' }
function showDetails(size, price) {
  console.log(this.name + ' ' + size + ': $' + price + '/kg')
}

showDetails.apply(fruit, ['small', 1])
-> Apple small: $1/kg

showDetails.call(fruit, 'medium', 5)
-> Apple medium: $5/kg

var bound = showDetails.bind(fruit, 'large', 10)
bound()
-> Apple large: $10/kg

showDetails.bind(fruit, 'large', 10)()
-> Apple large: $10/kg

var bound = showDetails.bind(fruit)
bound('medium', 7)
-> Apple medium: $7/kg
```

## 原型链是什么？

- 所有的 JS 对象都有一个 prototype 属性，指向它的原型对象。
- 当试图访问一个对象的属性时，如果没有在该对象上找到，它还会搜寻该对象的原型，以及该对象的原型的原型，依次层层向上搜索，直到找到一个名字匹配的属性或到达原型链的末尾。
- 创建的每个新对象实体中并没有一份属于自己的原型副本。当我们修改原型时，与之相关的对象也会继承这一改变。

## 原型 / 构造函数 / 实例

```js
const instance = new Object(); // 实例
const prototype = instance.__proto__; // 原型
const constructor = prototype.constructor; // 构造函数
```

## 执行上下文

- 它包含 3 个部分:

  - this 指向
  - 变量对象(VO)：存储着该执行上下文中的所有 变量和函数声明(不包含函数表达式)

    - 活动对象 (AO): 当变量对象所处的上下文为 active EC 时，称为活动对象。

  - 作用域链(词法作用域)

    - 声明提前: 一个声明在函数体内都是可见的, 函数优先于变量
    - 非匿名自执行函数，函数变量为 只读 状态，无法修改

```js
let foo = function() {
  console.log(1);
};
(function foo() {
  foo = 10; // 由于foo在函数中只为可读，因此赋值无效
  console.log(foo);
})();

// 结果打印：  ƒ foo() { foo = 10 ; console.log(foo) }
```

- ec 分为 3 种类型:

  - 全局执行上下文
  - 函数执行上下文
  - eval 执行上下文

- 代码执行过程:
  - 创建 全局上下文 (global EC)
  - 全局执行上下文 (caller) 逐行 自上而下执行。
  - 遇到函数时，函数执行上下文 (callee) 被 push 到执行栈顶层
  - 函数执行上下文被激活，成为 active EC, 开始执行函数中的代码，caller 被挂起
  - 函数执行完后，callee 被 pop 移除出执行栈，控制权交还全局上下文 (caller)，继续执行

## 闭包

- 闭包是指可以访问另一个函数作用域中变量的函数
- 闭包属于一种特殊的作用域，称为 静态作用域
- 可以理解为父函数被销毁 的情况下，返回出的子函数的[[scope]]中仍然保留着父级的变量对象和作用域链，因此可以继续访问到父级的变量对象
- 利用闭包可以突破作用链域，将函数内部的变量和方法传递到外部。
- 闭包的特征：
  1. 函数内再嵌套函数
  2. 内部函数可以引用外层的参数和变量
  3. 参数和变量不会被垃圾回收机制回收

```
function sayHi(name) {
    return () => {
       console.log(`Hi! ${name}`)
    }
}
const test = sayHi('xiaoming')
test() // Hi! xiaoming
```

- sayHi 函数执行完毕，但是其活动对象也不会被销毁，因为 test 函数仍然引用着 sayHi 函数中的变量 name
- 但因为闭包引用着 sayHi 函数的变量，导致另一个函数无法销毁，所以闭包使用过多，会占用较多的内存，这也是一个副作用。

## 自执行函数是什么?

- 声明一个匿名函数, 然后马上调用它
- 好处：
  - 截断作用域链，避免闭包造成引用变量无法释放
  - 创建独立的作用域，防止变量弥散到全局，以免各种 js 库冲突

自执行函数定义

```js
(function() {
  // body
})();
```

module pattern

```js
var module = (function() {
  // private
  return {
    // public
  };
})();
```

## 使用 let, var 和 const 有什么区别

- var 没有 block scope，只有 function scope
- let 和 const 有 block scope
- var 会将声明语句“提升”到当前作用域的顶部
- 这意味着变量可以在声明之前使用
- let 和 const 不会使变量提升，提前使用会报错
- 用 var 重复声明不会报错，但 let 和 const 会。
- let 和 const 的区别在于：let 允许多次赋值，而 const 只允许一次。

## 创建对象有几种方法

- 字面量

```js
const obj = { a: 1 };
```

- new 和构造函数

```js
function Obj(val) {
  this.a = val;
}

const obj = new Obj(1);
```

- Object.create

```js
const obj = Object.create({ a: 1 });
```

## 使用 new 创建一个对象经历了什么

- 创建一个新对象
- 设置新对象的**proto**属性指向构造函数的 prototype 对象
- 使用新对象调用函数，函数中的 this 被指向新实例对象
- 如果结果是 Object 类型，return object

```js
function _new(fn, ...arg) {
  const obj = Object.create(fn.prototype);
  const ret = fn.apply(obj, arg);
  return ret instanceof Object ? ret : obj;
}
```

## 对象浅拷贝 vs 深拷贝

- 基本数据类型，拷贝是直接拷贝变量的值
- 引用类型拷贝的其实是变量的地址
- 浅拷贝：只对基本数据类型进行了拷贝，而对引用数据类型只是进行了引用的传递
  - Object.assign
  - 展开运算符(...)
- 深拷贝：对引用数据类型进行拷贝的时候，创建了一个新的对象，并且复制其内的成员变量

```js
let o1 = { a: 1 };
let o2 = o1;

o2.a = 3;
console.log(o1.a); // 3
```

## 怎么实现对象深拷贝

简单方法

```js
let obj2 = JSON.parse(JSON.stringify(obj1));
```

递归方法

```js
function deepCopy(obj) {
  const result = {};
  for (const key in obj) {
    if (typeof obj[key] == "object") {
      result[key] = deepCopy(obj[key]);
    } else {
      result[key] = obj[key];
    }
  }
  return result;
}
```

## ==和===的区别是什么

- `==`是抽象相等运算符，而`===`是严格相等运算符。
- `==`运算符是在进行必要的类型转换后，再比较。`===`运算符不会进行类型转换，所以如果两个值不是相同的类型，会直接返回`false`
- 引用类型在比较运算符时候,隐式转换会调用本类型 toString 或 valueOf 方法
- 使用`==`时，可能发生一些特别的事情，例如：

```js
1 == "1"; // true
1 == [1]; // true
1 == true; // true
0 == ""; // true
0 == "0"; // true
0 == false; // true
```

## Array 常用函数

- map: 遍历数组，返回回调返回值组成的新数组
- forEach: 无法 break，可以用 try/catch 中 throw new Error 来停止
- filter: 过滤
- some: 有一项返回 true，则整体为 true
- every: 有一项返回 false，则整体为 false
- join: 通过指定连接符生成字符串
- push / pop: 末尾推入和弹出，改变原数组， 返回推入/弹出项
- unshift / shift: 头部推入和弹出，改变原数组，返回操作项
- sort(fn) / reverse: 排序与反转，改变原数组
- concat: 连接数组，不影响原数组， 浅拷贝
- slice(start, end): 返回截断后的新数组，不改变原数组
- splice(start, number, value...): 返回删除元素组成的数组，value 为插入项，改变原数组
- indexOf / lastIndexOf(value, fromIndex): 查找数组项，返回对应的下标
- reduce / reduceRight(fn(prev, cur)， defaultPrev): 两两执行，prev 为上次化简函数的 return 值，cur 为当前值(从第二项开始)

## 箭头函数和普通函数有什么区别

- 箭头函数体内的`this`对象，就是定义时所在的对象，而不是使用时所在的对象，用`call` `apply` `bind`也不能改变`this`指向
- 不可以当作构造函数，也就是说，不可以使用`new`命令，否则会抛出一个错误。
- 不可以使用`arguments`对象，该对象在函数体内不存在。如果要用，可以用 `rest` 参数代替。
- 不可以使用`yield`命令，因此箭头函数不能用作 `Generator` 函数。
- 箭头函数没有原型对象`prototype`

## 如何判断数组与对象

```js
Array.isArray([]); // true
Array.isArray({}); // false
```

## 事件循环

事件循环是一个单线程循环，用于监视调用堆栈并检查是否有工作即将在任务队列中完成。如果调用堆栈为空并且任务队列中有回调函数，则将回调函数出队并推送到调用堆栈中执行。

## 3 种事件绑定的方式

- 首选方法：事件监听

```
btn.addEventListener('click',function(){})
```

- 方法 2：嵌入 dom
  - 缺点：
    - 内容和逻辑不分离
    - 一个事件只有一个事件处理

```
<button onclick="func()">按钮</button>
```

- 方法 3: 获得 dom 元素后绑定 （和方法 2 等价
  - 缺点：一个事件只有一个事件处理

```
btn.onclick = function(){}
```

## cookies，sessionStorage 和 localStorage 的区别？

- localStorage 存储持久数据，浏览器关闭后数据不丢失
- sessionStorage 数据在当前窗口关闭后自动删除
- cookie 过期时间之前一直有效，即使窗口或浏览器关闭
  - 是为了标示用户身份而储存在客户端上的数据
  - cookie 数据始终在同源的 http 请求中携带，在浏览器和服务器间来回传递

## WEB 应用从服务器主动推送 Data 到客户端有那些方式？

- html5 提供的 Websocket
- 不可见的 iframe (XHR 长时间连接)

## 模块化开发怎么做？

- 使用立即执行函数，不暴露私有成员

  ```
  const module1 = (function() {
        let _count = 0;
  　　　　var m1 = function(){};
  　　　　var m2 = function(){};
  　　　　return {
  　　　　　　m1 : m1,
  　　　　　　m2 : m2
  　　　　};
  　　})();
  ```

## Ajax 解决浏览器缓存问题？

- RequestHeader 加上 ("If-Modified-Since","0")
- RequestHeader 加上 ("Cache-Control","no-cache")
- URL 后面加上一个随机数："fresh=" + Math.random();
- URL 后面加上时间戳："nowtime=" + new Date().getTime();

## JS 中有一个函数，执行对象查找时永远不会去查找原型，这个函数是？

- hasOwnProperty 返回一个布尔值，指出一个对象是否具有指定名称的属性
- 此方法无法检查该对象的原型链中是否具有该属性；该属性必须是对象本身的一个成员。

## javascript 代码中的"use strict";是什么意思 ?

- ES5 添加的新运行模式
- 消除 Javascript 语法的一些不合理行为
- 不能在意外的情况下给全局变量赋值
- 全局变量的显示声明,函数必须声明在顶层
- 不允许在非函数代码块内声明函数

## eval 是做什么的？

- 它的功能是把对应的字符串解析成 JS 代码并运行
- 应该避免使用 eval
  - 不安全
  - 非常耗性能

## 什么是模块化开发？

- Node / browser: use es6 module system
  - syntax: import/output 
  - support async and sync
- old NodeJs: use commonjs module
  - syntax: require / module.exports
  - sync
  - dependency determined at runtime
- old browser: amd
  - syntax: define/require
  - async
  - dependency determined at runtime
- old browser: cmd
  - similar to amd
- umd = commonJs + amd
  - if nodeJs env: use commonJs
  - if function named 'define' exist: use amd
  - else use window or global object

  
## requre 与 import 的区别？

- require 支持 动态导入，import 不支持，正在提案 (babel 下可支持)
- require 是 同步 导入，import 属于 异步 导入
- require 是 值拷贝，导出值变化不会影响导入值；import 指向 内存地址，导入值会随导出值而变化

# AMD 与 CMD 的区别

- AMD (Asynchronous Module Definition)

  - 所有的模块将被异步加载，模块加载不影响后面语句运行
  - 所有依赖某些模块的语句均放置在回调函数中。

- 对于依赖的模块，AMD 是提前执行，CMD 是延迟执行。
- CMD 推崇依赖就近，AMD 推崇依赖前置

```
// CMD
define(function(require, exports, module) {
    var a = require('./a')
    a.doSomething()
    var b = require('./b') // 依赖可以就近书写
    b.doSomething()
    // ...
})
```

```
// AMD 默认推荐
define(['./a', './b'], function(a, b) { // 依赖必须一开始就写好
    a.doSomething()
    b.doSomething()
})
```

## Javascript 如何实现继承？

1、构造继承：用构造函数实现继承

```js
```

2、原型继承
3、实例继承
4、拷贝继承

原型 prototype 机制或 apply 和 call 方法去实现较简单，建议使用构造函数与原型混合方式。

    function Parent(){
    	this.name = 'wang';
    }

    function Child(){
    	this.age = 28;
    }
    Child.prototype = new Parent();//继承了Parent，通过原型

    var demo = new Child();
    alert(demo.age);
    alert(demo.name);//得到被继承的属性

## 创建对象的几种方式？

- 对象字面量的方式

```
let person = {
  name : "Anand",
  getName : function (){
   return this.name
  }
}
```

- function 构造函数

```
function Person(name){
  this.name = name
  this.getName = function(){
    return this.name
  }
}
```

- 用原型方式来创建

```
function Person(){};
Person.prototype.name = "Anand";
```

- Function/Prototype combination

```
function Person(name){
  this.name = name;
}
Person.prototype.getName = function(){
  return this.name
}
```

## 运算中的类型转换

- -、\*、/、% ：一律转换成数值后计算
- +：

  - 数字 + 字符串 = 字符串， 运算顺序是从左到右
  - 数字 + 对象， 优先调用对象的 valueOf -> toString
  - 数字 + boolean/null -> 数字
  - 数字 + undefined -> NaN

- [1].toString() === '1'
- NaN !== NaN 、+undefined 为 NaN

# 浮点计算不准确

- binary 无法准确表达浮点数

```
console.log(0.1 + 0.2 == 0.3);
// false
```

# callback 执行顺序

console.log('one');
setTimeout(function () {
console.log('two');
}, 0);
Promise.resolve().then(function () {
console.log('three');
})
console.log('four');

# 不同 promise 的区别

doSomething().then(function () {
return doSomethingElse();
});
doSomething().then(function () {
doSomethingElse();
});
doSomething().then(doSomethingElse());
doSomething().then(doSomethingElse);

## 函数柯里化 （currying）

- 把接受多个参数的函数变换成接受单一参数的函数
- 返回接受余下的参数而且返回结果的新函数

```
const add = function add(x) {
	return function (y) {
		return x + y
	}
}

const add1 = add(1)

add1(2) === 3
```

## array 常用函数

- map: 遍历数组，返回回调返回值组成的新数组
- forEach: 无法 break，可以用 try/catch 中 throw new Error 来停止
- filter: 过滤
- some: 有一项返回 true，则整体为 true
- every: 有一项返回 false，则整体为 false
- join: 通过指定连接符生成字符串
- push / pop: 末尾推入和弹出，改变原数组， 返回推入/弹出项
- unshift: 头部推入, 改变原数组，返回列表长度
- shift: 头部弹出, 改变原数组，返回列表长度
- sort(fn) / reverse: 排序与反转，改变原数组
- concat: 连接数组，不影响原数组， 浅拷贝
- slice(start, end): 返回截断后的新数组，不改变原数组
- splice(start, number, value...): 返回或替换元素，value 为插入项，改变原数组
- indexOf / lastIndexOf(value, fromIndex): 查找数组项，返回对应的下标
- reduce / reduceRight(fn(prev, cur)， defaultPrev): 两两执行，prev 为上次化简函数的 return 值，cur 为当前值(从第二项开始)

## 异步解决方案

- Promise
- generator
- await / async
  - 是 generator 的语法糖， babel 中是基于 promise 实现。

## generator 是什么？

- 异步解决方案的一种
- yield: 暂停代码
- next(): 继续执行代码

```
function* helloWorld() {
  yield 'hello';
  yield 'world';
  return 'ending';
}

const generator = helloWorld();

generator.next()  // { value: 'hello', done: false }

generator.next()  // { value: 'world', done: false }

generator.next()  // { value: 'ending', done: true }

generator.next()  // { value: undefined, done: true }
```

## Memory Leak
- global variables
- event listeners
- setInterval

## Explain event delegation.

## Explain how prototypal inheritance works.

## What language constructions do you use for iterating over object properties and array items?

## What's the difference between host objects and native objects?

## Explain the difference between: `function Person(){}`, `var person = Person()`, and `var person = new Person()`?

## Explain the differences on the usage of `foo` between `function foo() {}` and `var foo = function() {}`

## Explain `Function.prototype.bind`.

## What's the difference between feature detection, feature inference, and using the UA string?

## Describe event bubbling.

## Describe event capturing.

## What's the difference between an "attribute" and a "property"?

## Explain the difference between mutable and immutable objects.

## What is an example of an immutable object in JavaScript?

## What are the pros and cons of immutability?

## What is event loop?

## What is the difference between call stack and task queue?

## What are the differences between ES6 class and ES5 function constructors?

## What advantage is there for using the arrow syntax for a method in a constructor?

## Can you give an example of a curry function and why this syntax offers an advantage?

## Why you might want to create static class members?

## 什么是执行上下文(EC)

## 原型 / 构造函数 / 实例 之间的关系

## 原型链

## 继承

- 最优化: 圣杯模式
- '''
  var inherit = (function(c,p){
  var F = function(){};
  return function(c,p){
  F.prototype = p.prototype;
  c.prototype = new F();
  c.uber = p.prototype;
  c.prototype.constructor = c;
  }
  })();
  '''

- ES6 的语法糖 class / extends

## 浏览器架构

- 用户界面
- 主进程
- 内核
  - 渲染引擎
  - JS 引擎
    - 执行栈
  - 事件触发线程
    - 消息队列
      - 微任务
      - 宏任务
  - 网络异步线程
  - 定时器线程

## 浏览器 Event Loop 的执行顺序

- 同步代码 => microstask => macrotask
- 宏任务 macrotask
  - script / setTimout / IO / UI Rendering
- 微任务 microtask
  - promise / ajax

## Node 的 Event Loop

- timer 阶段: 执行到期的 setTimeout / setInterval 队列回调
- I/O 阶段: 执行上轮循环残流的 callback
- idle, prepare
- poll: 等待回调
  - 执行回调
  - 执行定时器
    - 如有到期的 setTimeout / setInterval， 则返回 timer 阶段
    - 如有 setImmediate，则前往 check 阶段
- check
  - 执行 setImmediate
- close callbacks

## Web worker

- 现代浏览器为 JavaScript 创造的 多线程环境
- 可以新建并将部分任务分配到 worker 线程并行运行
- 两个线程可 独立运行，互不干扰，
- 可通过自带的 消息机制 相互通信

'''
// 创建 worker
const worker = new Worker('work.js');

// 向主进程推送消息
worker.postMessage('Hello World');

// 监听主进程来的消息
worker.onmessage = function (event) {
console.log('Received message ' + event.data);
}
'''

## 内存泄露的原因

- 意外的全局变量: 无法被回收
- 定时器: 未被正确关闭，导致所引用的外部变量无法被释放
- 事件监听: 没有正确销毁 (低版本浏览器可能出现)
- 闭包: 会导致父级中的变量无法被释放
- dom 元素被删除时，内存中的引用未被正确清空

## 判断是否是数组 Array 类型的方法

```js
var arr = [];
arr.constructor === Array;
arr instanceof Array; // true
Object.prototype.toString.call(arr) === "[object Array]"; // toString
Array.isArray(arr); // es5
```

## 介绍下 Set、Map、WeakSet 和 WeakMap 的区别？

## 介绍下深度优先遍历和广度优先遍历，如何实现？

## 请分别用深度优先思想和广度优先思想实现一个拷贝函数

## ES5/ES6 的继承除了写法以外还有什么区别？

## setTimeout、Promise、Async/Await 的区别？

## 第 12 题：JS 异步解决方案的发展历程以及优缺点。

## 第 13 题：Promise 构造函数是同步执行还是异步执行，那么 then 方法呢？

## 简单讲解一下 http2 的多路复用

## 全局作用域中，用 const 和 let 声明的变量不在 window 上，那到底在哪里？如何去获取？

在正常作用域里就可以获取

## cookie 和 token 都存放在 header 中，为什么不会劫持 token？

浏览器每次访问时不会自动携带 token

## Virtual DOM 真的比操作原生 DOM 快吗？谈谈你的想法

## 同源策略

源 = URI + 主机名+ 端口<br>
浏览器存在同源策略可防止 JavaScript 发起跨域请求<br>
目的是防止页面上的恶意脚本访问另一个网页上的敏感数据

## 跨域：规避同源策略

1. jsonp ，允许 script 加载第三方资源
2. cors 前后端协作设置请求头部
3. 反向代理
4. iframe 嵌套通讯，postmessage

## JSONP 使用以及需要注意的安全问题

- JSONP: 利用<script>标签不受跨域限制的特点
- 功能限制：只能支持 get 请求
- 安全问题：xss
  ```html
  http://127.0.0.1/getUsers.php?callback=
  <script>
    alert(/xss/);
  </script>
  ```
- 安全问题：csrf
  ```js
  <script>
  function wooyun(v){
      alert(v.username);
  }
  </script>
  <script src="http://js.login.360.cn/?o=sso&m=info&func=wooyun"></script>
  ```

```js
function jsonp(url, jsonpCallback, success) {
  const script = document.createElement("script");
  script.src = url;
  script.async = true;
  script.type = "text/javascript";
  window[jsonpCallback] = function(data) {
    success && success(data);
  };
  document.body.appendChild(script);
}
```

## Generator

- generator is a function that can stop midway and then continue from where it stopped
- simplify the task of writing iterators.
- produces a sequence of results instead of a single value
- a function which returns an object on which you can call next()

## History

- 1990 Tim Berners-Lee
  create first browser and server
- 1991 High performance computing act
  provide funding for first popular browser: Mosaic
- 1993 Mosaic released on Unix, Mac, Windows
  no Js yet, just DOM (not standardized)
- 1994 - 2000 netscape dominated
  tried to make things more interactive
  java on the web? no
- 1995 Brendan Eich put scheme on browser (Js born)
  first version of Js born (called Mocha)
  created in 10 days
  syntax like Java
  firt class function like Scheme
  dynamic typing like lisp
  prototypes like self
  second version call liveScript
  by the end of the year: JavaScript
- 1996 Microsft market JavaScript as JScript
- 1997 First EcmaScript standarization
  no strict equality, regex, trycatch
- 1999 ES3
  yes strict equality,
- 2003 Douglas Crockford
  created JSON
- 2000s ES3.1 & ES4 happend at the same time
- 2006 JQuery born
  first mature library to bridge the gap between browsers
- 2007 Atwood's law
  any application that can be written in JavaSciprt,
  will eventually be written in JavaScript
- 2008 chrome and V8 engine born
- 2009 Ryan Dahl invented NodeJs
- 2009 ES5 based on ES3.1
  strict mode, json support
- 2010 frameworks for SPA
  angular: declaritive
  backbone: imperitive
  coffescript: made transpiling popular
  underscore: utility library
- 2015 ES6
  babel
  typescript
  react
