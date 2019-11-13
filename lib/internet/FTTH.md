# FTTH接入网

标签（空格分隔）： 网络基础

---

Fiber To The Home，光纤到户，基于光纤的接入网技术

## 光纤

由纤芯、包层、保护套组成

![光纤](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/fiber.png)

### 分类

* 单模光纤：可全反射传导一个角度的光，失真小，用于距离较远的建筑物之间的连接，如FTTH接入网
* 多模光纤：可全反射传导多个角度的光，要求低，失真大，主要用于一座建筑物里面的连接，如POP、NOC

![光纤分类](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/fiber-type.png)

### 波形失真

多模光纤中多条光线到达的时间不同，信号的宽度会被拉伸，造成失真

![波形失真](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/fiber-distort.png)

### 光纤通信

通过在纤芯中传导光信号来传输数字信号，亮表示1，暗表示0

* 数字信号转换为电信号：1用高电压表示，0 用低电压表示
* 电信号转换为关信号：高电压发光亮，低电压发光暗

![光纤通信](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/fiber-communication.png)

### 波分复用

在一条光纤中使用不同的波长传输多个光信号

## 光纤接入

### 直连

用一根光纤直接从用户端连接到最近的电话局

* 光纤收发器：将以太网的电信号转换成光信号
* 多路光纤收发器：将光信号转换为电信号

![光纤直连-1](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/fiber-direct.png)

![光纤直连-2](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/fiber-direct-2.png)

### 分路

通过分光器让光纤分路，同时连接过个用户

* `ONU`：Optical Network Unit，光网络单元，将以太网的电信号转换成光信号
* 分光器：将信号发送给OLT或接收信号给相应的ONU
* `OLT`：Optical Line Terminal，光线路终端，将光信号转换为电信号，向ONU发指令调整信号收发时机来避免碰撞

![光纤分路-1](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/fiber-split.png)

![光纤分路-2](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/fiber-split-2.png)
