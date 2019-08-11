# getitem方法
在python的类中,如果定定义了这个方法,就可以通过[]符号访问数据
在这个类对象后面使用[]符号,会自动调用这个方法
```python
class test:
    t = 3
    def __getitem__(self,key):
    	return self.t,key

a = test()
a[1]   #(3, 1)
a['e']  # (3,'e')
```