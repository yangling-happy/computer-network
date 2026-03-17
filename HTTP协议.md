# 简单的HTTP协议

HTTP 协议和 TCP/IP 协议族内的其他众多的协议相同，用于客户端和服务器之间的通信。

应用 **HTTP** 协议时，必定是一端担任客户端角色，另一端担任服务器端角色

请求报文：

<img width="904" height="431" alt="image" src="https://github.com/user-attachments/assets/62795363-fe09-444d-8643-2c7956f57ba0" />

响应报文：

<img width="797" height="424" alt="image" src="https://github.com/user-attachments/assets/8fc084ac-a11b-4813-94bf-c11e77144aa0" />




**HTTP**无状态，有了cookie再用HTTP协议通信可以管理状态。

http协议使用uri定位资源，指定uri有很多方式，比如把uri放在请求报文中里面



## http方法

- GET 
- POST 
- PUT （传输文件）
- HEAD 获取报文首部
- DELETE 删除文件
- OPTIONS 询问针对请求URI 知道的资源支持方法，比如一个服务端表示支持 get和head 方法
- TRACE 追踪路径
- CONNECT 用隧道协议（ssl ， tls）连接代理

### 持久连接

为解决上述 TCP 连接的问题，HTTP/1.1 和一部分的 HTTP/1.0 想出了持久连接（HTTP Persistent Connections，也称为 HTTP keep-alive 或HTTP connection reuse）的方法。持久连接的特点是，只要任意一端没有明确提出断开连接，则保持 TCP 连接状态。

### 管线化

同时并行发送多个请求

### cookie

保留无状态协议这个特征的同时又要解决类似的矛盾问题，于是引入了 Cookie 技术。Cookie 技术通过在请求和响应报文中写入 Cookie 信息来控制客户端的状态。

Cookie 会根据从服务器端发送的响应报文内的一个叫做 Set-Cookie 的首部字段信息，通知客户端保存 Cookie。当下次客户端再往该服务器发送请求时，客户端会自动在请求报文中加入 Cookie 值后发送出去。

服务器端发现客户端发送过来的 Cookie 后，会去检查究竟是从哪一个客户端发来的连接请求，然后对比服务器上的记录，最后得到之前的状态信息。
## HTTP 报文内的 HTTP信息
### 内容协商技术

- 服务器驱动协商（**Server-driven Negotiation**）

由服务器端进行内容协商。以请求的首部字段为参考，在服务器端自动处理。但对用户来说，以浏览器发送的信息作为判定的依据，并不一定能筛选出最优内容。

- 客户端驱动协商（**Agent-driven Negotiation**）

由客户端进行内容协商的方式。用户从浏览器显示的可选项列表中手动选择。**还可以利用 JavaScript 脚本在 Web 页面上自动进行上述选择。比如按 OS 的类型或浏览器类型，自行切换成 PC 版页面或手机版页面**。

- 透明协商（**Transparent Negotiation**）

是服务器驱动和客户端驱动的结合体，是由服务器端和客户端各自进行内容协商的一种方法。
