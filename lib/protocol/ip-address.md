# IP地址

标签（空格分隔）： 网络基础

---

Internet Protocol Address，网络协议地址

## 版本

* IPv4: 地址位数为32位，主流版本，以下都是IPv4的介绍
* IPv6: 地址位数为128位，下一代IP地址

## 表示

![IP地址表示](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/ip-address.png)

### 格式

由32位二进制数组成，每8位一组，用十进制表示并用圆点分隔

```
210.21.196.6
```

### 组成

由网络地址和主机地址组成

* 网络地址：设备所在的子网地址
* 主机地址：设备在子网中的地址
 * 全为0：表示整个子网
 * 全为1：表示广播地址

### 子网掩码

由32位二进制数组成，左边为1，右边为0，用于区分网络地址和主机地址

* 1对应网络号
* 0对应主机号

![子网掩码](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/subnet-mask.png)

## 分类

| 网络类别 | IP地址范围 | 子网掩码 | 最大网络数 | 最大主机数 |
| --- | --- | --- | --- | --- | --- |
| A类 | 1.0.0.0 - 126.255.255.255 | 255.0.0.0 | 126 | 166777214 |
| B类 | 128.0.0.0 - 191.255.255.255 | 255.255.0.0 | 16384 | 65534 |
| C类 | 192.0.0.0 - 223.255.255.255 | 255.255.255.0 | 2097152 | 254 |
| D类 | 224.0.0.0 - 239.255.255.255 | 无 | 无 | 无 |
| E类 | 240.0.0.0 - 255.255.255.255 | 无 | 无 | 无 |

![IP地址分类](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/ip-address-category.png)

### 特殊IP

* `0.0.0.0`: 所有不清楚的主机和目的网络的集合
* `255.255.255.255`: 受限广播地址，只能在子网内广播
* `127.0.0.1`: 本机地址，用于本机测试

### 私网地址

访问互联网时需要做NAT或PAT网络地址转换

* A类：10.0.0.0 - 10.255.255.255
* B类：172.16.0.0 - 172.31.255.255
* C类：192.168.0.0 - 192.168.255.255

![私网访问](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/subnet-access.png)

## 子网划分

对主机号进行再划分，将一部分划入网络号

![子网划分](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/subnet-divide.png)

## 超网合并

将多个网段合并成一个大网络
