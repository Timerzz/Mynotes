javaBean正常的生命周期为三个，构造函数，初始化，销毁
通过Spring后置处理器可以增加生命周期

步骤：
1. 创建类实现BeanPostProcessor接口，实现方法
```java
public class MyProcesser implements BeanPostProcessor{
	public Object postProcessBeforeInitialization(Object bean, String beanName) throws BeansException {
		System.out.println("Bean初始化之前");
		return bean;
	}
	public Object postProcessAfterInitialization(Object bean, String beanName) throws BeansException {
		// TODO Auto-generated method stub
		System.out.println("Bean初始化之后");
		return bean;
	}
}
```
这个接口中两个方法，一个在初始化之前调用，一个在初始化之后调用

2. xml配置文件中，引入这个类
```xml
<bean class="com.igeek.excellence.processer.MyProcesser"></bean>
```
引入后只要是这个配置文件中实现的Bean都会在初始化之前和之后加上这两个方法。
