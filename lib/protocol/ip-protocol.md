# IP协议

标签（空格分隔）： 网络基础

---

Internet Protocol, 网络协议

* 网络层协议，规定了IP地址，解决了子网间的点到点通信

## IP数据包

由头部和负载组成

* IP数据包放入链路层数据包负载中
* IP的负载存放传输层数据包，如TCP数据包、UDP数据包

### 头部

## 数据包传输

## ARP协议

Address Resolution Protocol，地址解析协议，用于实现IP地址到MAC地址的转换

* 数据包的MAC地址填广播地址FF:FF:FF:FF:FF:FF，向子网内所有计算机广播，询问已知IP地址的MAC地址
* 得到结果后将结果缓存到内存中的ARP缓存表

```bash
# 显示ARP缓存表
arp -a
```
