## Set


- 声明
```js
let mset = new Set(['1','2','3'])
console.log(mset)
```


- 属性
 - 获取集合的长度
```js
let mset = new Set(['1','2','3'])
console.log(mset.size)
```

- 方法
	- add
```js
	let mset = new Set(['1','2','3','2'])
mset.add('5').add('6')
console.log(mset.size)
//支持链式调用
```
	- delet 与add类似
	- has  判断是否有某个元素
```js
let mset = new Set(['1','2','3','2'])
console.log(mset.has("1"))
```
	- clear 清空集合
