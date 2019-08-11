1. 创建cookie
```java
var cookie=new Cookie(uname,upwd);
```
2. 设置cookie存在时间
```java
cookie.setMaxAge(1*30*24*60*60);   //存在多少秒
```

3. 添加cookie
```java
resp.addCookie(cookie);
```

4.获取cookie
```java
var hrep=(HttpServletRequest)req;
var cookies=hrep.getCookies();
```