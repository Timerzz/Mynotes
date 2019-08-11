1.	 缺省方式：无参构造
<!-- 第一种方式 缺省：无参构造 -->
<bean id="user" class="com.igeek.excellence.entity.User"></bean>

2.	 静态工厂方法
public class UserStaticFactory {
	public static User getUser() {
		User user = new User();
		user.setName("宗伟");
		user.setPwd("123");
		return user;
	}
}
	<!-- 第二种方式  静态工厂方法 -->
	<bean id="user1" class="com.igeek.excellence.factory.UserStaticFactory" factory-method="getUser"></bean>

3.	 实例工厂方法
public class UserInstanceFactory {
	public User getUser() {
		User user = new User();
		user.setName("宗彭");
		user.setPwd("abc");
		return user;
	}
}
	<!-- 第三种方式  实例工厂方法 -->
	<bean id="instanceUser" class="com.igeek.excellence.factory.UserInstanceFactory"></bean>
	<bean id="user2" factory-bean="instanceUser" factory-method="getUser"></bean>

4.	 FactoryBean
public class UserFactoryBean implements FactoryBean<User>{
	public User getObject() throws Exception {
		User user = new User();
		user.setName("彭宗");
		user.setPwd("aaa");
		return user;
	}}
	
	<!-- 第四种方式  FactoryBean -->
<bean id="user3" class="com.igeek.excellence.factory.UserFactoryBean"></bean>
