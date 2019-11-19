# 代理

标签（空格分隔）： 网络基础

---

介于客户端和服务器之间，具有对服务器的访问进行转发的功能，用于实现防火墙、负载均衡、缓存服务器功能

* 将客户端的请求转发给服务器
* 将服务器的响应转发给客户端

## 正向代理

客户端侧的代理，接收客户端的请求转发到互联网中

![正向代理](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/forward-proxy.png)

### 转发消息

根据HTTP请求中完整的URI进行转发

![正向代理转发](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/forward-proxy-http.png)

## 反向代理

服务器侧的代理，接收客户端的请求转发给某个服务器

### 转发消息

根据HTTP请求中的URL路径进行转发

## 透明代理

对客户端的请求进行拦截，再转发给服务器
