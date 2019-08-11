## 高级接口
1. metrics测量表
```python
acc_meter = metrics.Accuracy()
loss_meter = metrics.Mean()

loss_meter.update_State(loss)   
acc_meter.update_state(y,pred)

#取数据
loss.meter.result().numpy()

#清缓存
loss_meter.reset_states()
```

2. Compile&fit
![compile](..\imgs\compile.PNG)


## 一些函数
1. summary()
model.summary()可以将网络情况打印出来

