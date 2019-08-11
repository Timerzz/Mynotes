# JSP

JSP本质上会被编译成servlet


所以他自带request，和response
```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Title</title>
</head>
<body>
<%
    String name=request.getParameter("name");
    String  pwd=request.getParameter("pwd");
    System.out.println("账号："+name+",密码："+pwd);
%>
</body>
</html>
```
而form表单提交的地址直接就可以是这个jsp文件

1. 在jsp中批量生成标签
	1. 方法一
	```jsp
	   <%
        for(int i=0;i<10;i++){
             response.getWriter().write("<div>Ass We Can"+i+"</div>");
        }
    %>
	```
	2. 方法二
	```jsp
	<%  for(int i=0;i<10;i++){ %>

    <div>eeeeeeee</div>

	<% } %>
	```