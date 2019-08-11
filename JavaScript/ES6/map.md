## map
> 在js中,map与对象有区别,map可以将任意东西作为键,包括对象,而对象,只能用字符串作为键

## 声明
```js
let obj1 = {'1':1}
let map = new Map([
    ['123', 123],
    [obj1,'objjjj1']
])
console.log(map)
//Map { '123' => 123, { '1': 1 } => 'objjjj1' }
```

### 方法
- size  和set中的类似
- set   添加键值对
```js
let obj1 = {'1':1}

let map = new Map([
    ['123', 123],
    [obj1,'objjjj1']
])

map.set("friends",['zzz','vvv'])
//Map {
 // '123' => 123,
 // { '1': 1 } => 'objjjj1',
  //'friends' => [ 'zzz', 'vvv' ]
//}
```
- 遍历
```js
map.forEach((key,val)=>{
    console.log(key)
    console.log(val)
})
```
