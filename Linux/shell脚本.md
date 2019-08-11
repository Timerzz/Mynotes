# Shell脚本
1.	通常以.sh结尾
2.	常用Bash shell，c shell
3.	文件开头指定使用哪种shell
	#!/bin/bash
4.	要给shell赋予执行权限
	Chmod  755  test.sh
5.	执行shell
	Sh  test.sh
6.	Shell定义变量
	name = “Ass we can”
7.	调用变量
	echo $name   打印 Ass wecan
	如果echo name那么直接打印name
	变量名外面的花括号是可选的，加不加都行，加花括号是为了帮助解释器识别变量的边界，比如下面这种情况：
	```shell
	for skill in Ada Coffe Action Java; do
    echo "I am good at ${skill}Script"
	done
	```
8.	$? $0 $1 $2 $3… 代表什么意思
	$0: 代表执行shell名
	$1: 代表执行shell脚本后面，携带的第1参数
	$2: 代表执行shell脚本后面，携带的第2参数
	$?: 代表前一个命令是否执行成功，成功为0
9.	Shell条件判断
	if [[ $? = 0 ]];then
			echo “Success”
	else
			echo “Error”
	fi
10.	Shell字符颜色显示
		#字符颜色显示
	#-e:允许echo使用转义
	#\033[:开始位
	#\033[0m:结束位
	echo -e "\033[30m黑色字\033[0m"  
	echo -e "\033[31m红色字\033[0m"  
	echo -e "\033[32m绿色字\033[0m"  
	echo -e "\033[33m黄色字\033[0m"  
	echo -e "\033[34m蓝色字\033[0m"  
	echo -e "\033[35m紫色字\033[0m"  
	echo -e "\033[36m天蓝字\033[0m"  
	echo -e "\033[37m白色字\033[0m"  
11. 循环
两种：1.for循环 2. for   in
```shell
for i in $1; do
	echo $i
done
```
```shell
for((j=0;j<$2;j++));do
	echo $3
done
```

12. 获取时间与显示
```shell
echo $(date +%Y年%m月%d日%H时%M分%S秒)
echo $(date)
```

