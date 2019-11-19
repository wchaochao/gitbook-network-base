# 缓存服务器

标签（空格分隔）： 网络基础

---

通过代理方式的对响应进行缓存

## 机制

* 没有缓存时将请求转发给服务器并将服务器响应缓存起来转发给客户端
* 命中缓存且数据未更新时将缓存返回给客户端

![缓存服务器](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/cache-server.png)

### 无缓存

* 客户端将请求发送给缓存服务器
* 缓存服务器通过URL判断中转目标，将请求发送给Web服务器
* Web服务器将响应返回给缓存服务器，缓存服务器将数据缓存下来
* 缓存服务器将响应返回给客户端

![无缓存-1](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/cache-server-miss-1.png)

![无缓存-2](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/cache-server-miss-2.png)

### 命中缓存

* 客户端将请求发送给缓存服务器
* 缓存服务器命中缓存，向Web服务器询问数据是否更新
 * 未更新，缓存服务器将缓存返回给客户端
 * 已更新，Web服务器将新数据发送给缓存服务器，缓存服务器更新缓存并返回新数据

![命中缓存](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/cache-server-hit.png)

## 部署

### 部署在客户端

可以减少网络流量，无法控制缓存服务器

![客户端缓存](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/client-cache.png)

### 部署在服务器端

可以降低服务器负载，无法减少网络流量

![服务器端缓存](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/server-cache.png)

### 部署在互联网边缘

可以减少网络流量，也可以控制缓存服务器

![互联网边缘缓存](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/access-cache.png)
