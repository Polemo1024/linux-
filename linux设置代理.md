# linux设置代理

本文主要对kali、ubuntu设置proxychains和ssr

1.修改linux系统的软件源为国内源

参考：阿里源、中山大学源、清华大学源等

2.更新软件源，更新软件

sudo apt-get update & sudo apt-get upgrade

3.安装proxychains、python

sudo apt-get install proxychains

sudo apt-get install python

sudo apt-get install python3

4.配置 proxychains

vim /etc/proxychains.conf

将dynamic_chain前面的注释去掉，再将[ProxyList]下的socks4 改为socks5，并且127.0.0.1后面的端口改为1080

![image-20210109141057493](C:\Users\lemon\AppData\Roaming\Typora\typora-user-images\image-20210109141057493.png)

5.安装ssr

下载SSR脚本：

```
wget https://onlyless.github.io/ssr
sudo mv ssr /usr/local/bin
sudo chmod 766 /usr/local/bin/ssr
```

安装SSR：

```
ssr install
```

配置SSR：

```
ssr config
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
{
    "server": "0.0.0.0",   //服务器IP地址
    "server_ipv6": "::",
    "server_port": 2333,  //端口
    "local_address": "127.0.0.1", 
    "local_port": 1080,

    "password": "password",  //密码
    "method": "aes-256-cfb", //加密方式
    "protocol": "auth_aes128_md5", //协议
    "protocol_param": "",
    "obfs": "plain",  //混淆方式
    "obfs_param": "",
    "speed_limit_per_con": 0,
    "speed_limit_per_user": 0,

    "additional_ports" : {}, 
    "additional_ports_only" : false, 
    "timeout": 120,
    "udp_timeout": 60,
    "dns_ipv6": false,
    "connect_verbose_info": 0,
    "redirect": "",
    "fast_open": false
}
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

配置完之后保存，ssr就会自动启动，查看本地1080端口：

sudo lsof -i:1080

ssr的启动和关闭方式为：

```
ssr start
ssr stop
```

执行proxyresolv www.google.com报错找不到命令：

```
cp /usr/lib/proxychains3/proxyresolv /usr/bin/
```

执行proxychains curl https://ipinfo.io

![image-20210109142346701](C:\Users\lemon\AppData\Roaming\Typora\typora-user-images\image-20210109142346701.png)

