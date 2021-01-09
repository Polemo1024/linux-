# linux设置代理

本文主要对kali、ubuntu设置proxychains和ssr

1.修改linux系统的软件源为国内源

参考：阿里源、中山大学源、清华大学源等

2.更新软件源，更新软件

sudo apt-get update

sudo apt-get upgrade

3.安装proxychains、python

sudo apt-get install proxychains

sudo apt-get install python

sudo apt-get install python3

4.配置 proxychains

vim /etc/proxychains.conf

将dynamic_chain前面的注释去掉，再将[ProxyList]下的socks4 改为socks5，并且127.0.0.1后面的端口改为1080

