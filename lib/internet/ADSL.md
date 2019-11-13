# ADSL接入网

标签（空格分隔）： 网络基础

---

Asymmetric Digital Subscriber Line，不对称数字用户线

* 利用架设在电线杆上的金属电话线来进行高速通信的技术
* 上行方向（用户到互联网）和下行方向（互联网到用户）的通信速率是不对称的

## 结构

* 互联网接入路由器：接入入口，给包加上MAC头部、PPPoE头部、PPP头部
* ADSL Modem：将包拆分为信元，调制成模电信号
* 分离器：将ADSL信号和语音信号混合/分离
* 电话线：传输ADSL、语音混合信号
* 配线盘：连接室内电话线和室外电话线
* 电话电缆：架设在电线杆上，将信号传输到电话局
* 电缆隧道：电话电缆通过电缆隧道进入电话局
* DSLAM：将ADSL信号还原为信元
* BAS：将信元还原为网络包，丢弃MAC头部、PPPoE头部，添加隧道专用头部
* 隧道专用路由器：取出IP包，转发到互联网内部

![ADSL结构-1](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/ADSL-1.png)

![ADSL结构-2](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/ADSL-2.png)

### 分离器

分离ADSL信号和语音信号

![分离器](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/splitter.png)

### 电话电缆

多条信号线捆绑在一起形成电话电缆，架设在电线杆上

![电话电缆](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/electric-cable.png)

### DSLAM

DSL Access Multiplexer，数字用户线接入复用设备，多个ADSL Modem 整合在一
个外壳里的设备

## 包传输

* 用户端将包发送给互联网接入路由器
* 互联网接入路由器给包加上MAC头部、PPPoE头部、PPP头部发送给ADSL Modem
* ADSL Modem将包拆分为ATM信元，并将信元按正交振幅调制为电信号，发送给分离器
* 分离器将ADSL信号和语音信号混合在一起通过电话线传输，在另一端分离
* DSLAM接收电信号，还原为信元，发送给BAS
* BAS接收信元，还原为网络包，丢弃MAC头部、PPPoE头部，加上隧道专用头部L2TP，发送到隧道
* 隧道专用路由器取出IP包，转发到互联网内部

![ADSL包](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/ADSL-package.png)

### ATM

Asynchronous Transfer Mode，异步传输模式

* 在以电话线为载体的传统电话技术基础上扩展出来的一种通信方式
* 以信元为单位进行数据传输

### 信元

ATM的数据传输单元

* 头部：5字节
* 数据：48字节

### 正交振幅调制

将数字信号调制成ADSL信号

* 振幅调制：按振幅大小表示0、1
* 相位调制：按波开始的位置表示0、1
* 正交振幅：振幅和相位合起来表示两个比特

![正交振幅调制](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/modem.png)

### 频分复用

使用多个频率的波来传输信号

* 4kHz以下：传输电话信号
* 4kHz~1.1MHz：划分成256个频宽为4.3125KHz的子频带
 * 20KHz到138KHz的频段用来传送上行信号
 * 138KHz到1.1MHZ的频段用来传送下行信号

![频分复用](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/fdm.png)
