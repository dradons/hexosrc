---
title: often
date: 2017-12-21 10:44:04
tags:
---
netstat -ano|findstr "8006"

exp pk2admin/password@orcl owner=pk2admin file=C:\Users\lenovo\Desktop\ppn_data2.dmp
imp test/password@orcl full=y file=C:\Users\lenovo\Desktop\ppn_data2.dmp


6222600910073994731

wspath   
/opt/IBM/WebSphere/AppServer/profiles/AppSrv01/logs/server1
/opt/IBM/WebSphere/AppServer/profiles/AppSrv01/installedApps/UE2-T-AppCell01

osoperator user create-group 76543 G2016Z08880001 G2016Z08880001

/opt/WebSphere/AppServer/profiles/Custom01/logs/A4K-app-02-server1   10.121.177.2
/opt/WebSphere/AppServer/profiles/Dmgr01/logs/dmgr    10.121.177.1

#############
https://10.122.6.1:9043/ibm/console/logon.jsp    admin admin
10.122.6.1
ZAQ!XSW@cde3vfr4
 ps -efl | grep WebS
 kill -9 123
/opt/IBM/WebSphere/AppServer/profiles/Dmgr01/bin/startManager.sh
/opt/IBM/WebSphere/AppServer/profiles/AppSrv01/bin/startNode.sh
/opt/IBM/WebSphere/AppServer/profiles/AppSrv01/bin/startServer.sh server1
/opt/IBM/WebSphere/AppServer/profiles/AppSrv01/logs/server1
/opt/IBM/WebSphere/AppServer/profiles/AppSrv01/installedApps/UE2-T-AppCell01
/opt/IBM/WebSphere/AppServer/profiles/AppSrv01/installedApps/UE2-T-AppCell01/PPN_TRANS_21_war.ear/PPN_TRANS_21.war/WEB-INF/classes/jetsennet/ppn/services/wfm
########ue2ws
vfr4cde3XSW@ZAQ!
vfr4cde3XSW@ZAQ!
/opt/IBM/WebSphere/AppServer/profiles/AppSrv01/logs/UE2-App-01
/opt/IBM/WebSphere/AppServer/profiles/AppSrv01/logs/UE2-App-02

/opt/IBM/WebSphere/AppServer/profiles/AppSrv01/installedApps/UE2-App-01Cell01/jppn_ue2_20161201_war.ear/jppn_ue2_20161201.war



10.121.47.33  PK1-APP-01Node01-server1
/opt/WebSphere/AppServer/profiles/Custom01/logs/PK1-APP-01Node01-server1 
 
/opt/WebSphere/AppServer/profiles/Dmgr01/bin/startManager.sh
/opt/WebSphere/AppServer/profiles/Custom01/bin/startNode.sh
/opt/WebSphere/AppServer/profiles/Custom01/bin/startServer.sh PK1-APP-01Node01-server1

/opt/WebSphere/AppServer/profiles/Custom01/bin/stopNode.sh
/opt/WebSphere/AppServer/profiles/Dmgr01/bin/stopManager.sh



10.121.47.34  PK1-APP-02Node01-server1
/opt/WebSphere/AppServer/profiles/Custom01/logs/PK1-APP-02Node01-server1

/opt/WebSphere/AppServer/profiles/Custom01/bin/startNode.sh
/opt/WebSphere/AppServer/profiles/Custom01/bin/startServer.sh PK1-APP-02Node01-server1





---------------------
cd /opt/IBM/HTTPServer/Plugins/config/webserver1
vi plugin-cfg.xml 
<Uri AffinityCookie="JSESSIONID" AffinityURLIdentifier="jsessionid" Name="/PpnTrans/*"/>
/opt/IBM/HTTPServer/bin/apachectl start


----------banwagong vps------------------------------------
104.224.168.73  26781
root/sdm4QUFcgyAw
----------------------------------------------

protask_code 生成方式是ZJ_[book的主键]     15000731

sudo timedatectl set-timezone Asia/Shanghai
----------linux soap-----------------------------------------------------


curl -H 'Content-Type: text/xml;charset=UTF-8;SOAPAction:"importAllow"' -d @/home/jetsen/Desktop/1.xml http://192.168.137.1:8080/PPN_UE2/services/PK1_ImportAllowService


curl -H 'Content-Type: text/xml;charset=UTF-8;SOAPAction:"importAllow"' -d @/root/importallowtest/1.xml http://10.111.3.23/ESBGWWeb/sca/ESBExport


curl -H 'Content-Type: text/xml;charset=UTF-8;SOAPAction:"addImportTask"' -d @/root/importallowtest/nettasknew.xml http://10.111.3.23/ESBGWWeb/sca/ESBExport


curl -H 'Content-Type: text/xml;charset=UTF-8;SOAPAction:"publish"' -d @/root/importallowtest/pgm.xml http://10.111.3.23/ESBGWWeb/sca/ESBExport



keytool -genkey -keyalg RSA -alias yufa -keystore d:\etc\cas\thekeystore    (changeit)

-------------------cmd-----syntax----------------------------------------------------------------------
## change cmd to English
chcp 437
## Delete one or more files.
del /p *.log
## Delete folder(s)
Syntax
      RD pathname
      RD /S pathname
      RD /S /Q pathname
## Tasklist command

tasklist /fi "memusage gt 30000"

tasklist /fi "pid eq 6544"

tasklist /fi "imagename eq firefox.exe"

## taskkill 
taskkill /pid 15900
taskkill /fi "pid eq 15900"

##WHERE Locate and display files in a directory tree. 
where /t cas*.log


------------------------------------------
1.su oracle 

然后启动监听器

1.lsnrctl start 
会看到启动成功的界面;

1.lsnrctl stop 
停止监听器命令.


1.lsnrctl status 
查看监听器命令.



sudo apt-get update

sudo apt-get install python-pip

sudo pip install shadowsocks

sudo ssserver -p 8388 -k yangyufa -m aes-256-cfb -d start

------------angular js ---------
angular js 思维导图在github搜索TeamStuQ/skill-map

大漠孤烟 开源中国

https://my.oschina.net/mumu/blog/1519357

http://video.tudou.com/v/XMjUwMjYyNTA5Ng==.html?spm=a2hzp.8244740.0.0&f=29431430

--------------docker---------

docker run -d --name myrabbitmq -p 5673:5672 -p 15673:1567

docker run -p 6379:6379 -v $PWD/data:/data  -d --name myredis6379 redis redis-server --appendonly yes

docker exec -it myrabbitmq /bin/bash

docker inspect node1 | grep IPA

redis-cli -h 172.17.0.1 -p 26380 info Sentinel
------------------------------------redis slave----172.17.0.4------------------redis-cli -h 127.0.0.1 -p 6379 info replication------
docker run -d \
-p 6380:6380 \
-v /home/jetsen/conf/redis6380.conf:/etc/redis/redis6380.conf \
-v /home/jetsen/data:/data \
--name redis_node1 \
 redis \
redis-server /etc/redis/redis6380.conf
-----------------------------------redis slave -----172.17.0.5------------
docker run -d \
-p 6381:6381 \
-v /home/jetsen/conf/redis6381.conf:/etc/redis/redis6381.conf \
-v /home/jetsen/data:/data \
--name redis_node2 \
 redis \
redis-server /etc/redis/redis6381.conf
redis-sentinel-26380.conf
-------------------------------sentinel-------------172.17.0.7--------------redis-cli -h 127.0.0.1 -p 26379 info Sentinel-
docker run -d \
-p 26379:26379 \
-v /home/jetsen/conf/redis-sentinel-26379.conf:/etc/redis/redis-sentinel-26379.conf \
-v /home/jetsen/data:/data \
--name sentinel-26379 \
 redis \
redis-sentinel /etc/redis/redis-sentinel-26379.conf
-------------------------------sentinel----------172.17.0.6-------------------
docker run -d \
-p 26380:26380 \
-v /home/jetsen/conf/redis-sentinel-26380.conf:/etc/redis/redis-sentinel-26380.conf \
-v /home/jetsen/data:/data \
--name sentinel-26380 \
 redis \
redis-sentinel /etc/redis/redis-sentinel-26380.conf
-------------------------------sentinel----------172.17.0.8-------------------
docker run -d \
-p 26381:26381 \
-v /home/jetsen/conf/redis-sentinel-26381.conf:/etc/redis/redis-sentinel-26381.conf \
-v /home/jetsen/data:/data \
--name sentinel-26381 \
 redis \
redis-sentinel /etc/redis/redis-sentinel-26381.conf

----------------MySQL------------
sudo docker run --name first-mysql -p 3306:3306 -e MYSQL\_ROOT\_PASSWORD=123456 -d mysql

-----------------------zookeeper-----------------
docker run --name my_zookeeper -p 2181:2181 -d zookeeper

docker logs -f my_zookeeper

docker run -it --rm --link my_zookeeper:zookeeper zookeeper zkCli.sh -server zookeeper


# Maven
MAVEN_HOME=/usr/local/maven3.5.2
PATH=$PATH:$MAVEN_HOME/bin
MAVEN_OPTS="-Xms256m -Xmx356m"
export MAVEN_HOME
export PATH
export MAVEN_OPTS



