# MIME类型

标签（空格分隔）： 网络基础

---

Multipurpose Internet Mail Extensions，媒体类型

## 结构

```
type/subtype
```

## 类型

| 类型 | 描述 | 示例 |
| --- | --- | --- |
| text | 普通文本 | text/plain, text/html, text/css, text/javascript |
| image | 图像 | image/gif, image/png, image/jpeg, image/svg+xml, image/bmp, image/webp, image/x-icon |
| audio | 音频 | audio/webm, audio/ogg, audio/wav |
| video | 视频 | video/webm, video/ogg |
| application | 二进制数据 | application/octet-stream, application/json,   application/xml, application/pdf |
| multipart | 多部分文档 | multipart/form-data, multipart/byteranges |

### multipart/form-data

表单提交数据

```
Content-Type: multipart/form-data; boundary=aBoundaryString
(other headers associated with the multipart document as a whole)

--aBoundaryString
Content-Disposition: form-data; name="myFile"; filename="img.jpg"
Content-Type: image/jpeg

(data)
--aBoundaryString
Content-Disposition: form-data; name="myField"

(data)
--aBoundaryString
(more subparts)
--aBoundaryString--
```

### multipart/byteranges

部分内容返回

```
HTTP/1.1 206 Partial Content
Accept-Ranges: bytes
Content-Type: multipart/byteranges; boundary=3d6b6a416f9b5
Content-Length: 385

--3d6b6a416f9b5
Content-Type: text/html
Content-Range: bytes 100-200/1270

eta http-equiv="Content-type" content="text/html; charset=utf-8" />
    <meta name="vieport" content
--3d6b6a416f9b5
Content-Type: text/html
Content-Range: bytes 300-400/1270

-color: #f0f0f2;
        margin: 0;
        padding: 0;
        font-family: "Open Sans", "Helvetica
--3d6b6a416f9b5--
```
