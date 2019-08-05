## 介绍一下你对浏览器内核的理解？

- 主要分成两部分：渲染引擎和 JS 引擎
- 渲染引擎
  - 取得网页的内容（HTML、XML、图像等等）
  - 整理讯息（例如加入 CSS 等）
  - 计算网页的显示方式，然后会输出至显示器
- JS 引擎

  - 解析和执行 javascript
  - 执行栈

- 主要线程
  - 事件触发线程
    - 消息队列： 微任务 + 宏任务
  - 网络异步线程
  - 定时器线程

## 常见的浏览器内核有哪些？

- Webkit 内核：Chrome, Safari, Edge, 360, opera
- Trident 内核：IE
- Gecko 内核：Firefox

# 跨标签页通讯

- 设置同域下共享的 localStorage
  - 监听 window.onstorage
  - 重复写入相同的值无法触发
  - 会受到浏览器隐身模式等的限制
- 通过父页面 window.open()和子页面 postMessage
- 设置共享 cookie 与不断轮询脏检查(setInterval)
