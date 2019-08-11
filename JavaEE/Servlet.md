servlets需要自带的那个容器或者Tomcat


- 重写方法
1. service（HttpServletRequest req, HttpServletResponse resp）
第一个参数是接收，第二个是发送
req.getMethod()   获得访问方式
req.getParameter("userName")  获得get或者post的方式
service是dopost和doget的集合
2. init（）初始化
3. 无参构造实例化
4.destroy()销毁的时候运行

- 生命周期
1. 在第一个用户访问并使用到的时候会实例化，初始化
2. 然后调用service方法
3. 后面的用户再访问的时候，就不会实例化和初始化，直接调用service