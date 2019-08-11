# tensorboard
先在cmd 输入tensorboard --logdir logs 监听需要监听的文件夹
summary_writer = tf.summary.create_file_writer(log_dir) 
```python
curr_time = datetime.datetime.now().strftime('%Y%m%d-%H%M%S')
log_dir = 'logs/'+ curr_time
summary_writer = tf.summary.create_file_writer(log_dir)
with summary_writer.as_default():
    tf.summary.image("Train Sample:",a,step =0)  # 图片可视化
    tf.summary.scalar('test:',float(n),step=step) # 数值的可视化
```