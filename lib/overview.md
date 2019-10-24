# 概述

标签（空格分隔）： 网络基础

---

从浏览器中输入网址开始探究网络的整个过程

![网络图](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/network-procedure.png)

## 浏览器

* 解析URL
* 生成HTTP请求
* 调用Socket库进行域名解析
* 调用Socket库发送HTTP请求

## Socket库

* 委托协议栈发送请求

## 协议栈

* 客户端、服务器端建立套接字连接
* 以包的形式收发数据
