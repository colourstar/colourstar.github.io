---
layout: post
title: 配置 shadowsocks的总结
---


## 一：选定vps商
  近期banwagon的付费到期了，想试试其他的VPS如何，选用了vultr,架设了一台机房在日本的服务器。
用speedtest测试，速度达到了惊人的6Mps,惊喜的不得了。但是实际应用发现，速度貌似并没有那么快，可能访问的环境多数都是在美国，日本的服务器还要绕一圈到老美去的缘故把。。。
  先去https://www.vultr.com/去租一台服务器，价格还是非常便宜的，1000G流量，15G，768RAM，才5美金/month

## 二：配置服务器
  一般的vps提供商都会提供几种不同类型的linux操作系统，vultr居然都提供了windowsserver，略微惊讶。
其中有一点需要注意一下，如果选择centOS来架设shadowsocks,可能会遇到防火墙的问题，昨天纠结了一段时间，ping是没问题的，就是shadowsocks访问不成功，最后发现是防火墙问题。
后来果断换成ubuntu

首先在服务器上安装软件 


Debian / Ubuntu:
```
apt-get install python-pip
pip install shadowsocks
```

或者
```
apt install shadowsocks
```

CentOS:

```
yum install python-setuptools && easy_install pip
pip install shadowsocks
```

然后配置shadowsocks的配置文件，目录在/etc/shadowsocks.json  


```
vi /etc/shadowsocks.json 
{ 
    "server":"my_server_ip", 
    "server_port":8388, 
    "local_address": "127.0.0.1", 
    "local_port":1080, 
    "password":"mypassword", 
    "timeout":300, 
    "method":"aes-256-cfb", 
    "fast_open": false 
} 
```

### 后台运行shadowsocks
```
ssserver -c /etc/shadowsocks.json -d start
```

## 三：客户端配置
下载shadowsocks,将客户端的配置配置完毕，代理方式选择PAC即可

![shadowsocksclient](/images/shadowsocksclient.png)

## 四：愉快的上网
balabalaxxoo