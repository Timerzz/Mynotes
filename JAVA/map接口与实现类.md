# map接口 （python中的字典）
- 实现类：HashMap，TreeMap，


## HashMap   建和值都可以为null
```java
var map=new HashMap<String,Integer>();
map.put("name",  12);           //存放

Set<String> keys=map.keySet();      //获得键的集合
Collection<Integer> Values=map.values();//获得值的集合
System.out.println("key:"+keys);
System.out.println("value"+Values);

for (var entry: map.entrySet())
System.out.println(entry);        //Entry是map封装的键值对类，通过entryset可以获得整个map

System.out.println(map.get("name")); //get取出
```

## TreeMap    有序，键不能为null,值可以为null
- 类似

## HashTable 线程安全  键值都不能为null

### LinkedHashMap
- 有序的HashMap键值都能null
- 这个有序与TreeMap不同。这里的有序是按存放顺序取
