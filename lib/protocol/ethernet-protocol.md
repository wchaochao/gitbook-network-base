# 以太网协议

标签（空格分隔）： 网络基础

---

Ethernet，规定了电子信号如何组成数据包，解决了子网内部的点对点通信

## 以太网数据包

### 头部

* 发送者的MAC地址和接收者MAC地址

### MAC地址

Media Access Control，硬件地址，烧录在网卡中，由48位二进制数组成

* 前24位：组织唯一标志符，用于区分厂家
* 后24位：扩展标识符，用于区分同一厂家的网卡

![MAC地址](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-computer-base/mac-address.png)

## 广播

Career Sense Multiple Access with Collision Detection，带冲突检测的载波监听多路访问，以太网的广播机制

* 载波监听：监听（Sense）表示网络是否正在使用的电信号（Career）
* 多路复用：多个（Multiple）设备可以同时访问（Access）传输介质
* 带冲突检测：检测（Detection）因同一时刻的传输而导致的电信号冲突（Collision）

![CSMA机制](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-computer-base/ethernet-CSMA.png)

![CD机制](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-computer-base/ethernet-CD.png)
