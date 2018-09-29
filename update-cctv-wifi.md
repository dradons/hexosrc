---
title: update_cctv_wifi
date: 2018-03-23 11:16:43
tags:
---
1 stop UAC(本地安全策略-安全设置-本地策略-安装选项-用户账号控制：以管理员标准模式运行所有管理员)
2 拷贝并安装除xamp(重启机器)
3 变更mysql密码
``` bash
  c:\xampp\mysql\bin\mysqladmin -r root -p password
  Enter password:
  New password: srun_3000
  Confirm new password: srun_3000
  ```
4 通过Nvaicat for MySQL 工具新建数据库ipt_yangshi
5 导入数据库脚本ipt_yangshi.sql
6 拷贝两个dll文件到c:\xampp\php\ext
7 拷贝php.ini文件到c:\xampp\php
