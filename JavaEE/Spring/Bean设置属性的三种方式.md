1. 通过property设置
在配置文件中，在bean里添加prioperty标签作为参数
```xml
<bean id="stu" class="com.igeek.excellence.enticy.Student" >
	<property value="张" name="name"></property>
	<property value="18" name="age"></property>
</bean>
```
- 先通过无参构造实例化，再添加property属性，所以只要有无参构造

2. 通过构造器设置，用的是有参构造
```xml
    <bean id="tea" class="com.igeek.excellence.enticy.Teacher" >
        <constructor-arg index="0" value="波多"></constructor-arg>
    </bean>
```
index表示用第几位参数，value是传入的值

3. 通过ref（其实是手动依赖注入）
- 上面两种方式只能插入基本数据类型和String，如果属性是一个类，就只能使用ref
```xml
  <bean id="stu" class="com.igeek.excellence.enticy.Student" >
        <property value="张" name="name"></property>
        <property value="18" name="age"></property>
        <property name="tea" ref="tea"></property>   //用了ref
</bean>
 <bean id="tea" class="com.igeek.excellence.enticy.Teacher" >
        <constructor-arg index="0" value="波多"></constructor-arg>
</bean>
```
- 注意，ref设置的类，必须是已经声明了的。


## 特殊参数类型
1. List
Student中有一个List的属性
通过配置文件赋值
```xml
 <bean id="stu" class="com.igeek.excellence.enticy.Student" autowire="byType">
        <property value="张" name="name"></property>
        <property value="18" name="age"></property>
        <property name="hobbies" >
            <list>
                <value>看书</value>
                <value>看电视</value>
            </list>
        </property>
</bean>
```

如果list里面放的是复杂数据类型，就用ref
```xml
  <bean id="stu" class="com.igeek.excellence.enticy.Student" autowire="byName">
        <property value="张" name="name"></property>
        <property value="18" name="age"></property>
        <property name="hobbies" >
            <list>
                <ref bean="tea"></ref>
                <ref bean="tea1"></ref>
            </list>
        </property>
</bean>
```

2. map
```xml
  <property name="score">
            <map>
                <entry key="ass" value="60"></entry>
                <entry key="we" value="70"></entry>
            </map>
</property>
```