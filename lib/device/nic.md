# 网卡

标签（空格分隔）： 网络基础

---

Network Interface Card，发送和接收包的计算机硬件

* 一台计算机可以有多个网卡，如以太网卡，WiFi网卡

## 结构

![网卡](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/nic.png)

### 初始化

* 开机时操作系统通过网卡驱动对网卡进行初始化
* 读取网卡ROM中的MAC地址分配给MAC模块

### 发送数据

* 缓冲区：接收IP模块拼装好的包
* MAC模块：将包从缓冲区中取出，开头加上报头和起始帧分界符，末尾加上校验码，并转换为通用格式
* PHY模块：将通用格式信号转换为可在网线上传输的格式，并通过网线发送出去

![网卡包](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/nic-package.png)

### 接收数据

* PHY模块：通过网线接收信号，并转换为通用格式信号传给MAC模块
* MAC模块：将通用格式信号转换为数字信号，检查FCS和MAC，一致时将包放入缓冲区
* 缓冲区：通过中断机制通知计算机接收到了包

### 信号转换

* 数字信号转换为电信号：需要叠加时钟信号来区分比特之间的界限
* 电信号转换为数字信号：根据一段特定的序列测量出时钟信号，再分解出数字信号

![数电转换](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/digital-signal.png)

## MAC

Media Access Control，网卡编号，烧录在网卡的ROM中，由48位二进制数组成

* 前24位：组织唯一标志符，用于区分厂家
* 后24位：扩展标识符，用于区分同一厂家的网卡

![MAC地址](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/mac-address.png)
