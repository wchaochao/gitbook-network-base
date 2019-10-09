# URI

标签（空格分隔）： 网络基础

---

Uniform Resource Identifier，统一资源标识符，用于唯一的标志资源

## 词法

```
uri ::: // URI
  uriCharacters(opt)

uriCharacters ::: // 多个URI字符
  uriCharacter uriCharacters(opt)

uriCharacter ::: // 单个URI字符
  uriUnescaped // URI非转义字符
  uriReserved // URI保留字符
  uriEscaped // URI转义字符

uriUnescaped :::  // URI非转义字符
  uriAlpha // URI字母
  DecimalDigit // 十进制数字
  uriMark // URI标记

uriAlpha ::: one of // URI字母
  a b c d e f g h i j k l m n o p q r s t u v w x y z
  A B C D E F G H I J K L M N O P Q R S T U V W X Y Z

uriMark ::: one of // URI标记
  - _ . ! ~ * ' ( )

uriReserved ::: one of // URI保留字符
  ; / ? : @ & = + $ ,

uriEscaped ::: // URI转义字符
  % HexDigit HexDigit
```

转义，使用UTF-8编码，再把每个字节使用两个十六进制表示，前面加上%

* URI非转义字符：不需要转义
* URI保留字符：有时需要转义，如查询参数里的值
* URI转义字符：一定要转义

```
字'转码：%E5%AD%97
```

## URL

Uniform Resource Location，统一资源定位符，通过位置标志资源

![URL](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/url.png)

### 组成

![URL组成](https://raw.githubusercontent.com/wchaochao/images/master/gitbook-network-base/url-structure.png)

* `protocol`: 协议
* `username`: 用户名，用于权限验证，可省略
* `password`: 密码，用于权限验证，可省略
* `host`: 主机，由主机名和端口号组成
* `hostname`: 主机名，对应具体的服务器
* `port`: 端口号，对应服务器程序，省略时为协议默认的端口
* `origin`: 源，由协议和主机组成，用于判断同源
* `pathname`: 资源路径
* `search`: 查询参数，可省略
* `hash`: hash片段，可省略

### protocol

| 协议 | 说明 | 默认端口 |
| --- | --- | --- |
| http | 超文本传输 | 80 |
| https | 安全的超文本传输 | 443 |
| ws | WebSocket连接 | 80 |
| wss | 安全的WebSocket连接 | 443 |
| ftp | 文件传输 | 21 |
| ssh | 安全Shell | 22 |
| telnet | 远程登录 | 23 |
| smtp | 发送邮件 | 25 |
| dns | DNS查询 | 53 |
| mailto | 电子邮件地址 | 无 |
| file | 本地文件 | 无 |
| data | 嵌入小文件 | 无 |
| view-source | 网页源代码 | 无 |

### hostname

使用IP或域名指定主机

* IP: IP对应的服务器
* 域名：通过DNS服务器转换为IP

### pathname

由目录 + 文件名组成，文件名有时可省略

```
// 目录 + 文件名
http://www.lab.glasscom.com/dir/index.html

// 省略文件名，访问目录下的默认文件
http://www.lab.glasscom.com/dir/ // 访问/dir/index.html或/dir/default.html
http://www.lab.glasscom.com/ // 访问/index.html或/default.html
http://www.lab.glasscom.com // 相当于http://www.lab.glasscom.com/

// 省略/，先当文件处理，没有当目录处理
http://www.lab.glasscom.com/whatisthis
```

## URN

Uniform Resource Name，统一资源名称，通过名称标志资源

```
urn:isbn:9780141036144 // 书号
urn:ietf:rfc:7230 // RFC文件
```
