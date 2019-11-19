# BAS

标签（空格分隔）： 网络基础

---

Broadband Access Server，宽带接入服务器

* 进行用户认证和配置下发，给计算机分配公有地址
* 使用隧道方式将包转发给隧道专用路由器

## PPP协议

Point-to-Point Protocol，点对点协议，拨号上网使用的协议

* `RAS`：Remote Access Server，远程访问服务器
* `RADIUS`：Remote Authentication Dial-in User Service，远程认证拨号用户服务，加密协议

![PPP协议](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/PPP-protocol.png)

### 连接

用户向运营商的接入点拨打电话进行连接

### 用户认证

* 用户输入用户名和密码，生成PPP消息，装入HDLC（High-level Data Link Control，高级数据联接控）包中，发送给RAS
* RAS通过RADIUS协议发送给认证服务器

![PPP认证](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/PPP-auth.png)

### 配置下发

* 认证服务器校验无误后返回IP地址等配置信息，并将这些信息下发给用户
* 用户的计算机根据这些信息配置IP地址等参数，收发TCP/IP网络包

## PPPoE协议

Point-to-Point Protocol over Ethernet，以太网的点对点协议

* 由PPP协议发展而来
* 将PPP消息装入以太网包中进行传输

### ADSL的PPP

![ADSL的PPP](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/ADSL-PPP.png)

### FTTH的PPP

![FTTH的PPP](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/FTTH-PPP.png)

## PPPoA协议

Point-to-Point Protocol over ATM，ATM的点对点协议，ADSL接入网可使用的方式

* 不添加MAC头部和PPPoE头部，直接将PPP消息装入信元

![PPPoA](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/PPPoA.png)

## DHCP协议

Dynamic Host Configuration Protocol，动态主机配置协议

* 不需用户认证，直接进行配置下发

![DHCP方式](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/DHCP-style.png)

## 隧道

从隧道一侧的出口放入数据，数据就会原封不动地从另一个出口出来

### TCP隧道

通过TCP连接建立隧道，隧道中传输网络包

![TCP隧道](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/TCP-tunnel.png)

### 封装隧道

将包装入另一个包中在隧道中传输

![封装隧道](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/package-tunnel.png)
