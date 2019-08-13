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

#### 8.Index(s, sep []byte) int
> 子切片sep在s中第一次出现的位置，不存在则返回-1。
```go
func TestIndex(t *testing.T){
	a := []byte{'1','2','3','2'}
	b :=[]byte{'2','3'}
	ret := bytes.Index(a,b)
	t.Log(ret)
}
```
- 该函数源码
```go
func Index(s, sep []byte) int {
	n := len(sep)
	switch {
	case n == 0:
		return 0
	case n == 1:
		return IndexByte(s, sep[0])
	case n == len(s):
		if Equal(sep, s) {
			return 0
		}
		return -1
	case n > len(s):
		return -1
	case n <= bytealg.MaxLen:
		// Use brute force when s and sep both are small
		if len(s) <= bytealg.MaxBruteForce {
			return bytealg.Index(s, sep)
		}
		c0 := sep[0]
		c1 := sep[1]
		i := 0
		t := len(s) - n + 1
		fails := 0
		for i < t {
			if s[i] != c0 {
				// IndexByte is faster than bytealg.Index, so use it as long as
				// we're not getting lots of false positives.
				o := IndexByte(s[i:t], c0)
				if o < 0 {
					return -1
				}
				i += o
			}
			if s[i+1] == c1 && Equal(s[i:i+n], sep) {
				return i
			}
			fails++
			i++
			// Switch to bytealg.Index when IndexByte produces too many false positives.
			if fails > bytealg.Cutover(i) {
				r := bytealg.Index(s[i:], sep)
				if r >= 0 {
					return r + i
				}
				return -1
			}
		}
		return -1
	}
	c0 := sep[0]
	c1 := sep[1]
	i := 0
	fails := 0
	t := len(s) - n + 1
	for i < t {
		if s[i] != c0 {
			o := IndexByte(s[i:t], c0)
			if o < 0 {
				break
			}
			i += o
		}
		if s[i+1] == c1 && Equal(s[i:i+n], sep) {
			return i
		}
		i++
		fails++
		if fails >= 4+i>>4 && i < t {
			// Give up on IndexByte, it isn't skipping ahead
			// far enough to be better than Rabin-Karp.
			// Experiments (using IndexPeriodic) suggest
			// the cutover is about 16 byte skips.
			// TODO: if large prefixes of sep are matching
			// we should cutover at even larger average skips,
			// because Equal becomes that much more expensive.
			// This code does not take that effect into account.
			j := indexRabinKarp(s[i:], sep)
			if j < 0 {
				return -1
			}
			return i + j
		}
	}
	return -1
}
```

#### 9.IndexByte(s []byte, c byte) int
> 字符c在s中第一次出现的位置，不存在则返回-1。
```go
func TestIndexByte(t *testing.T){
	a := []byte{'1','2','3','2'}
	b := byte('2')
	ret := bytes.IndexByte(a,b)
	t.Log(ret)
}
```
#### 10.IndexRune(s []byte, r rune) int
> unicode字符r的utf-8编码在s中第一次出现的位置，不存在则返回-1
```go
func TestIndexRune(t *testing.T){
	a := []byte{'1','2','3','2'}
	b := '2'
	ret := bytes.IndexRune(a,b)
	t.Log(ret)
}
```

#### 11.IndexFunc(s []byte, f func(r rune) bool) int
>s中第一个满足函数f的位置i（该处的utf-8码值r满足f(r)==true），不存在则返回-1
>

#### 12. LastIndex(s, sep []byte) int
>切片sep在字符串s中最后一次出现的位置，不存在则返回-1
>


#### 13.ToLower(s []byte) []byte
> 返回将所有字母都转为对应的小写版本的拷贝
```go
func TestToLower(t *testing.T){
	a := []byte{'a','B','C','E'}
	b :=bytes.ToLower(a)
	for _,v :=range b{
		t.Log(string(v))
	}
}  
//a,b,c,e
```
#### 14.Split(s, sep []byte) [][]byte
> 用去掉s中出现的sep的方式进行分割，会分割到结尾，并返回生成的所有[]byte切片组成的切片
```go
func TestSlipt(t *testing.T){
	a := []byte{'a','b','a','d'}
	b :=[]byte{'a'}
	ret := bytes.Split(a,b)
	t.Log(ret)
}  //返回值：[[] [98] [100]]
```






