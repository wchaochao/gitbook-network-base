# IP协议

标签（空格分隔）： 网络基础

---

Internet Protocol, 网际协议

* 网络层协议，规定了IP地址，解决了子网间的点到点通信

## IP数据包

由头部和负载组成

* IP数据包放入链路层数据包负载中
* IP的负载存放传输层数据包，如TCP数据包、UDP数据包

![IP数据包](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/tcp-package.png)

### 头部

* IP版本和负载的协议类型，如IPv4、TCP协议、UDP协议
* 源IP地址和目的IP地址
* 分片ID和分片偏移量
* IP包存活时间
* 头部总长度和包总长度
* 校验码

## 数据包传输

根据路由表判断将数据包传给哪个机器

* 在同一子网内，直接传送给目的机器
* 不在同一子网内，传送给路由器，由路由器转发

![路由表](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/route-table.png)

### 路由器

一台配备有多个网卡的专用电脑，通过网卡接入到不同的网络中

### 丢弃

IP数据包传输是尽力式的，一旦发生异常情况，就会被轻易丢弃

* 网络繁忙
* 超过存活时间
* 数据包出错
* 路由表未及时更新，无法送达目的地

## 辅助协议

辅助IP地址传输的协议

### ARP协议

Address Resolution Protocol，地址解析协议，介于链接层和网络层的协议，用于实现IPv4地址到MAC地址的转换

* 数据包的MAC地址填广播地址FF:FF:FF:FF:FF:FF，向子网内所有计算机广播，询问已知IP地址的MAC地址
* 得到结果后将结果缓存到内存中的ARP缓存表

```bash
# 显示ARP缓存表xx
arp -a
```

![ARP广播](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/arp-broadcast.png)

### RIP协议

Routing Information Protocol, 用来动态生成路由表的协议

### ICMP协议

在IP协议发生错误时，发送ICMP消息告知发送方
