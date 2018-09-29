---
title: rabbitmq
date: 2017-09-25 10:22:41
tags:

---

### get start
[Installing on Generic Unix](http://www.rabbitmq.com/install-generic-unix.html)
rabbitmq使用erlang语言编写，所以在安装rabbitmq前要安装erlang
1由于对erlang不太熟悉，使用rpm包安装,我的虚拟机是redhat6 64位
从网站下载[erlang](https://github.com/rabbitmq/erlang-rpm/releases)最新版，然后通过scp拷贝到虚拟机

拷贝安装包
``` bash
$ scp /c/Users/lenovo/Downloads/erlang-20.0.5-1.el6.x86_64.rpm root@192.168.137.131:/usr/local/rabbitmqinaction
```
执行安装
``` bash
$ rpm --insall erlang-20.0.5-1.el6.x86_64.rpm
```
解压rabbitmq
```bash
 tar -xvf rabbitmq-server-generic-unix-3.6.12.tar.xz
```
安装rabbitmq WEB管理
```bash
[root@bogon rabbitmqinaction]# cd rabbitmq_server-3.6.12/sbin
[root@bogon sbin]# ./rabbitmq-plugins enable rabbitmq_management
The following plugins have been enabled:
  amqp_client
  cowlib
  cowboy
  rabbitmq_web_dispatch
  rabbitmq_management_agent
  rabbitmq_management

Applying plugin configuration to rabbit@bogon... failed.
 * Could not contact node rabbit@bogon.
   Changes will take effect at broker restart.
 * Options: --online  - fail if broker cannot be contacted.
            --offline - do not try to contact broker.

```
由于域名的先关问题，造成管理启动不成功，我们关闭防火墙就可以了，root权限
暂时关闭，立即生效
```bash
 service iptables stop  
```
永久关闭，重启生效
```bash
chkconfig iptables off 
```

启动rabbitmq
```bash
[root@bogon sbin]# ./rabbitmq-server -detached
Warning: PID file not written; -detached was passed.
```

通过rabbitmqctl 查看服务状态

```bash
[root@bogon sbin]# ./rabbitmqctl status
Status of node rabbit@bogon
[{pid,6959},
 {running_applications,
     [{rabbitmq_management,"RabbitMQ Management Console","3.6.12"},
      {rabbitmq_management_agent,"RabbitMQ Management Agent","3.6.12"},
      {rabbitmq_web_dispatch,"RabbitMQ Web Dispatcher","3.6.12"},
      {rabbit,"RabbitMQ","3.6.12"},
      {mnesia,"MNESIA  CXC 138 12","4.15"},
      {amqp_client,"RabbitMQ AMQP Client","3.6.12"},
      {rabbit_common,
          "Modules shared by rabbitmq-server and rabbitmq-erlang-client",
          "3.6.12"},
      {cowboy,"Small, fast, modular HTTP server.","1.0.4"},
      {ranch,"Socket acceptor pool for TCP protocols.","1.3.0"},
      {ssl,"Erlang/OTP SSL application","8.2"},
      {public_key,"Public key infrastructure","1.4.1"},
      {asn1,"The Erlang ASN1 compiler version 5.0.2","5.0.2"},
      {inets,"INETS  CXC 138 49","6.4.1"},
      {cowlib,"Support library for manipulating Web protocols.","1.0.2"},
      {os_mon,"CPO  CXC 138 46","2.4.2"},
      {compiler,"ERTS  CXC 138 10","7.1.1"},
      {crypto,"CRYPTO","4.0"},
      {xmerl,"XML parser","1.3.15"},
      {syntax_tools,"Syntax tools","2.1.2"},
      {sasl,"SASL  CXC 138 11","3.0.4"},
      {stdlib,"ERTS  CXC 138 10","3.4.1"},
      {kernel,"ERTS  CXC 138 10","5.3.1"}]},
 {os,{unix,linux}},
 {erlang_version,
     "Erlang/OTP 20 [erts-9.0.5] [source] [64-bit] [smp:2:2] [ds:2:2:10] [async-threads:64] [hipe] [kernel-poll:true]\n"},
 {memory,
     [{connection_readers,0},
      {connection_writers,0},
      {connection_channels,0},
      {connection_other,2840},
      {queue_procs,2840},
      {queue_slave_procs,0},
      {plugins,720880},
      {other_proc,22257680},
      {metrics,193776},
      {mgmt_db,149160},
      {mnesia,61840},
      {other_ets,2078720},
      {binary,63400},
      {msg_index,48152},
      {code,24761019},
      {atom,1041593},
      {other_system,21117300},
      {total,72499200}]},
 {alarms,[]},
 {listeners,[{clustering,25672,"::"},{amqp,5672,"::"},{http,15672,"::"}]},
 {vm_memory_calculation_strategy,rss},
 {vm_memory_high_watermark,0.4},
 {vm_memory_limit,784151347},
 {disk_free_limit,50000000},
 {disk_free,9104482304},
 {file_descriptors,
     [{total_limit,924},{total_used,2},{sockets_limit,829},{sockets_used,0}]},
 {processes,[{limit,1048576},{used,328}]},
 {run_queue,0},
 {uptime,407},
 {kernel,{net_ticktime,60}}]
```
优雅的停止MQ
```bash
[root@bogon sbin]# ./rabbitmqctl stop
Stopping and halting node rabbit@bogon
```


下载rabbitmq安装包

2rabbitmq采用源码安装


```bash

```