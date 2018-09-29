---
title: readme
date: 2018-01-25 16:23:24
tags:
---
git clone git@github.com:dradons/dradons.github.io.git  .deploy/dradons.github.io.git

cp -R /d/tools/hexo/jetsen/public/* /d/tools/hexo/jetsen/.deploy/dradons
cd /d/tools/hexo/jetsen/.deploy/dradons
git add .
git commit -m “update”
git push origin master





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


Host github.com
User jetsen02@163.com 
Hostname ssh.github.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/id_rsa
Port 443