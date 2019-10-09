# HTTP协议

标签（空格分隔）： 网络基础

---

Hyper Text Transfer Protocol，超文本传输协议

## 介绍

* 基于 TCP/IP 协议的应用层协议
* 规定了客户端和服务器之间的通信格式，默认使用80端口
* 由请求和响应组成

![HTTP协议](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/http-protocol.png)

### 版本

* HTTP0.9: 只能返回文本
* HTTP1.0: 每次响应完后关闭连接
* HTTP1.1: 持久化连接，主流版本
* HTTP2: 二进制数据流传输

## 请求

* 请求行：请求的内容，由请求方法、URI、HTTP版本组成
* 请求头：请求的附加信息，每行一个头信息
* 请求体：向服务器发送的数据

![HTTP请求](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/http-request.png)

```
GET / HTTP/1.0
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_5)
Accept: */*
```

### 请求方法

| 方法 | 说明 |
| --- | --- |
| GET | 获取数据 |
| POST | 发送数据 |
| PUT | 更新数据 |
| DELETE | 删除数据 |
| HEAD | 获取响应头，用于获取文件最后更新时间等熟悉信息 |
| OPTIONS | 通知或查询通信选项，用于跨域的预检请求 |
| TRACE | 获取服务器收到的请求行和请求头，用于使用代理时查看请求信息 |
| CONNECT | 使用代理传输加密信息 |

## 响应

* 状态行：响应状态，由HTTP版本、状态码、状态短语组成
* 响应头：响应的附加信息
* 响应体：返回的数据

![HTTP响应](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/http-response.png)

```
HTTP/1.0 200 OK
Content-Type: text/plain
Content-Length: 137582
Expires: Thu, 05 Dec 1997 16:00:00 GMT
Last-Modified: Wed, 5 August 1996 15:55:28 GMT
Server: Apache 0.84

<html>
  <body>Hello World</body>
</html>
```

### 状态码

* 1xx：指示信息 – 表示请求已接收，继续处理
* 2xx：成功 – 表示请求已被成功接收、理解、接受
* 3xx：重定向 – 要完成请求必须进行更进一步的操作
* 4xx：客户端错误 – 请求有语法错误或请求无法实现
* 5xx：服务器端错误 – 服务器未能实现合法的请求

![状态码](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/http-status.png)

## 消息头

附加信息

### 通用头

适用于请求和响应的消息头

| 头字段 | 说明 |
| --- | --- |
| Date | 请求/响应的时间 |
| Cache-Control | 缓存控制 |
| Connection | 持久连接 |
| Transfer-Encoding | 编码形式 |
| Via | 记录途中经过的代理和网关 |

### 请求头

请求的消息头

| 头字段 | 说明 |
| --- | --- |
| User-Agent | 客户端名称版本信息 |
| Host | 服务器主机 |
| Referer | 上一个页面的URI |
| Accept | 客户端可支持的数据类型（Content-Type）， 以 MIME 类型来表示 |
| Accept-Charset | 客户端可支持的字符集 |
| Accept-Encoding | 客户端可支持的编码格式（Content-Encoding），一般来说表示数据的压缩格式 |
| Accept-Language | 客户端可支持的语言 |
| If-Modified-Since | 缓存的更新日期 |
| If-None-Match | 缓存的ETag |
| Authorization | 身份认证 |
| Range | 获取部分数据的范围 |

### 响应头

响应的消息头

| 头字段 | 说明 |
| --- | --- |
| Server | 服务器名称版本信息 |
| Accept-Ranges | 是否支持部分数据获取 |

### 实体头

消息体的附加信息

| 头字段 | 说明 |
| --- | --- |
| Content-Type | 消息体的数据类型，用MIME类型表示 |
| Content-Encoding | 消息体的编码形式 |
| Content-Language | 消息体的语言 |
| Content-Length | 消息体长度 |
| Content-Range | 消息体的数据范围 |
| Expires | 消息体的有效期 |
| Last-Modified | 数据的最后更新日期 |
| Etag | 数据体的Etag |
