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

### 广播

向其他设备广播信号

![CSMA机制](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-computer-base/ethernet-CSMA.png)

### 碰撞

同时发送信号时会发生碰撞

![CD机制](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-computer-base/ethernet-CD.png)

### 脉冲信号

以太网中没有数据传输时，会填充脉冲信号

* 告知自身状态
* 检测对方是否在正常工作

![脉冲信号](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/pulse.png)

### 工作模式

可以通过脉冲信号协商使用哪种模式

* 半双工模式：进行碰撞检测，发送和接收不能同时进行
* 全双工模式：不进行碰撞检测，发送和接收能同时进行

![工作模式](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/work-mode.png)
