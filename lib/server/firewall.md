# 防火墙

标签（空格分隔）： 网络基础

---

对经过的包进行过滤，只允许发往指定服务器的指定应用程序的包通过

## 过滤

### 头部过滤

根据头部信息过滤包，主流防火墙方式

| 头部类型 | 判断条件 |
| --- | --- |
| MAC头部 | 发送方MAC地址 |
| IP头部 | 发送方IP地址 |
| IP头部 | 接收方IP地址 |
| IP头部 | 协议类型 |
| IP头部 | 分片 |
| ICMP头部 | ICMP类型 |
| TCP/UDP头部 | 发送方端口号 |
| TCP/UDP头部 | 接收方端口号 |
| TCP头部 | 控制标志 |

![头部过滤](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/firewall-filter.png)

### 内容过滤

通过代理的方式对包的内容进行过滤

## 路由

防火墙内置了路由功能，可以进行地址转换、包转发
