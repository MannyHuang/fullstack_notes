# Optimization

## 前端性能优化
* 减少 HTTP 请求次数
  * 在客户端重复利用数据
* 对源码和传输进行压缩
  * CSS/JS minify
  * 开启 Gzip 压缩
  * 压缩图片
* 使用 CDN 加速
* 合理控制 cookie 大小（每次请求都会包含 cookie）
* HTML优化
  * 将 CSS 放到顶部，JavaScript 放到尾部
* DOM优化
  * 用innerHTML代替DOM操作
  * 减少 DOM 操作次数
  * 避免不必要的重绘与重排
* CSS优化
  * 优化 CSS 选择器（从右向左匹配）
  * 当需要设置的样式很多时设置className而不是直接操作style
  * 使用 CSS Sprite
  * 避免使用CSS Expression（css表达式)又称Dynamic properties(动态属性)

## 防抖与节流
* 防抖(debounce)<br>
在函数需要频繁触发时，只有当有足够空闲的时间时，才执行一次。
例子：搜索框预览搜索结果

* 节流(thorttle)<br>
预定一个函数只有在大于等于执行周期时才执行，周期内调用不执行


## 页面大量图片，如何优化加载，优化用户体验
1. 图片懒加载。在页面的未可视区域添加一个滚动事件，判断图片位置与浏览器顶端的距离与页面的距离，如果前者小于后者，优先加载。
2. 如果为幻灯片、相册等，可以使用图片预加载技术，将当前展示图片的前一张和后一张优先下载。
3. 如果图片为css图片，可以使用CSSsprite，SVGsprite等技术。
4. 如果图片过大，可以使用特殊编码的图片，加载时会先加载一张压缩的特别厉害的缩略图，以提高用户体验。
5. 如果图片展示区域小于图片的真实大小，应在服务器端根据业务需要先进行图片压缩，图片压缩后大小与展示一致。




## 首屏时间、白屏时间
Performance 接口可以获取到当前页面中与性能相关的信息。<br>
该类型的对象可以通过调用只读属性 Window.performance 来获得。<br>
白屏时间：
```
performance.timing.responseStart - performance.timing.navigationStart
```
首屏时间
```
window.onload = () => {
    new Date() - performance.timing.responseStart
}
```
https://developer.mozilla.org/zh-CN/docs/Web/API/Performance

