# 互联网

标签（空格分隔）： 网络基础

---

## 结构

由多个运营商网络相互连接组成

* 接入网通过POP接入运营商
* 运营商之间通过NOC直连或IX连接
* POP、NOC、IX之间通过光纤连接

![互联网结构](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/internet-construct.png)

### POP

Point of Presense，互联网接入点

* 专线接入：不需用户认证和配置下发，最古老的上网方式
* 拨号接入：拨号上网，传输HDLC包
* PPPoE接入：传输PPPoE包
* PPPoA接入：传输PPPoA包

![POP](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/POP.png)

### NOC

Network Operation Center，网络运行中心

* 运营商的核心设备，规模扩大后的POP
* 从POP传来的网络包都会集中到这里，并从这里被转发到离目的地更近的POP，或者是转发到其他的运营商

### IX

Internet eXchange，互联网交换中心，用于多个运营商之间的连接

* 核心是具有大量高速以太网端口的二层交换机

![IX](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/IX.png)

## 数据传输

按照路由表不断转发，直到接收端所在的POP，再由POP转发给接收端

* 同一运营商的路由器会平等地交换路由信息
* 不同运营商的路由器根据协商情况交换路由信息

### RIP

Routing Information Protocol，路由信息协议，局域网、运营商之内交换路由信息

* 向邻居发送整个路由表信息
* 从一个接口上学习到的路由信息，不再从这个接口发送出去
* 使用跳数来衡量到达目标地址的路由距离，最大跳数为15跳

### BGP

Border Gateway Protocol，边界网关协议，运营商之间交换路由信息

* 转接：告知所有路由
* 非转接：告知相连的路由

![BGP](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/BGP.png)
