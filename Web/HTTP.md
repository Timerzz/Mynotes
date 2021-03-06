# http
> http是一种无状态的协议
- 关于http1.x与http的区别，可以见
[HTTP2简介和基于HTTP2的Web优化](https://github.com/creeperyang/blog/issues/23)

## 结构
- http1.x请求一般有以下结构
```
请求行
零个或者多行请求头
空行
请求体
```
- http1.x响应一般有以下结构
```
状态行
零个或者多行响应头
空行
报文主体
```
- http1.x与2的结构区别如下：
![](img/http1与2.png)

## 请求方法
http请求有以下请求方法:
```
GET
POST
HEAD
PUT
DELETE
TRACE  命令服务器返回请求本身,
OPTIONS 命令服务器返回它支持的HTTP方法列表
CONNECT  命令服务器与客户端建立网络连接,通常用于设置SSL隧道开启HTTPS功能
PATCH 命令服务器使用报文主体中数据对URL资源进行修改
```

### 安全的请求方法
>	如果一个方法不会对服务器状态做任何 修改,那么这个方法就是安全的
#### 幂等的请求方法
>	如果一个方法在使用同样的数据进行第二次请求的时候,不会对服务器状态造成任何改变,那么这个方法就是幂等的。所有安全方法天生就是幂等的

## 请求头
| 字段| 作用 |
|------|-------|
|   Accept   |  客户端希望接受的内容类型 比如：Accept:text/html|
|   Accept-Charset   |  客户端希望接收的字符集编码    |
|   Cookie   |  服务器之前设置的cookie,多个cookie用分号分割    |
|   Content-Length   |  请求体字节长度     |
|   Content-Type   |  请求体内容类型     |
|   Host   |  服务器名称及端口     |
|   Referrer   |  发起请求的页面所在地址     |
|   User-Agent  |  对客户端进行描述     |









