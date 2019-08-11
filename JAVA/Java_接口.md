# 接口
- 接口用intrface定义
- 接口中的抽象方法恶意省略public 和 absolute
- JDK1.8之前接口中只能有常量和抽象方法
- JDK1.8之后可以有默认方法，静态方法
- JDK1.8之后，接口的实现可以使用lambda函数

- 示例：
```java
public class LambdaTest {
	public static void main(String[] args) {
		LambdaTest lTest=new LambdaTest();
		a add=(x,y)->(x+y); //lambda方法实现抽象方法
		a sub=(x,y)->x-y;
		a mul=(int x, int y)->x*y;
		System.out.println("方法一："+add.operat(1,2));
		System.out.println("方法二："+add.add(2, 3));
		System.out.print("方法三："+a.addtoo(1, 4));
		System.out.println("减操作："+lTest.chooseOne(10, 4, sub));
	}

	int chooseOne(int x,int y,a a1) {      //接口对象可以作为参数传入
		return a1.operat(x, y);
	}
	
	interface a {    //定义内部接口
		int  operat(int x,int y);	//普通的抽象方法,省略了public和absolute
		
		default int  add(int x,int y) { //默认方法
			return x+y;
			}
        
		static int addtoo(int x,int y) { //静态方法
			return x+y;
			}
		}
}
```