# 协议栈

标签（空格分隔）： 网络基础

---

## 内部结构

发送数据

* TCP模块：添加TCP头部
* UCP模块：添加UCP头部
* IP模块：添加IP头部和MAC头部
* 网卡：将数字信号转换为电信号或光信号，并通过网线或光纤发送出去

接收数据

* 网卡：通过网线或光纤接收电信号或光信号，转换为数字信号
* IP模块：解除IP头部和MAC头部

![内部结构](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/protocol-stack-structure.png)

## 收发操作

![收发操作](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/protocol-stack-action.png)

## 套接字

* 记录了用于控制通信操作的各种控制信息，如通信对象的IP地址、端口号、通信状态等
* 存放在协议栈的内存空间中，用于指示协议栈进行下一步行动

![套接字](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/netstat-socket.png)

## 创建套接字

在协议栈内存空间中创建套接字

* 协议栈分配用于存放套接字的内存空间
* 向套接字写入初始控制信息
* 返回标志套接字的描述符

## 连接套接字

通信双方交换控制信息，在套接字中记录这些必要信息并准备数据收发

* 客户端和服务器端交换控制信息，如IP地址、端口号等
* 在套接字中记录必要的控制信息
* 分配临时存放要收发数据的内存空间

### 控制信息

* 客户端和服务器相互联络时交换的控制信息，如TCP头部、IP头部、MAC头部
* 保存在套接字中用来控制协议栈操作的信息

## 发送数据

将发送的数据存放在发送缓冲区中，积累到一定量后发送出去

* 根据网络包的最大长度和时间判断何时发送
* 当数据太大时需要按照包拆分

### 包

![包结构](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/package-structure.png)

### 拆分

![拆分](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/package-split.png)

## 接收数据

* 将接收的数据存放在接收缓冲区中
* 从缓存区中取出数据传递给应用程序

## 断开连接

客户端或服务器端发起断开过程

## 删除套接字

通信结束后会等待一段时间再删除套接字，防止误操作
