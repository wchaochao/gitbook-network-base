# Socket库

标签（空格分隔）： 网络基础

---

提供网络相关的API，委托协议栈收发数据

## API调用

![Socket调用](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/socket-api.png)

## 域名操作

### getHostByName

域名解析

* 指定域名，生成DNS查询请求，委托协议栈发出请求
* 接收DNS响应，从响应中取出域名对应的IP传给应用程序

## 收发数据

通过对套接字的操作收发数据

* 创建套接字
* 连接套接字
* 收发数据
* 断开管道并删除套接字

![收发数据](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/socket-data.png)

### socket

创建套接字

* 指定套接字的相关信息，初始化套接字
* 返回套接字描述符，应用程序用来识别套接字的机制

### connect

连接套接字

* 指定套接字描述符、服务器IP地址和端口号，向服务器端发出连接请求
* 连接成功后将IP地址和端口号保存在套接字中
* IP地址和端口号：客户端和服务器之间用来识别对方套接字的机制

### write

发送数据

* 指定套接字描述符和发送的数据，通过套接字管道发送数据

### read

接收数据

* 指定存放接收数据的内存地址，通过套接字管道接收数据

### close

断开连接并删除套接字

* 客户端和服务器都可先执行close
