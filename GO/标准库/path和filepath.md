# path
1. path.Base
> 返回路径的最后一个元素



## filepath
1. filepath.Abs
> 返回所给路径的绝对路径
```go
path, _ := filepath.Abs("./1.txt");
```

2. filepath.Glob
> 返回所有匹配的文件
```go
match, _ := filepath.Glob("./*.go");
fmt.Println(match);
```