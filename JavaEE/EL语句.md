<h1><%=request.getAttribute("name")%>登录成功！</h1>
<h1>${name}</h1>
<h1>${user.getUname()}</h1>
<h1>${user.uname}</h1>
<h2>${pwd!=null?pwd:"没有密码"}</h2>
<h2>${empty pwd}</h2>
<%--empty判断是否为空--%>
<h2>${i==j}</h2>