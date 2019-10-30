# DHCP协议

标签（空格分隔）： 网络基础

---

建立在UDP协议之上的应用层协议，用于动态分配IP

## DHCP数据包

![DHCP数据包](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/dhcp-package.png)

## IP分配

* 每一个子网络中，有一台计算机负责管理本网络的所有IP地址，叫做DHCP服务器
* 新的计算机加入网络，必须向DHCP服务器发送一个DHCP请求数据包，申请IP地址和相关的网络参数

### 请求

* 以太网标头：设置发出方（本机）的MAC地址和接收方（DHCP服务器）的MAC地址（广播地址：FF-FF-FF-FF-FF-FF）
* IP标头：设置发出方的IP地址（0.0.0.0）和接收方的IP地址（255.255.255.255）
* UDP标头：设置发出方的端口（68）和接收方的端口（67）

### 响应

* 以太网标头：设置发出方（DHCP服务器）的MAC地址和接收方（待分配主机）的MAC地址
* IP标头：设置发出方的IP地址（DHCP服务器地址）和接收方的IP地址（255.255.255.255）
* UDP标头：设置发出方的端口（67）和接收方的端口（68）
* 响应内容：待分配主机的IP地址、子网掩码、网关地址、DNS服务器等参数
