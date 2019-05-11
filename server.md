# Server

## 同源策略
源 = URI + 主机名+ 端口<br>
浏览器存在同源策略可防止 JavaScript 发起跨域请求<br>
目的是防止页面上的恶意脚本访问另一个网页上的敏感数据

## 跨域：规避同源策略
1. jsonp ，允许 script 加载第三方资源
2. cors 前后端协作设置请求头部
3. 反向代理
4. iframe 嵌套通讯，postmessage
