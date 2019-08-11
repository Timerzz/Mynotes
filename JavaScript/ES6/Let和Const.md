- 除了var，在ES6中，还有let与const

## let也是用来声明变量
1. let对作用域更为严格，var除了在函数中，都是全局变量
包括{}大括号中的代码块，但是let对作用域比较严格，在代码块中
也是局部变量
```js
{
var name1='张三';
console.log(name1);

let name2='李四';
console.log(name2);

}
console.log(name2);
```
会报错找不到name2


2. let的作用域不会提升
用var声明的变量会在作用域中寻找，找到后会将声明提前
```js
{
console.log(name1);
var name1 = '张三';
}
```
> 结果为undefined。因为声明提前了

```js
{
console.log(name1);
let name1 = '张三';
}
```
> 结果报错，因为声明不会提前

3. let在同一作用域下不能声明同名变量
```js
{
	var name='1';
	var name='2';
	console.log(name);
}
```
> 结果为2
```js
{
	let name='1';
	let name='2';
	console.log(name);
}
```
> 结果报错

4. let父子作用域不同
- 网页上有5个button
```js
var btns=document.getElementsByTagName("button");
	for(var i=0;i<btns.length;i++){
		btns[i].onclick=function(){
			alert(i);
		}
	}
```
这样点击每个button，出来的都是5，因为点击是一个异步的过程，而执行是同步的。var在这里声明的i是全局变量，是一直存在的，，而且最后就是5，所以触发事件后，先去找i是否存在，存在，所以输出5.
之前的解决方法是，用闭包
```js
for(var i=0;i<btns.length;i++){
		(function(t){
			btns[t].onclick=function(){
				alert(t);
			}
		})(i);
	}
```
但是用let就会对作用域严格的区分
```js
	var btns=document.getElementsByTagName("button");
	for(let i = 0;i<btns.length;i++){
		btns[i].onclick=function(){
			alert(i);
		}
	}
```
用let可以实现
 
## const 用来声明常量