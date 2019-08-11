# 数据库与Java的连接
1. 导入jdbc的jar包
2. 用反射Class.forName("com.mysql.cj.jdbc.Driver")创建Driver对象
3. 创建DriverManager对象  //注意：musql8.0需要加上时区关闭useSSL
4. 通过DriverManager对象对数据库进行操作
- 实例：
```java
try {
			Class.forName("com.mysql.cj.jdbc.Driver");
		} catch (ClassNotFoundException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		try {
			String db_url=
			"jdbc:mysql://localhost:3306/mydb?useSSL=false&serverTimezone=UTC"; 
			Connection con=DriverManager.getConnection(db_url,"root","root");
			}
```

## 数据库操作
1. 不传参数用Statement
```java
Statement st=con.createStatement();
st.execute("insert into teacher(t_name) values('jdbc')");
```

2. 传入参数用PreparedStatement
```java
PreparedStatement ps=con.prepareStatement("insert into teacher(t_name) values(?)");
ps.setString(1, "雨露");
ps.executeUpdate();
```
- 注意，setString的时候，下标从1开始

## 查询
- 数据库查询需要用ResultSet承接返回的值
```java
PreparedStatement ps=con.prepareStatement("select * from student where s_no= ?");
ps.setString(1, "1001");
ResultSet rs=ps.executeQuery();
while(rs.next()) {
	System.out.println("学号："+rs.getInt(1)+",姓名："+rs.getString(2)+",年龄"+rs.getInt(3));
				}
```

## 批量操作
- 如果操作比较多，可以先通过addBatch添加到队列
- 最后通过executeBatch()生效
```java
for(int i=0;i<10000;i++) {
String name=String.valueOf((char)(random.nextInt(1000)+20000)+(char)(random.nextInt(1000)+20000)+(char)(random.nextInt(1000)+20000));
ps.setString(1,name);
ps.setString(2, i%50+"");
ps.setString(3, random.nextInt(2)==1?"男":"女");
ps.addBatch();

}
System.out.println("操作数据库中...");
ps.executeBatch();
```

