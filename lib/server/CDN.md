# 内容分发服务

标签（空格分隔）： 网络基础

---

Content Distribution Network，由内容分发服务运营商在全球部署缓存服务器，租借给Web服务器运营者

* Web服务器可以推送最新的数据给缓存服务器

## 分配访问

客户端访问距离最近的缓存服务器

### DNS分配

* 客户端发送域名解析给DNS服务器
* DNS服务器事先从缓存服务器部署地点的路由器中收集路由信息，根据这些路由信息估算到客户端DNS服务器的距离
* 返回距离最近的缓存服务器记录

![DNS分配-1](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/dns-distribution-1.png)

![DNS分配-2](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/dns-distribution-2.png)

### 重定向分配

增加了HTTP消息的交互次数，精度较高

* 客户端发送请求给重定向服务器
* 重定向服务器事先从缓存服务器部署地点的路由器收集路由信息，根据这些路由信息估算到客户端的距离
* 将距离最近的缓存服务器的资源地址放到Location字段中返回

![重定向分配-1](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/redirect-distribution-1.png)

![重定向分配-2](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/redirect-distribution-2.png)

![重定向分配-3](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/redirect-distribution-3.png)
