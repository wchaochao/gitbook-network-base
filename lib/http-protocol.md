# HTTP协议

标签（空格分隔）： 网络基础

---

Hyper Text Transfer Protocol，超文本传输协议

## 介绍

由请求和响应组成的传输层协议

![HTTP协议](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/http-protocol.png)

### 版本

* `HTTP0.9`: 只支持GET方法
* `HTTP1.0`: 支持GET、POST、HEAD方法，每次响应后关闭连接
* `HTTP1.1`: 新增PUT、DELETE、OPTIONS、TRACE、CONNECT方法，默认使用持久连接，主流版本
* `HTTP2`: 二进制数据流传输，支持多路复用

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
| HEAD | 获取响应头 |
| OPTIONS | 预检请求 |
| TRACE | 获取服务器收到的请求行和请求头，用于使用代理时查看请求信息 |
| CONNECT | 将连接改为管道方式的代理服务器，用于使用代理传输加密信息 |
| PATCH | 部分更新 |

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

| 状态码 | 类别 | 描述 |
| --- | --- | --- |
| 1xx | Informational | 告知请求的进度和情况 |
| 2xx | Success | 请求成功 |
| 3xx | Redirection | 需要进一步操作 |
| 4xx | Client Error | 客户端错误 |
| 5xx | Server Error | 服务器错误 |

常见状态码

| 状态码 | 状态短语 | 描述 |
| --- | --- | --- |
| 200 | OK | 请求成功 |
| 204 | No Content | 无内容返回 |
| 206 | Partial Content | 部分内容返回 |
| 301 | Moved Permanently | 永久移动资源 |
| 302 | Found | 临时移动资源 |
| 303 | See Other | 资源在另一个地址，需要GET请求 |
| 304 | Not Modified | 资源未更新 |
| 307 | Temporary Redirect | 临时重定向 |
| 400 | Bad Request | 请求错误 |
| 401 | Unauthorized | 认证失败 |
| 403 | Forbidden | 禁止访问 |
| 404 | Not Found | 未找到资源 |
| 405 | Method Not Allowed | 方法不允许 |
| 407 | Proxy Authentication Required | 需要代理的认证信息 |
| 416 | Request Range Not Satisfiable | 范围请求不满足 |
| 500 | Internal Server Error | 服务器错误 |
| 502 | Bad Gatway | 网关错误 |
| 503 | Service Unavailable | 服务不可用 |

![状态码](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/http-status.png)

## 消息头

### 上下文

通用头

| 消息头 | 说明 | 示例 |
| --- | --- | --- |
| Date | 消息的时间 | Date: Dec, 26 Dec 2015 17:30:00 GMT |

请求头

| 消息头 | 说明 | 示例 |
| --- | --- | --- |
| Host | 服务器主机名 | Host: developer.cdn.mozilla.net |
| User-Agent | 客户端信息 | User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/51.0.2704.103 Safari/537.36 |
| Referer | 引荐网页 | Referer: https://developer.mozilla.org/en-US/docs/Web/JavaScript |
| From | 请求人的邮件地址 | From: webmaster@example.org |

响应头

| 消息头 | 说明 | 示例 |
| --- | --- | --- |
| Server | 服务器信息 | Server: nginx/1.6.3 |

### 内容协商

通用头

| 消息头 | 说明 | 示例 |
| --- | --- | --- |
| Content-Type | 消息体的媒体类型 | Content-type: text/html; charset=utf-8 |
| Content-Length | 消息体的长度 | Content-Length: 348 |
| Content-Disposition | 数据描述 | Content-Disposition: attachment; filename="filename.jpg" |

请求头

| 消息头 | 说明 | 示例 |
| --- | --- | --- |
| Accept | 可接受的媒体类型 | Accept: text/plain |
| Accept-Charset | 可接受的编码方式 | Accept-Charset: utf-8 |
| Accept-Encoding | 可接受的压缩方式 | Accept-Encoding: gzip, deflate |
| Accept-Language | 可接受的语言列表 | Accept-Language: en-US |

响应头

| 消息头 | 说明 | 示例 |
| --- | --- | --- |
| Content-Encoding | 响应的压缩方式 | Content-Encoding: gzip |
| Content-Language | 响应的语言列表 | Content-Language: zh-cn |
| Content-Location | 响应的直接URL | Content-Location: /documents/foo.json |

### 传输编码

请求头

| 消息头 | 说明 | 示例 |
| --- | --- | --- |
| TE | 可接受的传输编码 | TE: trailers, deflate;q=0.5 |

响应头

| 消息头 | 说明 | 示例 |
| --- | --- | --- |
| Transfer-Encoding | 响应的传输编码 | Transfer-Encoding: chunked |
| Trailer | 分块传输的附加字段 | Trailer: Expires |

### 范围请求

请求头

| 消息头 | 说明 | 示例 |
| --- | --- | --- |
| Range | 请求范围 | Range: bytes=500-999 |
| If-Range | 资源未修改时获取部分内容 | If-Range: "9jd00cdj34pss9ejqiw39d82f20d0ikd" |

响应头

| 消息头 | 说明 | 示例 |
| --- | --- | --- |
| Accept-Ranges | 范围的单位 | Accept-Ranges: bytes |
| Content-Range | 响应的范围 | Content-Range: bytes 200-1000/67589 |

### 跨域请求

请求头

| 消息头 | 说明 | 示例 |
| --- | --- | --- |
| Origin | 跨域请求的源 | Origin: https://developer.mozilla.org |
| Access-Control-Request-Method | 跨域请求使用的方法 | Access-Control-Request-Method: GET |
| Access-Control-Request-Headers | 跨域请求要传递的头部 | Access-Control-Request-Headers: X-Custom-Header, Content-Type |

响应头

| 消息头 | 说明 | 示例 |
| --- | --- | --- |
| Access-Control-Allow-Origin | 跨域请求时允许的源 | Access-Control-Allow-Origin: https://developer.mozilla.org |
| Access-Control-Allow-Methods | 跨域请求时允许的方法 | Access-Control-Allow-Methods: GET, POST, OPTIONS |
| Access-Control-Allow-Headers | 跨域请求时允许传递的头部 | Access-Control-Allow-Headers: X-Custom-Header |
| Access-Control-Expose-Headers | 跨域请求时响应公开的头部 | Access-Control-Expose-Headers: Content-length |
| Access-Control-Allow-Credentials | 跨域请求时是否允许传递凭证 | Access-Control-Allow-Credential: true |
| Access-Control-Max-Age | 预检请求结果缓存的秒数 | Access-Control-Max-Age: 86400s |

### 缓存控制

通用头

| 消息头 | 说明 | 示例 |
| --- | --- | --- |
| Cache-Control | 缓存控制（HTTP1.1） | Cache-Control: private, max-age=600 |
| Pragma | 缓存设置（HTTP1.0） | Pragma: no-cache |

响应头

| 消息头 | 说明 | 示例 |
| --- | --- | --- |
| Expires | 缓存过期时间（HTTP1.0） | Expires: Wed, 21 Oct 2015 07:28:00 GMT |
| Age | 响应在代理中缓存的秒数 | Age: 12 |

### 资源校验

请求头

| 消息头 | 说明 | 示例 |
| --- | --- | --- |
| If-Match | 提供的ETag与资源匹配时进行相应的操作 | If-Match: "9jd00cdj34pss9ejqiw39d82f20d0ikd" |
| If-None-Match | 提供的ETag与资源不匹配时进行相应的操作 | If-None-Match: "9jd00cdj34pss9ejqiw39d82f20d0ikd" |
| If-Modified-Since | 资源在某个时间后修改了进行相应的操作 | If-Modified-Since: Dec, 26 Dec 2015 17:30:00 GMT |
| If-Unmodified-Since | 资源在某个时间后未修改进行相应的操作 | If-Unmodified-Since: Dec, 26 Dec 2015 17:30:00 GMT |

响应头

| 消息头 | 说明 | 示例 |
| --- | --- | --- |
| ETag | 资源的标识符，用于确定资源是否修改（HTTP1.1） | ETag: "33a64df551425fcc55e4d42a148795d9f25f89d4" |
| Last-Modified | 资源的最后修改时间，用于确定资源是否修改（HTTP1.0） | Last-Modified: Dec, 26 Dec 2015 17:30:00 GMT |

### 连接管理

通用头

| 消息头 | 说明 | 示例 |
| --- | --- | --- |
| Connection | 连接类型 | Connection: keep-alive |

### Cookie

请求头

| 消息头 | 说明 | 示例 |
| --- | --- | --- |
| Cookie | 服务器域名下的Cookie信息 | Cookie: PHPSESSID=298zf09hf012fh2; csrftoken=u32t4o3tb3gg43; |

响应头

| 消息头 | 说明 | 示例 |
| --- | --- | --- |
| Set-Cookie | 服务器设置Cookie | Set-Cookie: __Host-id=1; Secure; Path=/; domain=example.com |



### 认证

请求头

| 消息头 | 说明 | 示例 |
| --- | --- | --- |
| Authorization | 认证信息 | Authorization: Basic OSdjJGRpbjpvcGVuIANlc2SdDE== |
| Proxy-Authorization | 代理的认证信息 | Proxy-Authorization: Basic IOoDZRgDOi0vcGVuIHNlNidJi2== |

响应头

| 消息头 | 说明 | 示例 |
| --- | --- | --- |
| WWW-Authenticate | 认证方法 | WWW-Authenticate: Basic |
| Proxy-Authenticate | 代理服务器的认证方法 | Proxy-Authenticate: Basic |

### 重定向

响应头

| 消息头 | 说明 | 示例 |
| --- | --- | --- |
| Location | 重定向的地址 | Location: /index.html |
| Retry-After | 稍后重试 | Retry-After: 120 |

### 代理

通用头

| 消息头 | 说明 | 示例 |
| --- | --- | --- |
| Via | 经过的代理 | Via: HTTP/1.1 GWA |

请求头

| 消息头 | 说明 | 示例 |
| --- | --- | --- |
| Forwareded | 客户端请求经过的代理信息 | Forwarded: for=192.0.2.60; proto=http; by=203.0.113.43 |
| X-Forwarded-For | 客户端IP及经过的代理IP | Forwarded: for=192.0.2.60; proto=http; by=203.0.113.43 |
| X-Forwarded-Host | 客户端原始请求的Host | X-Forwarded-Host: id42.example-cdn.com |
| X-Forwarded-Proto | 客户端和代理之间的协议 | X-Forwarded-Proto: https |

| 消息头 | 说明 | 示例 |
| --- | --- | --- |
| Vary | 以指定消息头筛选代理缓存版本 | Vary: Accept-Encoding |

### 安全

响应头

| 消息头 | 说明 | 示例 |
| --- | --- | --- |
| Referrer-Policy | Referer规则 | Referer-Policy: no-referrer-when-downgrade |
| X-Frame-Option | 嵌入规则 | X-Frame-Options: DENY |
| Public-Key-Pins | 公钥与服务器绑定 | Public-Key-Pins: pin-sha256="cUPcTAZWKaASuYWhhneDttWpY3oBAkE3h2+soZS7sWs="; max-age=5184000; |

### 控制

请求头

| 消息头 | 说明 | 示例 |
| --- | --- | --- |
| Expect | 期待的行为 | Expect: 100-continue |

响应头

| 消息头 | 说明 | 示例 |
| --- | --- | --- |
| Allow | 响应允许的请求方法 | Allow: GET, POST, HEAD |
