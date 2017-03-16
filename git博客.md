---
title: git博客
date: 2017-03-16 22:16:07
tags:
---
#### hexo操作
1. 新建文件
 ``` $ hexo new [layout] <title>  ``` 
2. 通过notepad++ 编写
3. 生成静态文件，默认生成到public文件夹
``` $ hexo generate  ```
#### 拷贝到git库目录

下面的操作把生成的静态文件上传到github服务器的过程
``` bash
cp -R /d/hexo/public/* /d/hexo/gitblog/dradons.github.io
cd /d/hexo/gitblog/dradons.github.io
git add .
git commit -m “update”
git push origin master
```
