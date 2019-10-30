# 互联网协议

标签（空格分隔）： 网络基础

---

网络每一层协议的总称，用于交互数据包

![五层模型](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/internet-model.png)

## 实体层

把电脑连接起来的物理手段，负责传送0和1的电信号

## 链接层

确定了0和1的分组方式

### 以太网协议

* 规定了电子信号如何组成数据包
* 解决了子网内部的点对点通信

![以太网数据包](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/ethernet-package.png)

## 网络层

引进一套新的地址，区分计算机是否属于同一子网，建立主机到主机的通信

* 网络地址属于同一子网，采用广播的方式发送
* 网络地址不属于同一子网，采用路由的方式发送

![网络层](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/internet-level.jpg)

### IP协议

* 规定了IP地址
* 解决了子网间的点到点通信

### APR协议

在同一子网内通过IP地址得到MAC地址

## 传输层

建立端口到端口的通信，实现程序之间的交流

### 端口

每一个使用网卡的程序的编号

* 0到65535之间的一个整数
* 0到1023的端口被系统占用，用户只能选用大于1023的端口

### UDP协议

用户数据报协议，不保证数据的完整性

### TCP协议

有确认机制的UDP协议，保证数据通信的完整性和可靠性，防止丢包

## 应用层

规定应用程序的数据格式，对传输层的数据进行解读

### HTTP协议

规定了HTTP请求和响应的格式

### DNS协议

规定了DNS查询的格式

### DHCP协议

规定了如何分配动态IP
