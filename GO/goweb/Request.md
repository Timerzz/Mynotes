# Request结构
- Request结构主要由以下部分组成
```go
URL字段
Header字段
Body字段
Form字段,PostForm字段和MultipartForm字段
```

## Header
在go中的Header实际上是map实现的:
```go
type Header map[string][]string
```
所以一个Header类型的实例就是一个映射
```go
func handle(writer http.ResponseWriter, request *http.Request){
	h := request.Header
	fmt.Fprint(writer, h)
}
func main(){
	http.HandleFunc("/header", handle)
	if err:=http.ListenAndServe("127.0.0.1:8080",nil);err!=nil{
		fmt.Println(err)
	}
}
```
通过以下方法可以获得特定的首部
```go
h := request.Header["Accept-Encoding"]
h := request.Header.Get("Accept-Encoding")
```
第一种方法得到的是一个字符串切片, 而第二种方法返回的是字符串