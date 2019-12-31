# runtime 
1. GOMAXPROCS
> 设置可以并行计算的CPU核数最大值
2. Goexit
> 使当前的goroutine的运行终止并在终止前先执行此goroutine还未执行的defer语句，而其他协程不受影响。注意不要在主函数调用Goexit，会引发panic。
3. NumCPU
> 查询CPU核数量