---
title: git安装
---
## git安装

由于我的Linux环境是Redhat6-64，在安装git过程中遇到了不少问题。

git不提供Redhat的快捷安装方式，所以按照官网的说法进行源码编译安装。

其实Redhat可以通过yum来安装git,不过版本较低时1.7，现在的git已经到了
2.9，所以选择了源码安装，由于git依赖的包较多，所以首先需要替换掉原来
系统自带的yum,顺便说一句为什么要替换掉，因为自带的yum是需要收费的。
下面来采用centos的yum来替换。

1 以为我的系统没有注册，允许yum会报错，如下；
This system is not registered with RHN.RHN support will be disabled.

2删掉系统自带的yum
rpm -qa|grep yum|xargs rpm -e --nodeps 
rpm是Linux安装包的一种命令  

3 根据系统的版本到http://mirrors.163.com/centos/ 找对应系统版本号，我用的是6

4由于我的系统是64为的，我在此地址下载了3个RPM，http://mirrors.163.com/centos/6/os/x86_64/Packages/
yum-3.2.29-73.el6.centos.noarch.rpm  
yum-metadata-parser-1.1.2-16.el6.x86_64.rpm 
yum-plugin-fastestmirror-1.1.30-37.el6.noarch.rpm

5 下载方式可通过
``` bash
 wget http://mirrors.163.com/centos/6/os/x86_64/Packages/yum-3.2.29-73.el6.centos.noarch.rpm
 ```
下载到当前文件夹

6然后执行安装，由于三个包是互相有依赖，所以我选择了一起安装
``` bash
rpm -ivh yum-*
```
在我安装的过程有又出现了，python-urlgrabber-3.9.1-11.el6.noarch.rpm  
包缺少的问题所以我就又在http://mirrors.163.com/centos/6/os/x86_64/Packages/下载包
同样通过wget方式下载到当前目录执行安装 
``` bash
rpm -ivh python-urlgrabber-3.9.1-11.el6.noarch.rpm
```
在解决此问题的过程中我以为是python没有安装，所以从python官网下载了源码包进行解压安装了一把，走了弯路
python安装过程大致为，解压包 
''' bash 
tar xvf  Python-3.6.1rc1.tgz
'''     创建安装目录 mkdir /usr/local/python36    安装（进入到解压后的目录）./configure --prefix=/usr/local/python36
make   makeinstall
然后又改了python的指向 ln -s  /usr/local/python36/bin/python3.6 /usr/bin/python   然后就可以在命令行查看python版本了  python --version
安装完成后问题依然没解决（徒劳了）最终是通过上面安装rpm解决了，
7 呵呵，终于安上yum,安装完成后还需要配一下yum的库即资源下载源
a，进入存资源配置的文件夹  cd /etc/yum.repos.d
b，由于我的源cenos首先下载，所以不需要备份，如果更新源就需要备份了 mv ./CentOS-Base.repo ./CentOS-Base.repo.bak
c,使用wget下载163的源 http://mirrors.163.com/.help/centos.html       wget http://mirrors.163.com/.help/CentOS6-Base-163.repo
d，把下载下来的文件CentOS-Base-163.repo设置为默认源           mv CentOS6-Base-163.repo CentOS-Base.repo
e, 打开文件CentOS-Base.repo，把里面$resolver 全部替换为6（即系统版本）  我通过vi来操作的命令     :1$/$resolver/6/a
8 源更改后运行  yum makecache生成缓存，呵呵有报错了统默认python版本后yum不可用的问题  vi /usr/bin/yum 将文件头的1  #!/usr/bin/python替换为#!/usr/bin/python2.6
9 然后  yum makecache  ，到此yum算是完成了，开始安装git吧


10，保险起见先安装yum install curl-devel expat-devel gettext-devel \ openssl-devel zlib-devel 


先解压  tar -zxf git-2.9.3.tar.gz 
进入目录 cd git-2.9.3
新建安装目录  mkdir /usr/local/git
编译路径  ./configure --prefix=/usr/local/git
编译 make     有报错了
zlib.h: No such file or directory    yum install zlib-devel 
Can't locate ExtUtils/MakeMaker.pm  yum install perl-ExtUtils-CBuilder perl-ExtUtils-MakeMaker
安装  make install

11 安装成加入环境变量  在 /ect/profile最后加上  export PATH=/usr/local/git/bin/:$PATH
source /etc/profile  立即生效，git安装成功了



##搭建git服务器

1 新建一个git用户组，新建用户git把用户加到git组
groupadd git    useradd git -g git 
2 在/home/git建立一个资源库
cd /home/git   mkdir repo.git   cd repo.git     git init --bare #生成裸仓库
3 给仓库授权用户
chown -R git:git /home/git/repo.git

###git客户端生成秘钥
ssh-keygen -t rsa -C "yangyufa@jetsen.cn"，秘钥的过程中 yes 回车 回车
秘钥会生成到.ssh所在的目录，原则上需要把，公钥放到服务器上，ssh连接就不需要密码了

秘钥放到服务器的具体哪个位置呢，放到登录用户的.ssh目录下，如果没有该目录手动创建
/home/git/.ssh/authorized_keys  authorized_keys中就存放了，所以连接该机器的人的公钥放在里面

还需要修改ssh的配置文件允许，证书登录vi /etc/ssh/sshd.config
RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile      .ssh/authorized_keys

重启一下 /etc/init.d/sshd stop  /etc/init.d/sshd start


###克隆库

1 克隆
git clone git@192.168.137.131:/home/git/repo.git
报错：git-upload-pack: command not found
原因git安装路径是/usr/local/git，不是默认路径 
ln -s /usr/local/git/bin/git-upload-pack /usr/bin/git-upload-pack  


2 新建文件 cd repo
cat readme
3 更新索引
git  add reame
4 提交本地库
git commit -m "readme"
6 推到远程
git push origin master
报错 bash: git-receive-pack: command not found
ln -s /usr/local/git/bin/git-receive-pack /usr/bin/git-receive-pack

绕来绕去还是通过官方的文档，成功
https://git-scm.com/book/it/v2/Git-on-the-Server-Setting-Up-the-Server
如果我按下面的文章安装git估计问题少很多
https://tecadmin.net/install-git-2-x-on-centos-rhel-and-fedora/#

#hexo  /d/hexo/gitblog/dradons.github.io  /d/hexo/public
### 拷贝到git库目录
``` bash
cp -R /d/hexo/public/* /d/hexo/gitblog/dradons.github.io
cd /d/hexo/gitblog/dradons.github.io
git add .
git commit -m “update”
git push origin master
 ```




cd /d/tools/hexo/jetsen
hexo new [layout] <title>



$  git status


$ hexo n == hexo new
$ hexo g == hexo generate
$ hexo s == hexo server
$ hexo d == hexo deploy


git rm -r -n --cached  *
git rm -r --cached *
git commit -m"移除src目录下所有文件的版本控制"
git push origin master







  


