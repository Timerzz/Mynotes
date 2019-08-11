1. 字典也可以用生成式，而且可以条件判断
```python
dic={1:1,2:2,3:3,4:4}
dic = {k:v for k,v  in dic.items() if v >2}
dic
```