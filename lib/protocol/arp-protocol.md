# ARP协议

标签（空格分隔）： 网络基础

---

Address Resolution Protocol，地址解析协议

* 介于链接层和网络层的协议，用于实现IP地址到MAC地址的转换

## ARP包

封装在以太网包中

* 硬件地址类型和长度，如以太网地址
* 协议地址类型和长度，如IP地址
* 操作类型，如ARP请求、ARP应答
* 数据：源MAC地址、目的MAC地址、源IP地址、目的IP地址

![ARP包](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/arp-package.png)

## 数据传输

* ARP请求：目的MAC地址填广播地址FF:FF:FF:FF:FF:FF，向子网内所有计算机广播，询问已知IP地址的MAC地址
* ARP应答：IP地址一致时，回复自己的MAC地址

![ARP广播](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/arp-broadcast.png)

### 缓存

ARP应答的结果会被缓存到ARP缓存表中

```bash
# 显示ARP缓存表xx
arp -a
```
