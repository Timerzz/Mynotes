## list的函数
1. index(a)
返回a在list中的下标，如果没有会报错
```python
lists=[1,2,3,'a']
lists.index('a')   //返回3
```
2. clear()
将列表清空
```python
lists.clear()   //列表就饿空了
```
3. count（a）
返回a元素在列表中出现的次数
```python
l=[1,2,3,'a',1]
l.count(1)    //返回2，因为有两个1
```
4. extend(l2)
在列表后面添加另一个列表的内容，可以是迭代器
注意添加后是直接对原列表进行修改，而用+连接两个列表不会对两个列表进行修改
```python
l1=[1,2,3,'a',1]
l2=[7,8]
l1.extend(l2)
print(l1)        //[1, 2, 3, 'a', 1, 7, 8]而l2不变
//l1+l2也能连接列表，但是原列表不会改表
```
5. reverse()
列表反向
```python
l1=[1,2,3,'a',1]
l1.reverse()   //l1就是[1, 'a', 3, 2, 1]
```
6. insert（index,a）
在index下标位置插入a

7. remove(a)
删除list中的a元素

## 创建全是一个数的list
```python
l=[0 for _ in range(5)]
```
生成一个5个0的数组