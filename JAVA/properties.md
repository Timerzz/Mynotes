# properties
- 执行的时候，类就不能进行修改了
- 但是配置文件修改之后是可以实时生效的
- properties类就可以用来存储和生成配置文件

## properties的特点
- properties和map一样存储的是键值对
## 使用方法
- 创建并读取
```java
public class TestProperties {
    public static void main(String[] args) throws IOException {
        var p =new Properties();
        p.put("name","张浩港");  //存放键值对
        p.put("age","12");
        p.store(new FileWriter(new File("zhg.properties")),"utf-8"); 
        //生成配置文件，通过output输出流写入，用utf-8编码
    }
}
```
- 读取properties文件
```java
public class TestProperties {
    public static void main(String[] args) throws IOException {
        var p =new Properties();
        p.load(new FileReader(new File("zhg.properties")));
        System.out.println(p);
    }
}
```
- 通过stringPropertyNames可以获得所有key的名字
- getProperty可以通过名字获得值
```java
public class TestProperties {
    public static void main(String[] args) throws IOException {
        var p =new Properties();
        p.load(new FileReader(new File("zhg.properties")));
        var names=p.stringPropertyNames();
        for (String name : names) {
            System.out.println(name+":"+p.getProperty(name));
        }
    }
}
```