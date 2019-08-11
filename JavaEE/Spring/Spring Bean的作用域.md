默认情况下Spring、bean是单例模式，不管getBean多少个对象，都是同一个。
通过修改作用域可以改变模式
1.	Singleton : 单例，IOC容器中只会存在一个对象，默认是单例
2.	Prototype :原型，容器启动时不会实例化bean，每次getBean时才会实例化，生命周期交于自己管理
3.	Request ： 每次请求都会创建一个对象
4.	Session ：每个Session都会创建一个对象
在配置文件中，对Bean修改scrope属性
```xml
<bean id="propercess" class="com.igeek.excellence.propercess.propress" scope="prototype"></bean>
```