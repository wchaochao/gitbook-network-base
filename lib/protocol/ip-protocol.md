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

不算可选字段20字节

* 源IP地址和目的IP地址
* 分片ID和分片偏移量
* 包的生存时间，每经过一个路由器转发就减1
* IP版本和协议类型，如ICMP、TCP、UDP
* 头部长度和总长度，最大65535字节，受以太网包限制
* 首部检验和

![IP头部](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/ip-header.png)

## 数据包传输

根据路由表判断将数据包传给哪个机器

* 在同一子网内，直接传送给目的机器
* 不在同一子网内，传送给路由器，由路由器转发

![路由表](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/route-table.png)

### 丢弃

IP数据包传输是尽力式的，一旦发生异常情况，就会被轻易丢弃

* 网络繁忙
* 超过存活时间
* 数据包出错
* 路由表未及时更新，无法送达目的地
