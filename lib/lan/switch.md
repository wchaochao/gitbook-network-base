# 交换机

标签（空格分隔）： 网络基础

---

根据MAC地址将包转发给目的地

## 结构

* 端口：执行包的收发操作，相当于一张网卡
* 交互电路：根据MAC地址表将包通过对应端口转发给目的MAC

![交换机](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/switch.png)

## MAC地址表

MAC地址和端口的对应表

### 匹配

* 有MAC地址表记录匹配时，通过对应的端口转发
* 没有MAC地址表记录匹配时，对其他端口广播

### 维护

* 接收到包时会将发送方的MAC地址及其端口写入MAC地址表中
* MAC地址表中的记录在一段时间不使用时自动删除

## 与集线器比较

* 支持使用全双工工作模式
* 可同时执行多个转发操作
