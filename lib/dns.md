# DNS

标签（空格分隔）： 网络基础

---

Domain Name System，域名系统，用于关联域名和IP

## 域名

主机名.次级域名.顶级域名.根域名，由点号划分

* 根域名：所有域名的尾部都有的，省略
* 顶级域名：根域名的下一级域名，如`.com, .cn, .net`
* 次级域名：顶级域名的下一级域名，可供用户注册，如`.example`
* 主机名：最后一级域名，用户在自己的域内为服务器分配的名称

```
www.example.com
www.example.com.
www.lab.example.com
```

## 域名解析

通过DNS查询IP地址

![域名解析](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/domain-resolve.png)

## 域名解析器

执行域名解析的程序，包含在操作系统的Socket库中

* 向DNS服务器发送查询消息
* 接收DNS服务器返回的响应消息，取出IP地址

## 域名服务器

根据查询的域名和记录类型返回相关的记录

* 域名：服务器、邮件服务器的名称
* Class: 用来识别网络信息，永远是代表互联网的IN
* 记录类型：域名对应何种类型的记录
 * `A`: Address, 域名对应的IP地址
 * `NS`: Name Server, 域名对应的域名服务器
 * `MX`: Mail eXchange, 域名对应的邮件服务器
 * `CNAME`: Canonical Name, 域名的别名
 * `PTR`: Pointer Record, IP地址反查域名

![DNS服务器](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/dns-server.png)

## 分级查询

从根域名开始，依次查询每一级域名的NS记录，直到查到最终的IP地址

* 任意域名服务器：保存了根域名的NS记录和A记录
* 根域名服务器：保存了顶级域名的NS记录和A记录
* 顶级域名服务器：保存了次级域名的NS记录和A记录
* 次级域名服务器：保存了下一级域名的NS记录和A记录

![DNS服务器查询](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/dns-server-query.png)

## 缓存

* DNS查询后的记录会被缓存在DNS服务器中
* DNS记录在DNS服务器中有TTL(Time To Live)，过期后该记录会被删除
