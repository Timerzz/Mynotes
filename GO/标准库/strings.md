## 字符串分割
```go
	s := "A,B,c"
	parts:=strings.Split(s,",")  //按逗号进行分割
	for _,part:= range parts{
		t.Log(part)
	}
```

## 字符串拼接
```go
s := "A,B,c"
parts:=strings.Split(s,",")  //按逗号进行分割
for _,part:= range parts{
	t.Log(part)
}
t.Log(strings.Join(parts,"-"))
```