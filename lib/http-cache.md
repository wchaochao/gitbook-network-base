# HTTP缓存

标签（空格分隔）： 网络基础

---

* 保存资源副本并在下次请求时直接使用该副本的技术
* 一般只有GET请求才会被缓存

## 分类

* 私有缓存：如浏览器缓存
* 共享缓存：如代理缓存、CDN、负载均衡器

![缓存分类](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/http-cache-type.png)

## 设置

**HTTP1.1**

### Cache-control

默认为private

* `no-store`: 不缓存
* `no-cache`: 使用缓存前校验缓存
* `private`: 客户端可以缓存
* `public`: 客户端和代理服务器都能缓存
* `max-age=<secodes>`: 缓存将在多少秒后过期
* `must-revalidate`: 缓存过期后进行校验

```
Cache-control: private, max-age=2592000
```

### Vary

代理缓存以指定消息头区分缓存

```
Vary: User-Agent
```

**HTTP1.0**

### Pragma

* `no-cache`: 使用缓存前校验缓存

```
Pragma: no-cache
```

### Expires

缓存的过期时间

```
Expires: Fri, 04 Jan 2019 12:00:00 GMT
```

## 过期

缓存有过期时间，过期后缓存由fresh状态变为stale状态

* max-age设置：缓存经过多少秒后过期
* Expires设置：缓存到某个时间后过期
* 未设置：缓存时间为(Date - LastModified) / 10

## 标志

**HTTP1.1**

### ETag

资源的唯一标志，默认采用`SHA256`算法生成

```
Etag: W/"e563df87b65299122770e0a84ada084f"
```

**HTTP1.0**

### Last-Modified

资源的最后修改时间

```
Last-Modified: Wed, 02 Jan 2019 03:06:03 GMT
```

## 校验

**HTTP1.1**

### If-None-Match

* ETag不匹配时，资源已修改，返回最新数据
* ETag匹配时，资源未修改，返回304

```
If-None-Match: W/"e563df87b65299122770e0a84ada084f"
```

**HTTP1.0**

### If-Modified-Since

* Last-Modified不匹配时，资源已修改，返回最新数据
* Last-Modified匹配时，资源未修改，返回304

```
If-Modified-Since: Wed, 02 Jan 2019 03:06:03 GMT
```

## 存储

* `disk cache`: 硬盘缓存，可长久使用
* `memory cache`: 内存缓存，快速读取

## 读取

三级缓存原理

* 先从内存中读取
* 内存中没有，再从硬盘中读取，读取到的资源缓存到内存中
* 硬盘中没有，发送HTTP请求，资源缓存到硬盘和内存中，方便下次快速读取

### 缓存不存在

* 发送HTTP请求获取最新资源
* 按照指定的缓存规则对资源进行缓存

### 缓存存在

缓存未过期，根据缓存规则确定是否需要校验

* 不需校验，从缓存中读取资源
* 需校验，将校验信息发送给服务器
 * 资源未修改，返回304，更新缓存规则，从缓存中读取资源
 * 资源已修改，返回最新的资源，按照指定的缓存规则对最新资源进行缓存

缓存已过期，对资源进行校验

* 资源未修改，返回304，更新缓存规则，从缓存中读取资源
* 资源已修改，返回最新的资源，按照指定的缓存规则对最新资源进行缓存

## 策略

![缓存策略](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/http-cache-decision-tree.png)
