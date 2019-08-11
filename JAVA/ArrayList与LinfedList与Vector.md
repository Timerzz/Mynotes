# ArrayList与LinkedList与Vector的区别
## Set和List都继承于Collection类，而Collections是它的工具类
1. ArrayList是可变数组实现，查询比较快，插入和删除比较慢。因为每次插入和删除都要创建新的数组，所以效率比较低
2. LinkedList是链表格式实现，查询比较慢，插入和删除比较快。他还能帮我们清除内存碎片，
3. LinkedList还支持栈和队列
4. Vector与list没什么区别，但是他是线程安全的，所以效率低一点
5. 通用方法contains（）判断是否存在某元素
## LinkedList普通使用
```java
LinkedList<Integer> ls=new LinkedList<>();
ls.add(1);    //添加
ls.add(2);
ls.add(1, 3);    //在index=1，添加3
System.out.println(ls.toString());   //[1,3,2]

ls.remove(0);     //删除index=0的东西
System.out.println(ls.toString());    //[3,2]
```

## 栈的用法
```java
LinkedList<Integer> ls=new LinkedList<>();
ls.push(1);      //入栈
ls.push(2);
ls.push(3);

System.out.println(ls.toString()); 
System.out.println("出栈："+ls.pop());    //出栈
System.out.println("预测下一个出栈"+ls.peek());    //预测下一个出栈，但并不会真的出栈
System.out.println(ls.toString());

//[3, 2, 1]
//出栈：3
//预测下一个出栈2
//[2, 1]
```

## 队列的用法
```java
LinkedList<Integer> ls=new LinkedList<>();
ls.offer(1);     //入队列
ls.offer(2);
ls.offer(3);

System.out.println(ls.toString());
System.out.println("出栈："+ls.poll());   //出队列
System.out.println("预测下一个出队列"+ls.peek());   //预测
System.out.println(ls.toString());
//[1, 2, 3]
//出栈：1
//预测下一个出队列2
//[2, 3]
```

