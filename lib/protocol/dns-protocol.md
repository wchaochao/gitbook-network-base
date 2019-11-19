# DNS协议

标签（空格分隔）： 网络基础

---

建立在UDP协议之上的应用层协议，用于域名解析

## DNS包

![DNS包](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/dns-package.png)

### 头部

* 标识：查询/应答的ID
* 标志：查询、应答种类
* 问题数：查询的记录数
* 资源记录数：应答的记录数
* 授权资源记录数：授权应答的记录数
* 额外资源记录数：额外应答的记录数

## DNS查询

查询域名、Class、记录类型

![DNS查询](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/dns-inquire.png)

## DNS应答

返回资源记录

![DNS应答](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/dns-answer.png)

### 域名解析

* 一个域名只有一个IP时，返回该记录
* 一个域名有多个IP时，按照轮询的方式返回所有的IP记录，如先返回1、2、3，再返回2、3、1，在3、1、2，之后再循环
