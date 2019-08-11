# a标签的伪类选择器
- **<font color=#0099ff>伪类选择器不光可以用在a标签，任何标签都可以，所以可以用来监听鼠标是否点击/悬停/长按一个标签</font>**
- 伪类选择器与伪元素选择器有点类似，但是并不相同

## a标签伪类选择器的作用
- a标签有四种状态
	1. 从未点过状态
	2. 已经点过的状态
	3. 鼠标长按的状态
	4. 鼠标悬停的状态
- a标签伪类选择器就是用来设置a标签在不同状态下的样式

- 格式
	- :link
	- ：visited
	- ：active 修改鼠标长按状态
	- ：hover 修改鼠标悬停状态的样式

```css

a:nth-of-type(1):link{
	color: red;
}
a:nth-of-type(1):visited{
	color: greenyellow;
}

a:nth-of-type(1):hover{
	color: blueviolet;
}
a:nth-of-type(1):active{
	color: blue;
}
```

## 注意点
- a标签伪类选择器一起出现的时候一定要按照一定的顺序
	- 先link
	- visited
	- hover
	- active

```css
ul:hover li{
            margin-left: 350px;
        }
```
以上：当鼠标悬停ul的时候，ul里面的li标签属性改变