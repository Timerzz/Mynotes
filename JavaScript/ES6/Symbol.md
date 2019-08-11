## symbol

ES6之后对象属性除了字符串，还可以是Symbol


## Symbol和字符串的区别
Symbol描述出来的都是独一无二的，不回冲突

```js
let s1 = Symbol("张")
let s2 = Symbol("张")
console.log(s1 === s2)   //false
```