# BeanUtils
- Beanutils是额外的jar包，使用需要commons-logging.jar
- 主要可以简化一些发射的封装，赋值等

## 赋值
- 通过反射获得类，创建对象后，对属性赋值往往需要突破封装等操作
- BeanUtils可以简化这个过程
- setProperty
```java
var student=classObj.getDeclaredConstructor().newInstance();
BeanUtils.setProperty(student,"name","zzz");
System.out.println(student);
```

- populate
- 通过map对象赋多个值
- 注意：map中的key的名字必须与赋值对象的属性相同
```java
var maps= new HashMap();
maps.put("name","张浩港");
maps.put("age",12);
BeanUtils.populate(student,maps);
System.out.println(student);
```

## getProperty获取值
```java
 System.out.println(BeanUtils.getProperty(student,"name"));
```

## copyProperties深拷贝一个对象
```java
var newStudent=classObj.getDeclaredConstructor().newInstance();
BeanUtils.copyProperties(newStudent,student);
System.out.println(newStudent);
```