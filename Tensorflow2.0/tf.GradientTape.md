# tf.GradientTape

## 自动求导
gradient(y,x)
对y进行x求导,x可以是多个,那就按顺序求
```python
with tf.GradientTape() as tape:
	grades = tape.gradient(loss,model.trainable_variables)
	optimizer.apply_gradients(zip(grades,model.trainable_variables))
```