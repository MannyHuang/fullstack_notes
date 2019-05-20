# Network

## OSI 模型
* 应用层: HTTP, FTP, POP3, SMTP, and SNMP
* 传输层: host之间通讯
  * TCP, UDP, HTTPS安全机制
* 网络层(ip): 连接网络
  * 路由器, IP, ICMP
* 数据链路层：连接host
  * 交换机, ethernet, arp
* 物理层


## HTTP 状态码

| 状态码 | 类别                             | 描述                   |
| ------ | -------------------------------- | ---------------------- |
| 1xx    | Informational（信息状态码）      | 接受请求正在处理       |
| 2xx    | Success（成功状态码）            | 请求正常处理完毕       |
| 3xx    | Redirection（重定向状态码）      | 需要附加操作已完成请求 |
| 4xx    | Client Error（客户端错误状态码） | 服务器无法处理请求     |
| 5xx    | Server Error（服务器错误状态码） | 服务器处理请求出错     |

```
100  Continue	继续，一般在发送post请求时，已发送了http header之后服务端将返回此信息，表示确认，之后发送具体参数信息
200  OK 		正常返回信息
201  Created  	请求成功并且服务器创建了新的资源
202  Accepted 	服务器已接受请求，但尚未处理
301  Moved Permanently  请求的网页已永久移动到新位置。
302 Found  		临时性重定向。
303 See Other  	临时性重定向，且总是使用 GET 请求新的 URI。
304  Not Modified 自从上次请求后，请求的网页未修改过。

400 Bad Request  服务器无法理解请求的格式，客户端不应当尝试再次使用相同的内容发起请求。
401 Unauthorized 请求未授权。
403 Forbidden  	禁止访问。
404 Not Found  	找不到如何与 URI 相匹配的资源。

500 Internal Server Error  最常见的服务器端错误。
503 Service Unavailable 服务器端暂时无法处理请求（可能是过载或维护）。
```

## RESTful
* REST 指的是一组约束条件和原则
* 满足这些约束条件和原则的设计就是 RESTful

* GET
  * 主要用于获取资源，能够发送参数，不过有限制，且参数都会以?开头的形 式附加在URL尾部。
  * 应该是幂等的，也就是说对一个资源不论发送多少次get请求都不会更改数据或造成破坏。
* POST
  * 主要用于添加资源，参数信息存放在请求报文的消息体中相对安全，且可发送较大信息
* PUT
  * 主要用于更新资源，
  * 大多数浏览器不支持put和delete，会自动将put和delete请求转化为get和post
  * 为了使用put和delete方法, 需要以post发送请求，在表单中使用隐藏域发送真正的请求。
  * put方法是幂等的
* DELETE
  * 主要用于删除资源，
  * Delete方法是幂等的

* 其它
  * HEAD：获取报文首部，与GET方法类似，只是不返回报文主体，一般用于验证URL是否有效。
  * OPTIONS：查询相应URL支持的HTTP方法。

## GET和POST的区别
* GET产生一个TCP数据包；POST产生两个TCP数据包。
* GET在浏览器回退时是无害的，而POST会再次提交请求。
* GET产生的URL地址可以被Bookmark，而POST不可以。
* GET请求会被浏览器主动cache，而POST不会，除非手动设置。
* GET请求只能进行url编码，而POST支持多种编码方式。
* GET参数通过URL传递，POST放在Request body中。
* GET请求参数会被完整保留在浏览器历史记录里，而POST中的参数不会被保留。
* GET请求在URL中传送的参数是有长度限制的，而POST没有。
* 对参数的数据类型，GET只接受ASCII字符，而POST没有限制。
* GET比POST更不安全，因为参数直接暴露在URL上，所以不能用来传递敏感信息。 



## 什么是Http协议无状态协议?怎么解决Http协议无状态协议?
* 无状态协议：对于事务处理没有记忆能力。
* 第二次http请求不知道上次http请求的状态
* 可以使用Cookie来解决无状态的问题
  * Cookie就相当于一个通行证，第一次访问的时候给客户端发送一个Cookie，
  * 当客户端再次来的时候，拿着Cookie(通行证)，那么服务器就知道这个是”老用户“

## Http与Https的区别
* HTTP 的URL 以http:// 开头，而HTTPS 的URL 以https:// 开头
* HTTP 是不安全的，而 HTTPS 是安全的
* HTTP 标准端口是80 ，而 HTTPS 的标准端口是443
* 在OSI 网络模型中，HTTP工作于应用层，而HTTPS 的安全传输机制工作在传输层
* HTTP 无法加密，而HTTPS 对传输的数据进行加密
* HTTP无需证书，而HTTPS 需要CA机构wosign的颁发的SSL证书


## HTTP请求所经历的7个步骤

* 建立TCP连接
  * 浏览器通过TCP与Web服务器建立连接
* 客户端 发送请求行
  * 浏览器就向服务器发送请求命令。
  * 例如：GET /sample/hello.jsp HTTP/1.1。
* 客户端 发送请求头
  * 以头信息的形式向服务器发送一些别的信息
  * 之后发送了一空白行来通知服务器表示结束发送。
* 服务器 发送状态行
  * 服务器回送 协议版本号和状态码。
  * 例如： HTTP/1.1 200 OK
* 发送响应头
  * 服务器向用户发送关于它自己的数据及被请求的文档。
* 发送响应数据
  * 以Content-Type所描述的格式发送用户请求的实际数据。
* 断TCP连接
  * 发送了请求数据后关闭TCP连接

## TCP三次握手
* 建立连接前，客户端和服务端需要通过握手来确认对:
* 客户端发送 syn(同步序列编号) 请求
  * 进入 syn_send 状态，等待确认
* 服务端接收并确认 syn 包后发送 syn+ack 包
  * 进入 syn_recv 状态
* 客户端接收 syn+ack 包后，发送 ack 包
  * 双方进入 established 状态

## TCP四次挥手

* 客户端 -- FIN --> 服务端， FIN—WAIT
* 服务端 -- ACK --> 客户端， CLOSE-WAIT
* 服务端 -- ACK,FIN --> 客户端， LAST-ACK
* 客户端 -- ACK --> 服务端，CLOSED

# Websocket
* Websocket 是一个 持久化的协议
* 基于 http
* 服务端可以 主动 push

## 如何处理不让别人盗用你的图片，访问你的服务器资源
* http header, 对refer做判断看来源是不是自己的网站，如果不是就拒绝
* 通过session校验，如果不通过特定服务生成cookie和session就不能请求得到资源

## http报头结构
* 请求的http报头结构：通用报头|请求报头|实体报头 
* 响应的http报头结构：通用报头|响应报头|实体报头

## Accept和Content-Type
* Accept代表客户端希望接受的数据类型
* Accept属于请求报头
  ```
  Accept: text/html
  Accept: image/*
  Accept: text/html, application/xhtml+xml, application/xml;q=0.9, */*;q=0
  ```
* Content-Type代表发送端（客户端|服务器）发送的实体数据的数据类型。
* Content-Type属于实体报头
  ```
  Content-Type:text/html
  ```


## What are the differences between Long-Polling, Websockets and Server-Sent Events?
## Explain the following request and response headers:
  * Diff. between Expires, Date, Age and If-Modified-...
  * Do Not Track
  * Cache-Control
  * Transfer-Encoding
  * ETag
  * X-Frame-Options
## What is domain pre-fetching and how does it help with performance?


## 代理服务器的作用

* 正向代理（客户端代理）
  * 即用户通过访问这层正向代理服务器，再由代理服务器去到原始服务器请求内容后，再返回给用户
  * 例如我们常使用的 VPN 就是一种常见的正向代理模式。
  * 代理服务器属于 客户端层
  * 代理服务器是 为用户服务，对于用户是透明的
  * 对内容服务器来说是 隐藏 的，内容服务器并无法分清访问是来自用户或者代理；
* 反向代理（服务端代理）
  * 户访问头条的反向代理网关，通过网关的一层处理和调度后，再由网关将访问转发到内部的服务器上，返回内容给用户
  * 代理服务器属于 服务端层
  * 通常代理服务器与内部内容服务器会隶属于同一内网或者集群
  * 代理服务器是 为内容服务器服务 的，对用户是隐藏的，用户不清楚自己访问的具体是哪台内部服务器
  * 能有效保证内部服务器的 稳定与安全

## 反向代理的好处

* 安全与权限:
  * 用户访问必须通过反向代理服务器，也就是便可以在做这层做统一的请求校验，过滤拦截不合法、危险的请求，从而就能更好的保证服务器的安全与稳定；
* 负载均衡: 能有效分配流量，最大化集群的稳定性，保证用户的访问质量

## 负载均衡
* 负载均衡是基于反向代理下实现的一种 流量分配 功能
* Nginx 实现: Upstream模块， 这样当用户访问 http://xxx 时，流量便会被按照一定的规则分配到upstream中的3台服务器上

## 介绍 HTTPS 握手过程

## HTTPS 握手过程中，客户端如何验证证书的合法性