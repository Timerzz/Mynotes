- 数字转字符串strconv.Itoa
```go
s:=strconv.Itoa(10)
	t.Log("str"+s)
```
- 字符串转数字
	- ！ 字符串转数字会传回两个值所以要先进行判断
```go
	if i,err:=strconv.Atoi("5");err==nil{
		t.Log(10+i)
	}
```