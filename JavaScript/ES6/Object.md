## Object.assign

> 可以将多个对象合并到一个对象
>
> ```js
> p1 = {name:"zzz"}
p2 = {age:13}
p3 = {sex:'nan'}
p = {}
Object.assign(p,p1,p2,p3)  //第一个参数是要合并的目标对象
console.log(p)  //Object {name: "zzz", age: 13, sex: "nan"}
> ```