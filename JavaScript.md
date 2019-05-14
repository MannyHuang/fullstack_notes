# JavaScript

## 数据类型

* 原始数据类型存在栈（stack）中
  * Undefined，Null, Boolean, Number, String，Symbol
* 引用数据类型存在堆(heap)中
  * Object, Array, Function

## 原始数据类型 和 引用数据类型 的区别 ？
* 存储位置不同
* 原始数据类型直接存储在栈(stack)中的简单数据段，占据空间小、大小固定，属于被频繁使用数据，所以放入栈中存储
* 引用数据类型存储在堆(heap)中的对象, 占据空间大、大小不固定。如果存储在栈中，将会影响程序运行的性能；
* 引用数据类型在栈中存储了指针，该指针指向堆中该实体的起始地址。当解释器寻找引用值时，会首先检索其在栈中的地址，取得地址后从堆中获得实体

## 内置函数(原生函数)
* String
* Number
* Boolean
* Object
* Function
* Array
* Date
* RegExp
* Error
* Symbol

## null 和 undefined 的区别？

* null 表示“没有值”
* undefined 表示一个变量声明了但没有初始化
* undefined不是一个有效的JSON，而null是
* undefined的类型(typeof)是undefined；
* null的类型(typeof)是object；*
* 在验证null时，一定要使用　=== ，因为 == 无法分别 null 和　undefined

## Javascript作用链域?
* 全局函数无法查看局部函数的内部细节，但局部函数可以查看其上层的函数细节，直至全局细节

## 如何确定this指向
1. 由 new 调用：绑定到新创建的对象
2. 由 call，apply，bind调用：绑定到指定的对象
3. 函数作为对象里的方法被调用：函数内的`this`是调用该函数的对象
4. 默认：在严格模式下绑定到 undefined ，否则绑定到全局对象。
5. 箭头函数忽略以上规则，直接继承外层函数调用的this 绑定

## bind, call, apply的区别
* bind, call, apply 都是改变调用者的this指向
* call 和 apply 都是在调用时生效
* bind 不是在调用时生效，而是返回一个新函数
* call和apply其实是一样的，区别就在于传参时参数是一个一个传或者是以一个数组的方式来传


```
var fruit = { name: 'Apple' }
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

## 原型继承
所有的JS对象都有一个prototype属性，指向它的原型对象。当试图访问一个对象的属性时，如果没有在该对象上找到，它还会搜寻该对象的原型，以及该对象的原型的原型，依次层层向上搜索，直到找到一个名字匹配的属性或到达原型链的末尾。


## 使用let, var和const有什么区别
* var没有block scope，只有function scope
* let 和 const 有 block scope
* var会将声明语句“提升”到当前作用域的顶部
* 这意味着变量可以在声明之前使用
* let和const不会使变量提升，提前使用会报错
* 用var重复声明不会报错，但let和const会。
* let和const的区别在于：let允许多次赋值，而const只允许一次。


## 创建对象有几种方法
* 字面量
```js
const obj = {a: 1}
```
* new和构造函数
```js
function Obj(val) {
    this.a = val
}

const obj = new Obj(1)
```
* Object.create
```js
const obj = Object.create({a: 1})
```

## 使用new创建一个对象经历了什么
```
function Test(){}
const test = new Test()
```

1. 创建一个新对象：
```
const obj = {}
```
2. 设置新对象的constructor属性为构造函数的名称，设置新对象的__proto__属性指向构造函数的prototype对象
```
obj.constructor = Test
obj.__proto__ = Test.prototype
```
3. 使用新对象调用函数，函数中的this被指向新实例对象
```
Test.call(obj)
```
4. 将初始化完毕的新对象地址，保存到等号左边的变量中


## 对象浅拷贝和深拷贝有什么区别

* 基本数据类型，拷贝是直接拷贝变量的值
* 引用类型拷贝的其实是变量的地址
* 浅拷贝：只对基本数据类型进行了拷贝，而对引用数据类型只是进行了引用的传递
* 深拷贝：对引用数据类型进行拷贝的时候，创建了一个新的对象，并且复制其内的成员变量
```
let o1 = {a: 1}
let o2 = o1

o2.a = 3
console.log(o1.a) // 3
```

## 怎么实现对象深拷贝
简单方法
```
let obj2 = JSON.parse(JSON.stringify(obj1))
```
递归方法
```
function deepCopy(s) {
    const d = {}
    for (let k in s) {
        if (typeof s[k] == 'object') {
            d[k] = deepCopy(s[k])
        } else {
            d[k] = s[k]
        }
    }
    return d
}
```


## ==和===的区别是什么
* `==`是抽象相等运算符，而`===`是严格相等运算符。
* `==`运算符是在进行必要的类型转换后，再比较。`===`运算符不会进行类型转换，所以如果两个值不是相同的类型，会直接返回`false`
* 使用`==`时，可能发生一些特别的事情，例如：
```js
1 == '1'; // true
1 == [1]; // true
1 == true; // true
0 == ''; // true
0 == '0'; // true
0 == false; // true
```

## 箭头函数和普通函数有什么区别
* 函数体内的`this`对象，就是定义时所在的对象，而不是使用时所在的对象，用`call` `apply` `bind`也不能改变`this`指向
* 不可以当作构造函数，也就是说，不可以使用`new`命令，否则会抛出一个错误。
* 不可以使用`arguments`对象，该对象在函数体内不存在。如果要用，可以用 `rest` 参数代替。
* 不可以使用`yield`命令，因此箭头函数不能用作 `Generator` 函数。
* 箭头函数没有原型对象`prototype`

## 闭包
* 闭包是指有权访问另一个函数作用域中的变量的函数。
```
function sayHi(name) {
    return () => {
       console.log(`Hi! ${name}`)
    }
}
const test = sayHi('xiaoming')
test() // Hi! xiaoming
```

* sayHi函数执行完毕，但是其活动对象也不会被销毁，因为test函数仍然引用着sayHi函数中的变量name
* 但因为闭包引用着sayHi函数的变量，导致另一个函数无法销毁，所以闭包使用过多，会占用较多的内存，这也是一个副作用。


## 自执行函数是什么?
* 声明一个匿名函数, 然后马上调用它
* 好处：
  * 截断作用域链，避免闭包造成引用变量无法释放
  * 创建独立的作用域，防止变量弥散到全局，以免各种js库冲突

自执行函数定义
```
(function () {
  // body
})();
```

 module pattern
```
var module = (function () {
  // private
  return {
    // public
  };
}());
```



## 如何判断数组与对象
```js
Array.isArray([]) // true
Array.isArray({}) // false
```

## 事件循环
事件循环是一个单线程循环，用于监视调用堆栈并检查是否有工作即将在任务队列中完成。如果调用堆栈为空并且任务队列中有回调函数，则将回调函数出队并推送到调用堆栈中执行。


## 3种事件绑定的方式
* 首选方法：事件监听
```
btn.addEventListener('click',function(){})
```

* 方法2：嵌入dom
  * 缺点：内容和逻辑不分离
```
<button onclick="func()">按钮</button>
```

* 方法3: 直接绑定
  * 缺点：一个事件只有一个事件处理
```
btn.onclick = function(){}
```
## cookies，sessionStorage 和 localStorage 的区别？

* localStorage 存储持久数据，浏览器关闭后数据不丢失
* sessionStorage 数据在当前窗口关闭后自动删除
* cookie 过期时间之前一直有效，即使窗口或浏览器关闭
  * 是为了标示用户身份而储存在客户端上的数据
  * cookie数据始终在同源的http请求中携带，在浏览器和服务器间来回传递

## WEB应用从服务器主动推送Data到客户端有那些方式？
* html5提供的Websocket
* 不可见的iframe (XHR长时间连接)

## 模块化开发怎么做？

* 使用立即执行函数，不暴露私有成员

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


