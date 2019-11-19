# ICMP协议

标签（空格分隔）： 网络基础

---

Internet Control Message Protocol，网络控制信息协议

* 介于网络层和传输层的协议，用于告知数据包传输过程中产生的错误以及各种控制信息
* 经常被黑客借用进行网络攻击

## ICMP数据包

封装在IP数据包中

* `Type`: ICMP消息的类型
* `Code`: Type下的小类型
* 检验和

![ICMP头部](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/icmp-header.png)

## ICMP消息

| 消息 | 说明 |
| --- | --- |
| Echo | ping命令发送的消息，用于确认接收端是否存在 |
| Echo reply | Echo的响应消息 |
| Source Quench | 源头冷却，提醒发出端放慢发送速度 |
| Destination Unreachable | 目的地无法到达 |
| Time Exceeded | traceroute命令发送的消息，超过存活时间 |
| Redirect | 重定向，直接发送不需路由器转发 |
| Parameter problem | IP头部字段存在错误 |
