1. 当前时间 time.Now()
2. 计算用时
```go
start :=time.Now()
fmt.Print("time Spent:",time.Since(start).Seconds())
```
3. 等待
```go
time.Sleep(time.Second*1)
```

