# 网卡

标签（空格分隔）： 网络基础

---

Network Interface Card，发送和接收包的计算机硬件

* 一台计算机可以有多个网卡，如以太网卡，WiFi网卡

## 结构

![网卡](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/nic.png)

### MAC

Media Access Control，网卡编号，烧录在网卡的ROM中，由48位二进制数组成

* 前24位：组织唯一标志符，用于区分厂家
* 后24位：扩展标识符，用于区分同一厂家的网卡

![MAC地址](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/mac-address.png)

### RJ-45接口

网卡接口

* `MDI`：RJ-45与PHY直连接线
* `MDI-X`：RJ-45与PHY交叉接线

![RJ-45连线](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/rj-45.png)

## 数据传输

### 网络包

![网卡包](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/nic-package.png)

### 初始化

* 开机时操作系统通过网卡驱动对网卡进行初始化
* 读取ROM中的MAC地址分配给MAC模块

### 发送数据

* 缓冲区：从协议栈中接收包
* MAC模块：将包从缓冲区中取出，开头加上报头和起始帧分界符，末尾加上校验码
* PHY模块：将数字信号转换为电信号
* RJ-45接口：通过网线发送信号

![网卡发送](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/nic-send.png)

### 接收数据

* RJ-45接口：通过网线接收信号
* PHY模块：将接收的信号转换为数字信号传给MAC模块
* MAC模块：检查FCS和MAC，一致时将包放入缓冲区，不一致时丢弃
* 缓冲区：将包传给对应的协议栈

### 信号传输

* 发送数字信号：需要叠加时钟信号来区分比特之间的界限
* 读取数字信号：根据一段特定的序列测量出时钟信号，再分解出数字信号

![信号传输](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/digital-signal.png)

![还原数字信号](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/digital-signal-reduction.png)
