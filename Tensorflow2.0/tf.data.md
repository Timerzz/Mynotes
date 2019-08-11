# tf.data相关操作

## Dataset
```python
train_db = tf.data.Dataset.from_tensor_slices((x,y)).batch(200)
```

## Dataset的功能
1. shuffle打散
```python
db = tf.data.Dataset.from_tensor_slices((x,y))
db = db.shuffle(10000)  # 这个参数是指在这个区域内进行打散
```

2. map  和python自带的map类似
```python
def preprocess(x,y):
	x = tf.cast(x,dtype = tf.float32)/255
	y = tf.cast(y,dtype = tf.float32)
	y = tf.one_hot(y,depth=10)
	return x,y
db = db.map(preprocess)
```

3. batch
db = db.batch(32)

4. repeat
可以指定迭代几次
```python
db4 = db.repeat(4)
# 用for循环迭代db4的时候,就不会迭代一次就退出,而是会迭代4次
```
