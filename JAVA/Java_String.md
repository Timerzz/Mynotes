# String的方法

* 效率:StringBuilder>StringBuffer>String 
* 字符串经常变动用StringBuilder，多线程情况用StringBuffer，不经常变更就用String

## String 转换成Char数组

 * str.toCharArray

## String SubString
* str.subString  //截取str一段字符串

## String toUpCase(toLowCase)
* 转换大小写

## String trim()
* 去掉两端空格

## replace()
```java
String s="abc";
String s2=s.replace("ab","x")；
System.out.println(s) ；    //结果：abc
System.out.println(s2)  ；  //结果：xc
```
