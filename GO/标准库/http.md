# http


## server
> 通过Server结构,可以对服务器进行详细的配置
```go
	server := http.Server{
		Addr:              "0.0.0.0:8080",
		Handler:           nil,
		TLSConfig:         nil,
		ReadTimeout:       0,
		ReadHeaderTimeout: 0,
		WriteTimeout:      0,
		IdleTimeout:       0,
		MaxHeaderBytes:    0,
		TLSNextProto:      nil,
		ConnState:         nil,
		ErrorLog:          nil,
	}
	server.ListenAndServe()
```
以上这种写法和下面这种是类似的, 因为实际上调用的是同一个函数
```go
func main(){
	http.ListenAndServe("0.0.0.0:8080",nil)
}
```

## http.Handle
> http.Handle实际上调用了默认的DefaultServerMux的Handle方法

## http.HandleFunc
> 这个函数实际上调用了DefaultServerMux的HandleFunc函数. 而HandleFunc这个函数,实际上是将处理器函数类型转化为处理器
http.HandleFunc源码:
```go
func HandleFunc(pattern string, handler func(ResponseWriter, *Request)) {
	DefaultServeMux.HandleFunc(pattern, handler)
}
```
HandleFunc函数源码:
```go
func (mux *ServeMux) HandleFunc(pattern string, handler func(ResponseWriter, *Request)) {
	if handler == nil {
		panic("http: nil handler")
	}
	mux.Handle(pattern, HandlerFunc(handler))
}
```

## http.ServeMux
> ServeMux是一个HTTP请求多路复用器. 接收/HTTP请求并重定向到正确的处理器.
> ServeMux内部通过一个map实现映射.
```go
type ServeMux struct {
	mu    sync.RWMutex
	m     map[string]muxEntry
	es    []muxEntry // slice of entries sorted from longest to shortest.
	hosts bool       // whether any patterns contain hostnames
}
```
> ServeMux结构也实现了ServeHTTP方法,所以也是一个处理器
> DefaultServerMux是ServeMux的一个实例i



