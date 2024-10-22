# 路由器

标签（空格分隔）： 网络基础

---

根据IP地址将包转发给目的地

## 结构

* 端口模块：根据相应通信技术规范执行包的收发操作，有MAC地址和IP地址
* 转发模块：根据路由表执行包的转发操作

![路由器](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/router.png)

## 路由表

* 目标地址：匹配目的IP地址
* 子网掩码：匹配目的IP地址时需要比对的比特数量
* 网关：转发给哪个路由器，没有时直接转发给目的地
* 接口：从哪个端口转发
* 跃点数：距离目的IP地址的距离

![路由表](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/router-table.png)

### 匹配

* 多个路由表记录匹配时，选择匹配比特数多的和跃点数少的
* 没有路由表记录匹配时选择默认路由，即目标地址为0.0.0.0的记录
* 没有路由表记录匹配且没有默认路由时，丢弃这个包并发送ICMP消息告知发送方

### 维护

* 手动维护路由表记录
* 根据路由协议机制，通过路由器之间的信息交换由路由器自行维护路由表的记录

## 功能

### 转发

* 输入端口接收包，检查MAC地址，正确时将包传给转发模块
* 转发模块查找路由表，匹配时更新IP头部的TTL和MAC头部，交给相应的输出端口发送
* 输出端口发送的包长度超过输出端口能传输的最大长度时，使用IP协议的分片功能对包进行拆分
* 输出端口按照所使用的通信技术（以太网、无线局域网等）将包发送给下一个路由器或目的地

![包分片](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/ip-fragment.png)

### 地址转换

为缓解IP地址耗尽问题，将内网地址转换为公网地址

* 内网往外网发送：将内网IP和端口改写为公网IP和端口
* 外网往内网发送：根据NAT地址转换表将目的IP地址和端口改为相应的内网IP地址和端口

![地址转换](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/address-convert.png)

### 包过滤

根据事先设置好的规则，转发包或丢弃包
