# Collections是Collection工具类
- set和list继承于Collection

## 方法
1. addAll    添加多个
```java
var list =new LinkedList<String>();
Collections.addAll(list, "a","b","c","d");   //添加多个
System.out.println(list);
```

2. shuffle   随机打乱
```java
var list =new LinkedList<String>();
Collections.addAll(list, "a","b","c","d");

Collections.shuffle(list);
System.out.println(list);
```

