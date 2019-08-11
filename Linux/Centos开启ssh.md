1、  首先，要确保CentOS7安装了  openssh-server，在终端中输入  yum list installed | grep openssh-server
![img](https://img-blog.csdn.net/20161008123201530?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)
此处显示已经安装了  openssh-server，如果又没任何输出显示表示没有安装  openssh-server，通过输入  yum install openssh-server

来进行安装openssh-server

 

2、  找到了  /etc/ssh/  目录下的sshd服务配置文件 sshd_config，用Vim编辑器打开

将文件中，关于监听端口、监听地址前的 # 号去除

![img](https://img-blog.csdn.net/20161008123807764?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

然后开启允许远程登录

![img](https://img-blog.csdn.net/20161008123926358?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

最后，开启使用用户名密码来作为连接验证

![img](https://img-blog.csdn.net/20161008124037166?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

保存文件，退出

 

3、  开启  sshd  服务，输入 sudo service sshd start

![img](https://img-blog.csdn.net/20161008124204950?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

检查  sshd  服务是否已经开启，输入ps -e | grep sshd

![img](https://img-blog.csdn.net/20161008124257998?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

或者输入netstat -an | grep 22  检查  22 号端口是否开启监听

![img](https://img-blog.csdn.net/20161008124408719?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)