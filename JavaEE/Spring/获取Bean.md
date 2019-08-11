- javaBean其实就是可以实例化的java对象

spring通过配置文件可以获得bean
1. 通过id获取
spring的配置文件：
```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">
    <bean id="stu" class="com.igeek.excellence.enticy.Student" >
        <property value="张" name="name"></property>
        <property value="18" name="age"></property>
    </bean>
    <bean id="tea" class="com.igeek.excellence.enticy.Teacher" >
        <property value="苍老师" name="name"></property>
    </bean>
</beans>
```
spring可以通过id获取bean
```java
var ac=new ClassPathXmlApplicationContext("spring-config.xml");
var stu=(Student)ac.getBean("stu");
var tea=(Teacher)ac.getBean("tea");
System.out.println(stu);
System.out.println(tea);
```
- new ClassPathXmlApplicationContext("spring-config.xml");是通过配置文件实例化容器对象，在这个过程中。容器会实例化所有配置文件中的bean，相当于把bean的声明周期交给了容器，用到的时候直接问容器要。
- getBean则可以通过id获取bean对象

2. 通过类型获取
getBean也可以通过类型获取Bean
```java
var ac=new ClassPathXmlApplicationContext("spring-config.xml");
var tea=(Teacher)ac.getBean(Teacher.class);
System.out.println(tea);
```

## ApplicationContext与BeanFactory
- 都可以用来获取Bean
```java
var ac=new ClassPathXmlApplicationContext("spring-config.xml");
var bf=ac.getBeanFactory();
var stu=(Student)bf.getBean("stu");
System.out.println(stu);
```
