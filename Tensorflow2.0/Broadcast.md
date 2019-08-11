# Broadcast
当两个tensor进行运算的时候,如果他们的维度不同导致不能进行运算,通过Broadcast可以进行数据的扩张
**与tf.file的一个区别是,Broadcast进行了数据的扩张,但是不会真的进行 数据的复制,没有占用内存,而tf.file进行了数据的复制**

## 显式的使用Broadcast
tf.broadcast_to

## 能否使用broadcast
1. 首先看维度是否相同,不同的话会创建新的维度,shape为1
2. 如果维度相同,shape不同,那就看每个维度是否有shape为1,有的话就能进行扩张