1. 查看所有shell
```shell
cat /etc/shells
```

2. 修改shell
chsh -s 后面加路径 ： 设置当前用户默认shell
```shell
chsh -s /bin/zsh
```
3. 查看当前shell
```shell
echo $SHELL
```