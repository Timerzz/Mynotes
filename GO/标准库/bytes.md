## bytes
> bytes包实现了操作[]byte的常用函数

## Variables
```go
var ErrTooLarge = errors.New("bytes.Buffer: too large")
```

## Function

#### 1. Compare(a, b []byte) int
> 比较两个[]byte按字典序比较，a==b返回0， a<b返回-1.
```go
func TestCompare(t *testing.T) {
	a := []byte{'1','2','3'}
	//b := []byte{'1','2','3'}
	c := []byte{'1','2','4'}
	ret := bytes.Compare(a,c)
	t.Log(ret)
}
```

#### 2. Equal(a, b []byte) bool
> 比较两个byte切片内容是否相同
```go
func TestEqual(t *testing.T){
	a := []byte{'1','2','3'}
	//b := []byte{'1','2','3'}
	c := []byte{'1','2','4'}
	ret := bytes.Equal(a,c)
	t.Log(ret)
}
```

#### 3. Runes(s []byte) []rune
> 返回和s等价的[]rune切片
```go
func TestRunes(t *testing.T){
	a := []byte{'1','2','3'}
	ret := bytes.Runes(a)
	t.Log(ret)
}
```
- 该函数的源码：
```go
func Runes(s []byte) []rune {
	t := make([]rune, utf8.RuneCount(s))
	i := 0
	for len(s) > 0 {
		r, l := utf8.DecodeRune(s)    //编码s中第一个字符，返回编码后的字符和 s 中被解码的字节数
		t[i] = r
		i++
		s = s[l:]
	}
	return t
}
```
#### 4. HasPrefix(s, prefix []byte) bool
> 判断s是否有前缀切片prefix。
```go
func TestHasPrefix(t *testing.T){
	a := []byte{'1','2','3'}
	b :=[]byte{'1'}
	ret := bytes.HasPrefix(a,b)
	t.Log(ret)
}
```
- 该函数源码：
```go
func HasPrefix(s, prefix []byte) bool {
	return len(s) >= len(prefix) && Equal(s[0:len(prefix)], prefix)
}
```
#### 5. HasSuffix(s, suffix []byte) bool
> 与上面类似，判断s是否有后缀切片suffix。
#### 6. Contains(b, subslice []byte) bool
> 判断切片b是否包含子切片subslice。
```go
func TestContains(t *testing.T){
	a := []byte{'1','2','3'}
	b :=[]byte{'4'}
	ret := bytes.Contains(a,b)
	t.Log(ret)
}
```
- 该函数的源码：
```go
func Contains(b, subslice []byte) bool {
	return Index(b, subslice) != -1
}
//就是调用Index函数。。。
```

#### 7. Count(s, sep []byte) int
> 计算s中有多少个不重叠的sep子切片
```go
func TestCount(t *testing.T){
	a := []byte{'1','2','3','2'}
	b :=[]byte{'2'}
	ret := bytes.Count(a,b)
	t.Log(ret)
}
```
- 该函数源码：
```go
func Count(s, sep []byte) int {
	// special case
	if len(sep) == 0 {
		return utf8.RuneCount(s) + 1
	}
	if len(sep) == 1 {
		return bytealg.Count(s, sep[0])
	}
	n := 0
	for {
		i := Index(s, sep)
		if i == -1 {
			return n
		}
		n++
		s = s[i+len(sep):]
	}
}
//在sep为空的情况下，会调用utf8.RuneCount(s)，也就是说sep为空的时候，返回的是s的UTF-8编码字符个数+1。关于这两种编码区别，可以搜索Rune和byte类型的区别。简单来说Rune实现类型是int32对应UTF-8，而byte实现类型是int8，对应acsii
//sep长度为1，调用bytealg.Count。bytealg似乎涉及在不同硬件下的实现，看不到源码。
//剩余情况就用Index函数搜索，并不断缩减s
```





