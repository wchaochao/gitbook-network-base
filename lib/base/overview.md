# 概述

标签（空格分隔）： 网络基础

---

从浏览器输入网址开始探究网络的整个过程

![网络图](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/network-procedure.png)

## 浏览器

发出请求

* 解析URL
* 生成HTTP请求
* 调用Socket库进行域名解析
* 调用Socket库发送HTTP请求

## Socket库

网络请求调用层

* 提供网络请求的API
* 委托协议栈发送请求、接收响应

## 协议栈

操作套接字

* 创建套接字
* 连接套接字
* 收发数据
* 断开连接

## 局域网

传输包

* 网卡：发送/接收信号
* 网线：传输信号
* 集线器：子网内广播信号
* 交换机：子网内转发信号
* 路由器：子网间转发信号

## 接入网

将局域网接入网络运营商

* 互联网接入路由器：接入网入口
* ADSL接入网：通过电话线接入
* FTTH接入网：通过光纤接入
* 宽度接入服务器：进行登录认证、配置下发、包转发

## 互联网

包在网络运营商之内、之间转发

* POP：互联网接入点
* NIX：网络运行中心
* IX：运营商之间的大型交换机

## 服务器

返回响应

* 服务器：作出响应
* 防火墙：过滤包
* 负载均衡：均衡负载
* 缓存服务器：提供缓存

## 包传输过程

![包传输过程-1](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/package-transport-1.png)

![包传输过程-2](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/package-transport-2.png)
