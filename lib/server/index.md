# 服务器

标签（空格分隔）： 网络基础

---

响应客户端请求

## 结构

* 等待连接模块：创建套接字，等待客户端连接，在连接时复制套接字与客户端连接并将新套接字移交给新启动的通信模块
* 通信模块：使用新套接字与客户端通信，与客户端一一对应

![服务器结构](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/server-construct.png)

## 收发操作

* 创建套接字：等待连接模块调用Socket模块创建套接字
* 等待连接：创建的套接字绑定端口，状态为listen
* 接受连接：复制套接字，客户端连接到新套接字上，并将新套接字移交给新启动的通信模块
* 收发数据：通信模块通过新套接字收发数据
* 断开连接
* 删除套接字

![收发操作](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/server-dispatch.png)

### 网卡接收信号

* 网卡接收电信号，还原为数字信号
* MAC模块检验FCS和MAC地址，正确时将包存入网卡缓冲区
* 网卡通过中断将网络包到达的事件通知给CPU
* CPU驱使网卡驱动从网卡缓冲区中取出包，根据MAC头部的以太类型转交给TCP/IP协议栈

### IP模块

* 检查IP地址
* 分片时需要等所有分片到达后组装还原成原始包
* 根据IP头部的协议号字段将包转交给TCP模块

### TCP模块

处理连接包

* 检查端口和SYN标志位
* 复制套接字，记录发送方IP地址和端口并分配数据缓冲区
* 回复初始包编号、ACK号、滑动窗口大小

处理数据包

* 根据发送方IP地址、接收方IP地址、发送方端口、接收方端口匹配套接字
* 将接收的数据存放到套接字对应的接收缓冲区，回复ACK号
* 服务器程序调用read模块读取接收缓冲区中的数据，组成应用层消息

处理断开包

* 客户端调用close模块发送FIN包，服务器回复ACK号
* 服务器调用close模块发送FIN包，客户端回复ACK号
* 断开连接一段时间后删除套接字

### 程序模块

* 将接收缓冲区中取出的数据组成请求
* 对请求消息进行处理，获取响应
* 调用write模块发送响应

![返回响应](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/server-response.png)

## 访问控制

设置规则对服务器的访问进行控制

* 客户端IP地址：从IP头部取出
* 客户端域名：通过客户端IP地址反查询其域名
* 用户名和密码：要求提供用户名、密码

![访问控制](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/server-auth.png)

## 部署

* 直接连接路由器：容易被攻击
* 通过防火墙隔离：只允许发往指定服务器的指定应用程序的网络包通过
* 部署在数据中心：由数据中心维护

![服务器部署](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/server-deploy.png)
