1. 添加DNS服务器
vi /etc/resolv.conf
在文件中添加如下两行（可以自己选择DNS服务器，这里选的是114的，包括谷歌的8.8.8.8和腾讯的119.29.29.29都可以）：
nameserver 114.114.114.114
nameserver 114.114.114.115

两行分别是首选DNS服务器和备选DNS服务器。 
:wq保存退出，直接就可以使用。 
如果还不好使，接着向下看。

2. 设置一个配置文件：
进入到/etc/sysconfig/network-scprits/打开ifcfg-ens33文件(这个文件名称不同的客户端可能会不同，我的是ens33，也有的是ens0或者是加上其他数字)

vi /etc/sysconfig/network-scprits/ifcfg-ens33
在文件中,找到 ONBOOT=NO 改成 ONBOOT=yes

:wq保存退出

重启网络：

service network restart
