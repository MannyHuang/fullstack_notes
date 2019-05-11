
## XSS
### XSS是什么
* 能注入恶意的HTML/JS代码到提供给其它用户使用的页面中
* 可以利用XSS漏洞旁路掉访问控制，例如同源策略


```
示例：
<script>alert(document.cookie)</script>
```
 
### 如何防范
* 过滤JavaScript 事件的标签。例如 "onclick=", "onfocus" 等等
* 过滤特殊的Html标签， 例如: script, iframe
* 对数据进行Html Encode 处理
* 表单数据规定值的类型，例如：年龄应为只能为int、name只能为字母数字组合。。。。

