# UDP协议

标签（空格分隔）： 网络基础

---

User Datagram Protocol, 用户数据报协议

* 传输层协议，简单，不保证数据的完整性和可靠性
* 用于传输数据很短的包，未收到响应时重发

## UDP数据包

由头部和负载组成

* UDP数据包放入IP数据包负载中
* UDP的负载存放传输层数据包，如DNS数据包

![IP数据包](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/tcp-package.png)

### 头部

8字节

* 源端口和目的端口
* 数据长度
* 校验码
