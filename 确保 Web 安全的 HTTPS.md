## 安全性

- TCP/IP 是可能被窃听的网络
- 加密处理防止被窃听

1. 通信加密 SSL TLS 

   通过和 SSL（Secure Socket Layer，安全套接层）或TLS（Transport Layer Security，安全层传输协议）的组合使用，加密 HTTP 的通信内容。

2. 内容加密

   传输的报文本身加密

   

**HTTP+** 加密 **+** 认证 **+** 完整性保护**=HTTPS**



HTTP下，原来的服务器是“来者不拒”的状态，不管是什么发起请求都会接受，在安全性上有漏洞。

HTTPS则是身披 **SSL** 外壳的 **HTTP**。HTTPS 并非是应用层的一种新协议。只是 HTTP 通信接口部分用SSL（Secure Socket Layer）和 TLS（Transport Layer Security）协议代替而已。HTTPS 更安全。



加密和解密都会用到密钥。没有密钥就无法对密码解密，反过来说，任何人只要持有密钥就能解密了。如果密钥被攻击者获得，那加密也就失去了意义。



公开密钥加密使用一对非对称的密钥。一把叫做私有密钥（private key），另一把叫做公开密钥（public key）。顾名思义，私有密钥不能让其他任何人知道，而公开密钥则可以随意发布，任何人都可以获得。

（算两层防护吧！！）



- HTTPS 采用共享密钥加密和公开密钥加密两者并用的混合加密机制。



#### 证明公开密钥正确性的证书

遗憾的是，公开密钥加密方式还是存在一些问题的。**那就是无法证明公开密钥本身就是货真价实的公开密钥。**

比如，正准备和某台服务器建立公开密钥加密方式下的通信时，如何证明收到的公开密钥就是原本预想的那台服务器发行的公开密钥。或许在公开密钥传输途中，真正的公开密钥已经被攻击者替换掉了。

为了解决上述问题，可以使用由数字证书认证机构（CA，Certificate Authority）和其相关机关颁发的公开密钥证书。


<img width="714" height="867" alt="image" src="https://github.com/user-attachments/assets/4de50317-4ca9-4c16-8c9c-cbddb138e30b" />


这个好像是三握四挥额。

## 过程

- 步骤 **1**： 客户端通过发送 Client Hello 报文开始 SSL通信。报文中包含客户端支持的 SSL的指定版本、加密组件（Cipher Suite）列表（所使用的加密算法及密钥长度等）。

- 步骤 **2**： 服务器可进行 SSL通信时，会以 Server Hello 报文作为应答。和客户端一样，在报文中包含 SSL版本以及加密组件。服务器的加密组件内容是从接收到的客户端加密组件内筛选出来的。

- 步骤 **3**： 之后服务器发送 Certificate 报文。报文中包含公开密钥证书。

- 步骤 **4**： 最后服务器发送 Server Hello Done 报文通知客户端，最初阶段的 SSL握手协商部分结束。

- 步骤 **5**： SSL第一次握手结束之后，客户端以 Client Key Exchange 报文作为回应。报文中包含通信加密中使用的一种被称为 Pre-mastersecret 的随机密码串。该报文已用步骤 3 中的公开密钥进行加密。

- 步骤 **6**： 接着客户端继续发送 Change Cipher Spec 报文。该报文会提示服务器，在此报文之后的通信会采用 Pre-master secret 密钥加密。

- 步骤 **7**： 客户端发送 Finished 报文。该报文包含连接至今全部报文的整体校验值。这次握手协商是否能够成功，要以服务器是否能够正确解密该报文作为判定标准。

- 步骤 **8**： 服务器同样发送 Change Cipher Spec 报文。

- 步骤 **9**： 服务器同样发送 Finished 报文。

- 步骤 **10**： 服务器和客户端的 Finished 报文交换完毕之后，SSL连接就算建立完成。当然，通信会受到 SSL的保护。从此处开始进行应用层协议的通信，即发送 HTTP 请求。

- 步骤 **11**： 应用层协议通信，即发送 HTTP 响应。

- 步骤 **12**： 最后由客户端断开连接。断开连接时，发送 close_notify 报文。上图做了一些省略，这步之后再发送 TCP FIN 报文来关闭与 TCP的通信。

在以上流程中，应用层发送数据时会附加一种叫做 MAC（Message Authentication Code）的报文摘要。MAC 能够查知报文是否遭到篡改，从而保护报文的完整性。

<img width="736" height="442" alt="image" src="https://github.com/user-attachments/assets/6da6bdad-56ff-4e7c-a2b0-eeffa8d605fc" />


<img width="669" height="294" alt="image" src="https://github.com/user-attachments/assets/74effe95-1335-45e0-921c-66609bd5d0d0" />

## 为什么不一直使用 **HTTPS**

既然 HTTPS 那么安全可靠，那为何所有的 Web 网站不一直使用HTTPS ？

其中一个原因是，因为与纯文本通信相比，加密通信会消耗更多的CPU 及内存资源。如果每次通信都加密，会消耗相当多的资源，平摊到一台计算机上时，能够处理的请求数量必定也会随之减少。而且购买认证证书也有开销，不敏感的信息就不用https了，不涉及敏感的信息还是用http比较多呢。

采用SSL会变慢，增加网络负载，还有加密解密会消耗CPU以及内存等资源，处理速度也会变慢。


mark一下读到158页

