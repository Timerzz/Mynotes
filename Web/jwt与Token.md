## jwt
> json web token 简称 jwt.他是一种轻量级的规范.这种规范允许客户端和服务端之间传递一些非敏
>感信息.
>常用于用户认证和授权系统.
>
## jwt的组成
> 1. Header
> 2. Claims
> 3. Signature

## Header 组成部分
```go
    typ: "JWT",
    alg: "HS256"
```
typ是默认的一种标识.标识这条信息采用JWT规范.
alg表示签名使用的加密算法.通常有ES256,ES512,RS256等等

## Claims 组成部分
```go
Audience  string `json:"aud,omitempty"`
ExpiresAt int64  `json:"exp,omitempty"`
Id        string `json:"jti,omitempty"`
IssuedAt  int64  `json:"iat,omitempty"`
Issuer    string `json:"iss,omitempty"`
NotBefore int64  `json:"nbf,omitempty"`
Subject   string `json:"sub,omitempty"`
```
这段结构体是我们在golang中使用到的字段. 可以在这个的基础上进行组合,定义新的Claims部分.

```go
1. aud 标识token的接收者.
2. exp 过期时间.通常与Unix UTC时间做对比过期后token无效
3. jti 是自定义的id号 
4. iat 签名发行时间.
5. iss 是签名的发行者.
6. nbf 这条token信息生效时间.这个值可以不设置,但是设定后,一定要大于当前Unix UTC,否则token将会延迟生效.
7. sub 签名面向的用户
```
通过设置exp与nbf来管理token的生命周期.

## Signature 组成部分
将Header与Claims信息拼接起来[base64(header)+"."+base64(claims)],采用Header中指定的加密算法进行加密,得到Signature部分.
## token组成部分
base64(header) + “.” + base64(claims) + “.” + 加密签名

## go语言Jwt
```go
if passwd == user.Password {

            // 带权限创建令牌
            claims := make(jwt.MapClaims)
            claims["username"] = username
            if username == "admin" {
                claims["admin"] = "true"
            } else {
                claims["admin"] = "false"
            }
            claims["exp"] = time.Now().Add(time.Hour * 480).Unix() //20天有效期，过期需要重新登录获取token
            token := jwt.NewWithClaims(jwt.SigningMethodHS256, claims)

            // 使用自定义字符串加密 and get the complete encoded token as a string
            tokenString, err := token.SignedString([]byte("mykey"))
            if err != nil {
                beego.Error("jwt.SignedString:", err)
                this.RetError(errSystem)
                return
            }
            this.Data["json"] = map[string]interface{}{"status": 200, "message": "login success ", "moreinfo": tokenString}
        } else {
            this.Data["json"] = map[string]interface{}{"status": 400, "message": "login failed ", "moreinfo": time.Now().Format("2006-01-02 15:04:05")}
        }
```
