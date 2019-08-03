- What is CSS selector specificity and how does it work?
- What's the difference between "resetting" and "normalizing" CSS? Which would you choose, and why?
- Describe Floats and how they work.
- Describe z-index and how stacking context is formed.
- Describe BFC (Block Formatting Context) and how it works.
- What are the various clearing techniques and which is appropriate for what context?
- How would you approach fixing browser-specific styling issues?
- How do you serve your pages for feature-constrained browsers?
  - What techniques/processes do you use?
- What are the different ways to visually hide content (and make it available only for screen readers)?
- Have you ever used a grid system, and if so, what do you prefer?
- Have you used or implemented media queries or mobile specific layouts/CSS?
- Are you familiar with styling SVG?
- Can you give an example of an `@media` property other than `screen`?
- What are some of the "gotchas" for writing efficient CSS?
- What are the advantages/disadvantages of using CSS preprocessors?
  - Describe what you like and dislike about the CSS preprocessors you have used.
- How would you implement a web design comp that uses non-standard fonts?
- Explain how a browser determines what elements match a CSS selector.
- Describe pseudo-elements and discuss what they are used for.
- What does `* { box-sizing: border-box; }` do? What are its advantages?
- What is the CSS `display` property and can you give a few examples of its use?
- What's the difference between the "nth-of-type()" and "nth-child()" selectors?
- What's the difference between a relative, fixed, absolute and statically positioned element?
- Can you explain the difference between coding a web site to be responsive versus using a mobile-first strategy?
- Have you ever worked with retina graphics? If so, when and what techniques did you use?
- Is there any reason you'd want to use `translate()` instead of _absolute positioning_, or vice-versa? And why?

## 盒模型

- 页面渲染 DOM 元素所采用的 布局模型
  - margin + border + padding + content
- 可通过 box-sizing 进行设置。
- 根据计算宽高的方法可分为：
  - content-box (W3C 标准盒模型)
    - 宽高指 content
  - border-box (IE 盒模型)
  - - 宽高指 border + padding + content
- 正常模式下所有浏览器都是 W3C 盒子模型

# CSS 样式覆盖规则

- 由于继承而发生样式冲突时，最近祖先获胜。
- 继承的样式和直接指定的样式冲突时，直接指定的样式获胜
- 直接指定的样式发生冲突时，样式权值高者获胜
  - 选择器优先级： !important > 行内样式 > #id > .class > tag > \* > 继承 > 默认
  - 选择器 从右往左 解析
- 样式权值相同时，后者获胜。
- !important 的样式属性不被覆盖

## 块级元素 vs 行内元素

- 块级元素（block）
  - 占据其父元素（容器）的整个空间
  - 通常浏览器会在块级元素前后另起一个新行
  - 例子：<div>，<h1>~<h6>，<p>，<ul>
- 行内元素（inline）
  - 一个行内元素只占据它对应标签的边框所包含的空间
  - 包含其自身及其他行内元素
  - 例子：<span>，<a>，<input>，<button>
- 行内块元素（inline-block）
  - 和 inline 一样，但可以设宽高
- 区别
  - 一般行内元素只能包含数据和其他行内元素，块级元素可以包含行内元素和自身及其他块级元素。
  - 默认情况下块级元素占用一整行，而行内元素占据自身宽度空间
  - 宽高只对块级元素生效
  - 行内元素只能设置 padding 及左右 margin，上下 margin 无用
  - 设置 padding 时左右推开距离，上下会延申出去，但不会增加上下两行间的距离。
  - 如果给行内元素设定绝对定位，会隐形的改变 a 的 display 为 inline-block，此时就可以把 a 当成块元素一样设置宽高了。

## 垂直水平剧中方案

```html
<div class="father">
  <div class="child"></div>
</div>
```

- method 1: flexbox + margin

```css
.father {
  display: flex;
}
.child {
  margin: auto;
}
```

- method 2: flexbox + justify + align

```css
.father {
  display: flex;
  justify-content: center;
  align-items: center;
}
.child {
}
```

- method3: absolute + translate

```css
.father {
  position: relative;
}
.child {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

## 隐藏方案

```
{ display: none; }  <= 导致页面重绘，不占用空间
{ visibility: hidden; } <= 不会导致页面重绘，仍占用空间
{ height: 0; overflow: hidden; }
{ position: absolute; top: -999em; }
{ position: relative; top: -999em; }
{ position: absolute; visibility: hidden; }
```

## link 与 @import 的区别

- link 功能较多，可以定义 RSS，定义 Rel 等作用，而@import 只能用于加载 css
- 当解析到 link 时，页面会同步加载所引的 css，而@import 所引用的 css 会等到页面加载完才被加载
- link 可以使用 js 动态引入，@import 不行
