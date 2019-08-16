# firstweb
> 一开始学习go的web搭建的时候，都会有一个小的例子,如下
```go
import (
	"fmt"
	"net/http"
)

func handle(writer http.ResponseWriter, request *http.Request){
	fmt.Fprint(writer, "Hello World")
}
func main(){
	http.HandleFunc("/", handle)
	if err:=http.ListenAndServe("127.0.0.1:8080",nil);err!=nil{
		fmt.Println(err)
	}
}
```
需要注意的是, ListenAndServe第一个参数一定要填写完整:地址加端口,我一开始的时候只写了端口号,程序始终运行不了.
ListenAndServe的第二个参数是多路复用器,如果传入的是nil那么就会用它默认的多路复用器

>通过python的requests发送请求，查看响应
```python
r = requests.get("http://127.0.0.1:8080")
r.text
//Hello World, %s!ttt'

In [8]: r = requests.post("http://127.0.0.1:8080/ttt")

In [9]: r.text
Out[9]: 'Hello World, %s!ttt'
```
对监听端口的post和get请求都是同一个返回值