# Set
## Set和List都继承于Collection类，而Collections是它的工具类
- set是集合，与python中相同，不能重复
- set接口有几个实现类
- set都有的方法contains()方法判断是否存在某元素

## HashSet
- HashSet无序且不重复
- 由于无序所以没有get方法通过下表获得元素
```java
var hS=new HashSet<String>();
hS.add("a");
hS.add("a");
hS.add("b");
hs.contains("a");//是否存在a
System.out.println(hS.toString()); //[a, b]
```

## TreeSet
- TreeSet有序不重复
- TreeSet的排序方法不是根据放入的顺序排序，而是根据Asc或者定义的比较器进行比较
```java
var ts=new TreeSet<String>() ;
ts.add("bb");
ts.add("c");
ts.add("a");
ts.add("1a");
System.out.println(ts.contains("a"));
System.out.println(ts);    //[1a, a, bb, c]
```