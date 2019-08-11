# Junit
- JUnit是java的测试工具，不需要main方法也可以运行
- 使用的时候需要导入包，但是实际上大部分IDE都已经包含了
- 只要在方法上面写@Test，然后淡入就可以
- 除了Test还有Before，After方法
- Before修饰的方法可以在每个Test修饰的方法运行前运行，After与之相反

```java
 @org.junit.jupiter.api.Test
    public void test1(){
        System.out.println("1");
    }

    @BeforeEach
    public  void eachinit(){
        System.out.println("单个初始化");
    }

    @AfterEach
    public void overeach(){
        System.out.println("单个结束");
    }

```