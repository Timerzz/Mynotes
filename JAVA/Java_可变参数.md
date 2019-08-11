# 可变参数

- 定义方法的时候，在参数类型后面加三个点，表示该类型随便可以传多少个
- 注意：可变参数要放在其他参数的后面
- 可以用fore方法遍历每一参数

```java
public void eat(int...i){
    for(int n : i){
        System.out.println(n);
    }
}
```

```java
public void eat(int i,String...strings){
	System.out.println(i);
    for(int s:strings){
        System.out.println(s);
    }
}
```