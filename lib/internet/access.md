# 接入网

标签（空格分隔）： 网络基础

---

连接网络运营商的通信线路

## 结构

![互联网结构](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/access-net.png)

### 互联网接入路由器

接入入口，将包转发给运营商的BAS

### 接入方式

* ADSL接入网：通过电话线将包转发给BAS
* FTTH接入网：通过光纤将包转发给BAS

### BAS

Broadband Access Server，宽带接入服务器

* 进行用户认证和配置下发，给计算机分配公有地址
* 使用隧道方式将包转发给隧道专用路由器

### 隧道专用路由器

互联网的入口，接收BAS发送过来的包，将包转发到互联网内部

## 数据传输

### 连接

互联网接入路由器查询BAS的MAC地址

### 用户认证

* 互联网接入路由器将用户名和密码发送给BAS
* BAS通过RADIUS协议将密码发送给认证服务器进行认证

### 配置下发

认证无误后将IP地址、DNS服务器地址、默认网关地址等信息下发给互联网接入路由器

* BAS下发的TCP/IP参数会被配置到互联网接入路由器上
* 一对一连接时不下发默认网关的IP地址

### 包转发

一般采用PPPoE方式转发包

* 互联网接入路由器对包进行地址转换，并给包加上MAC头部、PPPoE头部、PPP头部，转发给BAS
* BAS丢弃包的MAC头部和PPPoE头部，通过隧道将包转发给隧道专用路由器
* 隧道专用路由器将包转发给互联网内部

![PPPoE包](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/PPPoE-package.png)
