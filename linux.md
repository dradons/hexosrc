---
title: linux
date: 2018-01-26 14:40:22
tags:
---
### apt-get下载文件目录
apt-get下载文件目录默认在/var/cache/apt/archives。
如果apt-get install 下载慢， 而网络下载deb快，可以把下载的deb文件放到该目录。
再执行安装就不下载直接安装了

###  [pip](http://www.ttlsa.com/python/how-to-install-and-use-pip-ttlsa/)
### [Ubuntu下apt-get安装与pip安装的区别](http://blog.csdn.net/rona_lin/article/details/45028277)


## [shadowsocks 服务器安装](https://linghucong.js.org/2016/04/20/setup-Shadowsocks-on-ubuntu-1604/)
### 更新软件源
sudo apt-get update
### 然后安装 PIP 环境
sudo apt-get install python-pip
### 直接安装 shadowsocks
sudo pip install shadowsocks

## 运行 shadowsocks 服务器
### 启动命令如下：如果要停止运行，将命令中的start改成stop。
sudo ssserver -p 8388 -k password -m rc4-md5 -d start
### 也可以使用配置文件进行配置，方法创建/etc/shadowsocks.json文件，填入如下内容：
{
    "server":"my_server_ip",
    "server_port":8388,
    "local_address": "127.0.0.1",
    "local_port":1080,
    "password":"mypassword",
    "timeout":300,
    "method":"rc4-md5"
}

### 创建完毕后，赋予文件权限
sudo chmod 755 /etc/shadowsocks.json
### 为了支持这些加密方式，你要需要安装
sudo apt–get install python–m2crypto
### 然后使用配置文件在后台运行
sudo ssserver -c /etc/shadowsocks.json -d start

## 配置开机自启动
### 编辑 /etc/rc.local 文件
sudo vi /etc/rc.local
### 在 exit 0 这一行的上边加入如下
/usr/local/bin/ssserver –c /etc/shadowsocks.json
### 或者 不用配置文件 直接加入命令启动如下
/usr/local/bin/ssserver -p 8388 -k password -m aes-256-cfb -d start


## ubuntu安装界面，基于GNOME
二、安装
1、首先，ubuntu server版本的安装这里就不再赘述，基本的还是三个步骤，首先是下载镜像，然后使用ultraISO刻录至u盘，最后通过U盘引导进行安装。安装过程中，会要求你输入用户名和密码，一定要牢记，因为后续软件的安装都需要密码。
2、然后，login进入系统之后，开始进行用户界面的安装。首先输入如下命令：
sudo apt-get install xinit
3、上述安装完毕之后，再安装环境管理器。本人亲测安装的是GNOME。使用如下命令安装：
sudo apt-get install gdm
4、然后，安装桌面环境。本人亲测安装的是KUbuntu。安装命令如下：
sudo apt-get install kubuntu-desktop
5、网上有人还说要安装一些必要的包，如新立得软件包管理器，中文支持等，如果你嫌麻烦，可以不进行安装。上述安装完毕之后，直接重启。重启完成后，再进入系统，便是图形界面了