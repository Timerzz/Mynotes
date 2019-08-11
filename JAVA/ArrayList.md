# ArrayList

## 添加

```java
ArrayList list=new ArrayList(2);
list.add(123);
list.add("abc");
list.add(false);
list.add(0,34);     //在0起点添加34
System.out.println(list.toString());   //[34, 123, abc, false]
System.out.println(list.get(1));  //123
```

## 删除remove,修改

```java
ArrayList list=new ArrayList(2);
list.add(123);
list.add("abc");
list.add(false);		
list.add(0,34);
list.set(1,"xxx");   //将第0个设为xxx
list.remove(list.size()-1);    //删除最后一个
System.out.println(list.toString());
System.out.println(list.size());     //.saize（）数组的元素个数
```

## 数组与List的转换
```java
String[] Str= {"a","b","c"};
var list=new LinkedList<String>();
list.addAll(Arrays.asList(Str));   //从数组转换为list
System.out.println(list);
```

