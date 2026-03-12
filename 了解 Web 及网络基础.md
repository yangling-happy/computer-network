# HTTP( HyperText Transfer Protocol )
>HTTP 通常被译为超文本传输协议，但这种译法并不严谨。严谨的译名应该
为“超文本转移协议”。但是前一译法已约定俗成，本书将会沿用。有兴趣的读者
可参考图灵社区的相关讨论 ：http://www.ituring.com.cn/article/1817。——译者注

最初的HTTP:

当年 HTTP 协议的出现主要是为了解决文本传输的难题。由于协议本
身非常简单，于是在此基础上设想了很多应用方法并投入了实际使
用。现在 HTTP 协议已经超出了 Web 这个框架的局限，被运用到了
各种场景里。


网络基础 TCP/IP:

通常使用的网络（包括互联网）是在 TCP/IP 协议族的基础上运作
的。而 HTTP 属于它内部的一个子集。 (http是tcp/ip 协议下的)

>TCP/IP 是互联网相关的各类协议族的总称:像这样把与互联网相关联的协议集合起来总称为 TCP/IP。也有说法
认为，TCP/IP 是指 TCP 和 IP 这两种协议。还有一种说法认为，TCP/
IP 是在 IP 协议的通信过程中，使用到的协议族的统称。


TCP/IP 分层：
- 应用层

  TCP/IP 协议族内预存了**各类通用的应用服务**。比如，**FTP（File
Transfer Protocol，文件传输协议）和 DNS（Domain Name System，域
名系统）服务就是其中两类。HTTP 协议也处于该层。**

- 传输层（包含TCP UDP）

负责数据的传输。在传输层有两个性质不同的协议：TCP（Transmission Control
Protocol，传输控制协议）和 UDP（User Data Protocol，用户数据报
协议）。
  
- 网络层
  
网络层用来处理在网络上流动的数据包。

  
- 数据链路层

  用来处理连接网络的硬件部分。包括控制操作系统、硬件的设备驱
动、NIC（Network Interface Card，网络适配器，即网卡），及光纤等
物理可见部分（还包括连接器等一切传输媒介）。**硬件上的范畴均在
链路层的作用范围之内。**

<img width="875" height="782" alt="image" src="https://github.com/user-attachments/assets/a76a1733-922c-46f4-96f2-c3ce0df6b60a" />


