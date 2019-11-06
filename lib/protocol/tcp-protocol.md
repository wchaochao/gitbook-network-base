# TCP协议

标签（空格分隔）： 网络基础

---

Transmission Control Protocol, 传输控制协议

* 传输层协议，保证数据通信的完整性和可靠性，防止丢包

## TCP数据包

由头部和负载组成

* TCP数据包放入IP数据包负载中
* TCP的负载存放应用层数据包，如HTTP数据包

![TCP数据包](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/tcp-package.png)

### 头部

* 源端口号和目的端口号
* 发送的数据包编号
* 接收的数据包ACK确认号和滑动窗口大小
* 控制标志位
* 校验码

### 标志位

* URG：紧急标志，为1时紧急指针有效
* ACK：确认标志，为1时ACK确认号有效
* PSH：push标志，为1时尽快将该报文交给应用层
* RST：复位标志，为1时重建连接
* SYN：同步标志，为1时建立连接，同步初始编号和滑动窗口大小
* FIN：关闭连接标志，为1时关闭连接

## 数据包传输

有序、可靠

### 编号

对每个包进行编号，以便接收的一方按照顺序还原

* 第一个包编号为随机数
* 下一个包编号 = 上一个包编号 + 上一个包的负载长度

### 组装

收到数据包后，由操作系统完成组装，转交给应用程序

* 操作系统：持续地接收 TCP 数据包，按照顺序组装好
* 应用程序：根据套接字转交给相应的应用程序，并依照应用层协议正确的读出一段段数据，如HTTP协议按照Content-Length读取

### ACK确认

包确认机制，用于在丢包时重发

* 接收端在接收到数据包后，发送要收到的下一个数据包的编号
* 如果连续收到三个重复的ACK或ACK超时（超时时间根据ACK返回时间动态调整），则确认丢包，重新发送这个包

![ACK确认](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/ack-retry.png)

### 数据缓冲区

通过数据缓冲区发送、接收数据

![缓冲区](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/socket-buffer.png)

发送端

* `LastByteWritten`: 应用程序写入数据的位置
* `LastByteSent`: 已发送数据的位置
* `LastByteAcked`: 已确认成功接收的数据位置

接收端

* `LastByteRcvd`: 收到的包的位置
* `NextByteExpected`: 收到的连续包的位置
* `LastByteRead`: 已被应用程序接收的位置

## 数据包控制

### 时延应答

延迟发送ACK，减少接收端的发包数

* 接收端在收到数据后并不立即发送一个应答数据包，而是等待一段时间
* 如果有新的数据被接受就更新应答号，如果有其他数据要发送就坐上该数据包的顺风车

![时延应答](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/ack-delay.jpg)

### Nagle算法

TCP连接上只允许一个未被确认的小分组（数据包小于最大报文段长度），减少发送端的发包数

* 发送端欲多次发送多个小数据包，先将第一个小包发送出去，而将后面到达的少量字符数据都缓存起来而不立即发送
* 当收到第一个数据包的ACK确认，或当前字符属于紧急数据，或者积攒到了一定数量的数据等多种情况才将其组成一个较大的数据包发送出去

![Nagle算法](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/nagle-algorithm.jpg)

### 滑动窗口

接收端根据自己的状况通告窗口大小，进行流量控制

* 接收端在接收到数据包后，发送当前能接收的数据包总大小
* 发送端下一次发送数据包时，根据滑动窗口大小调整数据包发送

![滑动窗口](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/slide-window.jpg)

### 拥塞窗口

根据网络情况调整拥塞窗口大小，进行拥塞控制，实际窗口取滑动窗口和拥塞窗口的最小值

* 发送端一开始发送包时执行慢开始算法，拥塞窗口指数增长
* 到达慢启动阈值时执行拥塞避免算法，拥塞窗口线性增长
* 一旦发送丢包，慢启动阈值设为当前拥塞窗口的一半，拥塞窗口重新从1开始执行慢开始算法

![拥塞窗口](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/congestion-control.png)

## 传输过程

![TCP传输](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/tcp-transmission.jpg)

### 三次握手

同步初始序号

* 客户端发送SYN，开始连接，告知客户端数据包的初始序号
* 服务器端返回ACK，表示已接收，并给客户端发送SYN，告知服务器端数据包的初始序号
* 客户端发送ACK确认收到

![三次握手](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/tcp-connect.jpg)

### 四次挥手

客户端、服务器端关闭连接

* 主动关闭的一方发送FIN，表示单方面关闭数据传输，另一方发送ACK确认
* 另一方数据传输完毕后也发送FIN，表示关闭这个方向的数据传输，主动关闭的一方发送ACK确认
* 主动关闭的一方进入TIME_WAIT状态，防止发送的ACK丢失

![四次挥手](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/tcp-close.jpg)
