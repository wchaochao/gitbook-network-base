# 以太网协议

标签（空格分隔）： 网络基础

---

Ethernet Protocol，以太网的传输协议

* 规定了以太网数据包的格式
* 解决了以太网内的点对点通信

## 以太网

一种为多台计算机能够彼此自由和廉价地相互通信而设计的通信技术

* 用发送方MAC地址识别发送方
* 用接收方MAC地址识别接收方
* 用以太类型识别包内容

![以太网](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/ethernet.png)

## 以太网数据包

负载用于存放更高层的协议

![以太网数据包](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/tcp-package.png)

### 头部

* 源MAC地址和目的MAC地址
* 网络层协议类型，如IP协议、ARP协议

## 以太网传输

以太网通过广播的方式在子网内收发数据

### CSMA/CD

Career Sense Multiple Access with Collision Detection，带冲突检测的载波监听多路访问，以太网的广播机制

* 载波监听：监听（Sense）表示网络是否正在使用的电信号（Career）
* 多路复用：多个（Multiple）设备可以同时访问（Access）传输介质
* 带冲突检测：检测（Detection）因同一时刻的传输而导致的电信号冲突（Collision）

![CSMA机制](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-computer-base/ethernet-CSMA.png)

![CD机制](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-computer-base/ethernet-CD.png)
