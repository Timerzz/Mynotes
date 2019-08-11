# 创建Tensor

## from numpy
```python
a = tf.convert_to_tensor(np.ones([2,3]))
#<tf.Tensor: id=0, shape=(2, 3), dtype=float64, numpy=
#array([[1., 1., 1.],
#      [1., 1., 1.]])>
#注意,类型是float64
```
可以指定数据类型
```python
b = tf.convert_to_tensor(np.zeros([2,2]),dtype=tf.float32)
#<tf.Tensor: id=2, shape=(2, 2), dtype=float32, numpy=
#array([[0., 0.],
#      [0., 0.]], dtype=float32)>
```

## from list
```python
c = tf.convert_to_tensor([12,3])
#<tf.Tensor: id=4, shape=(2,), dtype=int32, numpy=array([12,  3])>
```

## tf.zeros
```python
d = tf.zeros(1)
d
#<tf.Tensor: id=11, shape=(1,), dtype=float32, numpy=array([0.], dtype=float32)>
e = tf.zeros([2,3,4])
e
#<tf.Tensor: id=15, shape=(2, 3, 4), dtype=float32, numpy=
#array([[[0., 0., 0., 0.],
#        [0., 0., 0., 0.],
#        [0., 0., 0., 0.]],

#       [[0., 0., 0., 0.],
#        [0., 0., 0., 0.],
#        [0., 0., 0., 0.]]], dtype=float32)>
```

### tf.zeros_like()
根据传入的值的shape创建全是0的tensor
```python
f = tf.zeros_like(a)
f
#<tf.Tensor: id=18, shape=(2, 3), dtype=float64, numpy=
#等价于tf.zeros(a.shape)
```

## tf.ones /tf.one_like
- 用法类似于 tf.zeros /tf.zeeros_like

## tf.fill
用指定的值填充指定的shape
```python
g = tf.fill([2,2],3)
g
#<tf.Tensor: id=25, shape=(2, 2), dtype=int32, numpy=
#array([[3, 3],
#       [3, 3]])>
```

## tf.random
### tf.random.normal
- mean 是均值,stddev是方差
```python
h = tf.random.normal([2,2],mean=1,stddev=2)
h
#<tf.Tensor: id=32, shape=(2, 2), dtype=float32, numpy=
#array([[ 1.1311908 , -2.641872  ],
#       [ 2.1963706 , -0.09618616]], dtype=float32)>
```

### tf.random.truncated_normal
- truncated是截取的意思,是对正态分布进行截取后,在进行随机取值
```python
g = tf.random.truncated_normal([2,2],mean = 1,stddev=1)
g
#<tf.Tensor: id=12, shape=(2, 2), dtype=float32, numpy=
#array([[-0.1410433 ,  0.27218056],
#       [ 0.49668992,  0.0555982 ]], dtype=float32)>
```

### tf.random.uniform
- 平均分布后,取随机值
```python
h = tf.random.uniform([2,2],minval=1,maxval=4)
h
```

## tf.comstant
和tf.convert_to_tensor()基本类似
