# 负载均衡

标签（空格分隔）： 网络基础

---

* 使用多台服务器来分担负载
* 将客户端发送的请求分配到每台服务器上

## DNS轮询

通过多个IP地址的方式分配客户端请求

* 一个域名对应多个IP地址
* DNS查询时会按轮询的顺序返回DNS记录，客户端访问的IP地址将不同

![DNS轮询](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/dns-poll.png)

## 负载均衡器

通过代理的方式将请求转发给某台服务器

* 域名对应的IP地址设为负载均衡器的IP地址，客户端访问负载均衡器
* 负载均衡器根据服务器的负载情况判断请求转发给哪台Web服务器

![负载均衡器](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/load-balance.png)
