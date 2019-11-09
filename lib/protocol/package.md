# 包

标签（空格分隔）： 网络基础

---

网络传输的最小单位

## 结构

分为头部、数据、尾部三部分

![包结构](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/package-structure.png)

### 头部

* `preamble`: 7字节的序言，每个字节都是0xAA，用于确定时钟信号
* `SFD`: Start Frame Delimiter, 1字节的起始信号, 为0xAB
* `DST`: Destination, 6字节的目的地址
* `SRC`: Source, 6字节的发出地址
* `Type`: 上层协议类型，如0×0800为IPv4，0×0806为ARP

### 数据

存放更高层协议的数据包，如IP数据包

### 尾部

校验序列，检验数据的传输是否发生错误

## 拆分

数据超过包最大长度时需要拆分，一般为1500字节

![拆分](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/package-split.png)

## 传输

根据IP地址确定是否在同一子网内

* 在同一子网内，根据MAC地址通过集线器或交换机发送到目的设备
* 不在同一子网内，根据MAC地址发送到路由器，再由路由器根据IP地址转发

![TCP/IP网络](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/tcp-ip-internet.png)
