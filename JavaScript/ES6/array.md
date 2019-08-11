## Array.from
> 可以将一些伪数组,装换为真的数组
```js
var li = document.querySelectorAll('li');   //获取的一般是Nodelist
var new_li = Array.from(li)
console.log(typeof new_li)
```

## Array.of
>可以传入多个值,合为数组
```js
let mylist = Array.of(1,2,3,4)
console.log(mylist)
```

## 延展操作符
> 可以将传入的数据转化为数组
```js
s = "今天天气不错"
console.log(...s)
```
