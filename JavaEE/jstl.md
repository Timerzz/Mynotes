<c:set var="sex" value="男" scope="application"></c:set>

<c:out value="${sex}" default="中性"></c:out>
<c:if test="${sex=='男'}">
    <div>ig牛逼</div>
</c:if>

<c:choose>
    <c:when test="${sex == '男'}">
        这是男的
    </c:when>
    <c:when test="${sex == '女'}">
        这是女的
    </c:when>
    <c:when test="${sex == '中性'}">
        这是中性
    </c:when>
</c:choose>

<c:forEach var="item" items="${list}">

<div>账号：${item.uname} 密码：${item.upwd}</div>

</c:forEach>

<c:forEach var="num" begin="1" end="3">
    
</c:forEach>

<c:set var="ages" value="12,32,44,51"></c:set>

<c:forTokens items="${ages}" delims="," var="age">
    <div>年龄${age}</div>
</c:forTokens>

<c:remove var="sex"></c:remove>
<c:out value="${sex}"></c:out>