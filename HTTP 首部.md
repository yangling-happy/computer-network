<img width="660" height="418" alt="image" src="https://github.com/user-attachments/assets/9235c4eb-9a06-4a76-b031-d1d62051506f" />


请求首部字段：

<img width="666" height="719" alt="image" src="https://github.com/user-attachments/assets/7b9ca879-e52f-49b2-a0de-3d36a4f0261e" />



<img width="704" height="418" alt="image" src="https://github.com/user-attachments/assets/9d49b3f4-8806-4fd3-9f77-fabf8be5f990" />


<img width="700" height="456" alt="image" src="https://github.com/user-attachments/assets/dbfbf9c8-1189-4eff-be7d-745ab0274b2f" />


首部字段内容太多了，记一下基础的，别的细节要看的时候再来查表：

HTTP 首部字段根据实际用途被分为以下 4 种类型。

- 通用首部字段（**General Header Fields**）

请求报文和响应报文两方都会使用的首部。

- 请求首部字段（**Request Header Fields**）

从客户端向服务器端发送请求报文时使用的首部。补充了请求的附加内容、客户端信息、响应内容相关优先级等信息。

- 响应首部字段（**Response Header Fields**）

从服务器端向客户端返回响应报文时使用的首部。补充了响应的附加内容，也会要求客户端附加额外的内容信息。

- 实体首部字段（**Entity Header Fields**）

针对请求报文和响应报文的实体部分使用的首部。补充了资源内容更新时间等与实体有关的信息。

#### 通用首部

- **Cache-Control**：控制缓存行为（如 `no-cache`、`max-age`）。
- **Connection**：管理连接（如 `keep-alive`）。
- **Date**：报文创建时间。

#### 请求首部

- **Host**：**必含字段**，指定服务器域名。
- **User-Agent**：标识客户端信息。
- **Accept** / **Accept-Encoding** / **Accept-Language**：告诉服务器自己能接受的内容类型、压缩方式和语言。
- **Cookie**：发送给服务器的Cookie信息。
- **Referer**：当前请求的来源页面地址。
- **Authorization**：身份认证凭证。

#### 响应首部

- **Set-Cookie**：服务器向客户端写入Cookie。
- **Content-Type**：响应内容的类型（如 `text/html`、`application/json`）。
- **Content-Length**：响应体的长度。
- **Location**：重定向的目标地址（配合3xx状态码使用）。
- **Server**：服务器软件信息。

#### 实体首部

- **Content-Encoding**：内容的编码方式（如gzip）。
- **Last-Modified**：资源的最后修改时间。
- **ETag**：资源的实体标识。
