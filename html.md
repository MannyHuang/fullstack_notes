## 页加载流程

* 浏览器一边下载 HTML 网页，一边开始解析
* 解析过程中，浏览器发现script元素，就暂停解析，把网页渲染的控制权转交给 JavaScript 引擎
* 如果script元素引用了外部脚本，就下载该脚本再执行，否则就直接执行代码。
* JavaScript 引擎执行完毕，控制权交还渲染引擎，恢复解析 HTML 网页。


## 异步加载JS的方式有哪些？

* 将script标签放到body底部 (本质还是同步的)
* defer: 给script标签设置defer属性，将脚本文件设置为延迟加载
  * 会再开启一个线程去下载js文件，同时继续解析HTML文档，等等HTML全部解析完毕DOM加载完成之后，再去执行加载好的js文件
* async: 给script标签设置async属性
  * 也是会开启一个线程去下载js文件，但和defer不同的时，它会在下载完成后立刻执行
* 创建script，插入到DOM中，加载完毕后callBack


## 浏览器的渲染过程
1. 解析HTML生成DOM树。
2. 解析CSS生成CSSOM规则树。
3. 将DOM树与CSSOM规则树合并在一起生成渲染树。
4. 遍历渲染树开始布局，计算每个节点的位置大小信息。
5. 将渲染树每个节点绘制到屏幕。

## img中的alt和元素的title属性作用
* img的alt属性
  * 如果无法显示图像，浏览器将显示alt指定的内容
* 元素title属性
  * 在鼠标移到元素上时显示title的内容

## href和src区别
* href 
  * href标识超文本引用，用在link和a等元素上
  * href是在当前元素和引用资源之间建立联系
* src 
  * src表示引用资源，替换当前元素，用在img，script，iframe上
  * 当浏览器解析到src ，会暂停其他资源的下载和处理，直到将该资源加载、编译、执行完毕，图片和框架等也如此，

## label标签有什么作用
`label` 标签通常是写在表单内，它关联一个控件，使用 `label` 可以实现点击文字选取对应的控件。
```html
<input type="checkbox" id="test">
<label for="test" >test</label>
```



## iframe框架有那些优缺点
#### 优点：
* iframe能够原封不动的把嵌入的网页展现出来。
* 如果有多个网页引用iframe，那么你只需要修改iframe的内容，就可以实现调用的每一个页面内容的更改，方便快捷。
#### 缺点：
* 搜索引擎的爬虫程序无法解读这种页面
* 框架结构中出现各种滚动条
* iframe页面会增加服务器的http请求


## Ascii、GBK、UTF、Unicode
* Ascii（1个字节）
* GBK是国内的编码标准（2个字节）
* Unicode是国际编码标准（2个字节）
* UTF是Unicode实现的另一个标准
* UTF-8就是每次8个位传输数据： 联网上使用最广的一种unicode的实现方式
* UTF-8最大的一个特点，就是它是一种变长的编码方式。
  * 它可以使用1~4个字节表示一个符号，根据不同的符号而变化字节长度，当字符在ASCII码的范围时，就用一个字节表示，保留了ASCII字符一个字节的编码做为它的一部分，注意的是unicode一个中文字符占2个字节，而UTF-8一个中文字符占3个字节）。
* 从unicode到utf-8并不是直接的对应，而是要过一些算法和规则来转换。