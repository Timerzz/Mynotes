#  代码块执行顺序

- 代码块的执行在构造函数之前，但是父类的构造函数在子类代码块之前

```java
//父类
public class Test {

	public Test() {
		System.out.println("父构造");
	}

	{
		System.out.println("父代码块");
	}
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		new Testzi();
		
	}

}
//子类
class Testzi extends Test{
	public Testzi() {
		System.out.println("子构造");
	}
	{
		System.out.println("子代码块");
	}
}
```
	执行结果：
	父代码块
	父构造
	子代码块
	子构造

### 构造函数中调用其他构造函数
- 用this方法可以调用重载的其他构造函数
- 注意：this方法要写在开头。和super方法类似

```java
public Test() {
	this(1);       //在无参构造中调用了有参构造函数
	System.out.println("父无参构造");
}

public Test(int i){
	System.out.println("父有参构造");
}
```