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
