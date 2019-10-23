# Socket库

标签（空格分隔）： 网络基础

---

依次调用Socket库的程序组件，向操作系统的协议栈发出委托，进行数据收发

## 收发过程

* 创建套接字
* 将管道连接服务器端的套接字上
* 收发数据
* 断开管道并删除套接字

![收发数据](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/socket-data.png)

## Socket调用

![Socket调用](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/socket-api.png)

### 创建套接字

调用Socket库的socket程序组件

* 返回套接字描述符，应用程序用来识别套接字的机制

### 连接套接字

调用Socket库的connect程序组件

* 指定套接字描述符、服务器IP地址和端口号
* 连接成功后将IP地址和端口号保存在套接字中
* IP地址和端口号：客户端和服务器之间用来识别对方套接字的机制

### 发送数据

调用Socket库的write程序组件

* 指定套接字描述符和发送的数据

### 接收数据

调用Socket库的read程序组件

* 指定存放响应的内存地址

### 断开连接

调用Socket库的close程序组件

* 客户端和服务器都可先执行close
