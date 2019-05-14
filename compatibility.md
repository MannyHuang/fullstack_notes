
## IE与其他浏览器不一样的特性？


* 事件处理机制：
  * IE是事件冒泡
  * Firefox同时支持捕获型事件和冒泡型事件
  
* 事件不同之处
  * Firefox触发事件的元素被认为是目标（target）。
  * 在 IE 中，目标包含在 event 对象的 srcElement 属性；

* 获取字符代码
  * 如果按键代表一个字符（shift、ctrl、alt除外），IE 的 keyCode 会返回字符代码（Unicode），DOM 中按键的代码和字符是分离的，要获取字符代码，需要使用 charCode 属性

* 阻止某个事件的默认行为
  * IE 中阻止某个事件的默认行为，必须将 returnValue 属性设置为 false，Mozilla 中，需要调用 preventDefault() 方法；

* 停止事件冒泡
  * IE 中阻止事件进一步冒泡，需要设置 cancelBubble 为 true
  * Mozzilla 中，需要调用 stopPropagation()