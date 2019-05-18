
## XSS (Cross-site scripting)
### XSS是什么
* 能注入恶意的HTML/JS代码到提供给其它用户使用的页面中
* 可以利用XSS漏洞旁路掉访问控制，例如同源策略


```
示例：
<script>alert(document.cookie)</script>
```
 
### 防御
* 过滤JavaScript 事件的标签。例如 "onclick=", "onfocus" 等等
* 过滤特殊的Html标签， 例如: script, iframe
* 对数据进行Html Encode 处理
* 表单数据规定值的类型，例如：年龄应为只能为int、name只能为字母数字组合。。。。
* cookie 设置 httpOnly


## CSRF（Cross-site request forgery）
### CSRF是什么
* 而CSRF则通过伪装来自受信任用户的请求来利用受信任的网站

### 特点
* 利用网站对用户标识的信任
* 欺骗用户的浏览器发送HTTP请求给目标站点

### 防御
* 检查token，确保用户请求来自客户端正常操作
* 检查referer， 确保HTTP request同源
* 对于用户修改删除等操作最好都使用post操作 。
* 避免全站通用的cookie，严格设置cookie的域。


