# RESTful（Representational State Transfer）
>(资源的)表现层状态转化
>

## 为什么是资源的表现层
>在互联网，一个具体的信息就是一个资源，可以是一段文本，一首歌等等。我们用一个**URL**指向它，每个资源对应一个独一无二的URL，这个URL就好像它的id，我们要获取这个资源，就访问这个URL。
>

## 表现层
> 资源是信息实体，比如文本，而表现层就是具体的形式比如它可以是txt,csv
> 

## 状态转化
>HTTP协议，是一个无状态协议。这意味着，所有的状态都保存在服务器端。因此，如果客户端想要操作服务器，必须通过某种手段，让服务器端发生"状态转化"（State Transfer）。而这种转化是建立在表现层之上的，所以就是"表现层状态转化
>具体来说的手段就是HTTP协议的四种操作动词：GET用来获取资源，POST用来新建资源（也可以用于更新资源），PUT用来更新资源，DELETE用来删除资源
>

## 设计思路
>进行一个操作，应该是动词+名词。而http的四个操作动词就是这个动词，所以URL的设计中，应当只能出现名词
举例来说，某个URI是/posts/show/1，其中show是动词，这个URI就设计错了，正确的写法应该是/posts/1，然后用GET方法表示show

## 误区
> 1. 在URL中加入版本号
> 不同的版本，可以理解成同一种资源的不同表现形式，所以应该采用同一个URI。版本号可以在HTTP请求头信息的Accept字段中进行区分：

　　Accept: vnd.example-com.foo+json; version=1.0

　　Accept: vnd.example-com.foo+json; version=1.1

　　Accept: vnd.example-com.foo+json; version=2.0
　　
## 设计原则
1. 避免多级URL
>多级分类不利于扩展，用查询字符串表达更好
```
GET /authors/12/categories/2

GET /authors/12?categories=2     //better
```

2. 服务器不返回纯文本
> 服务器一般应当返回json数据。因此服务器回应的 HTTP 头的Content-Type属性要设为application/json
