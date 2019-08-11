# StringBuilder

## 构造方法

```java
StringBuilder sb=new StringBuilder("abc");
String s="abc";
StringBuilder sb2=new StringBuilder(s);
```

## replace方法

```java
StringBuilder sbd=new StringBuilder("abc");
System.out.println(sbd);    //abc
sbd.replace(0, 2, "sfd");    
System.out.println(sbd);   //sbdc
```

## 拼接append

```java
StringBuilder S=new StringBuilder("abc");
s.append("def");
```

## 删除delete

```java
StringBuilder sbd=new StringBuilder("1234567");
		System.out.println(sbd);    
		sbd.delete(2, 3);
		System.out.println(sbd);//124567
```

## 插入insert

