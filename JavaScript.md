# JavaScript

## 数据类型
1. Undefined 
2. Null 
3. Boolean 
4. Number
5. String 
6. Object
7. symbol(ES6新增)

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


## 如何判断数组与对象
```js
Array.isArray([]) // true
Array.isArray({}) // false
```

## 事件循环
事件循环是一个单线程循环，用于监视调用堆栈并检查是否有工作即将在任务队列中完成。如果调用堆栈为空并且任务队列中有回调函数，则将回调函数出队并推送到调用堆栈中执行。


## 事件绑定的方式
* 嵌入dom
```
<button onclick="func()">按钮</button>
```

* 直接绑定
```
btn.onclick = function(){}
```

* 事件监听
```
btn.addEventListener('click',function(){})
```