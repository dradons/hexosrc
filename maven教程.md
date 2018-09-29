---
title: maven教程
date: 2017-03-23 09:47:35
tags:
---
打算用maven搭建一个web的项目，由于前期对maven不了解，只是知道有这么个东西。下面开始讲述我在使用过程中遇到的问题
及解决方案

1 需要在Apache网站下载win版本的maven,是一个压缩包，解压后放到任意一个路径，我一般放在D:\tools\java\apache-maven-3.3.9,由于我是java开发的所以我就放在这里了
2 这一步就需要配置环境变量了，先配置一个 MAVEN_HOME=D:\tools\java\apache-maven-3.3.9 然后把MAVEN_HOME加入到path=$path\%MAVEN_HOME%\bin
3 从现在开始就可以cmd验证  mvn -version  如果打印出信息说明已经成功了
4 我是在IDE开发的，用的的eclipse,我自己的的eclipse自带的maven插件有问题，所以我就在网上找了个离线版的，加压后把plguin profiles 放到对应的目录下重启就可以了
5 开始我的maven插件有问题新建maven project总报错，为此我还改了 maven architecture 的索引文件，从网站下载了xml文件添加上

###eclipse maven webproject
1 通过eclipse创建一个maven webproject,eclipse中配置maven-installation中添加下载的maven
2 新建Maven Project,选择默认工作空间，在选择Architype中的过滤器中输入maven-archetype-webapp ，下一步添加maven 标准的数据配置
3 为了能直接发布到tomcat下，还需要吧maven项目转为eclipse的web项目，设置Project Facets,Deployment Assembly
4 web3.0需要jdk1.7,所以使用web2.5 修改项目所在目录的配置文件解决不能使用web 2.5的问题，修改E:\project\JPPN_SSM\.settings\org.eclipse.wst.common.project.facet.core.xml 中
 installed facet="jst.web" version="2.5"
5




###nexus responsit

1 启动方式 ./bin/nexus console
2 浏览器访问 http://localhost:8081/nexus  
3 默认用户名密码 adminand admin123
4 以服务方式启动 
``` bash
D:\tools\java\nexus\nexus-2.14.3-02\bin>nexus.bat install
wrapper  | nexus installed.
D:\tools\java\nexus\nexus-2.14.3-02\bin>nexus.bat start
wrapper  | Starting the nexus service...
wrapper  | Waiting to start...
wrapper  | Waiting to start...
wrapper  | Waiting to start...
wrapper  | Waiting to start...
wrapper  | Waiting to start...
wrapper  | Waiting to start...
wrapper  | nexus started.
 ```
 
### JWS

/Library/Java/JavaVirtualMachines/jdk1.7.0_80.jdk/Contents/Home 







