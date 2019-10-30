# 包

标签（空格分隔）： 网络基础

---

网络传输的最小单位

## 结构

TCP/IP包结构

![包结构](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/package-structure.png)

* MAC头部：控制子网内的包传输
* IP头部：控制子网间的包传输
* TCP头部：控制套接字的连接，保证包无遗漏

## 拆分

数据超过包最大长度时需要拆分

![拆分](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/package-split.png)

## 传输

根据IP地址确定是否在同一子网内

* 在同一子网内，根据MAC地址通过集线器或交换机发送到目的设备
* 不在同一子网内，根据MAC地址发送到路由器，再由路由器转发

![TCP/IP网络](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/tcp-ip-internet.png)
