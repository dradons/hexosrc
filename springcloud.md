---
title: springcloud
date: 2017-09-28 10:14:18
tags:
---
##Spring Cloud Config
- config server(https://github.com/spring-cloud/spring-cloud-config)
--- Client Side Usage
---- 在maven的pom中配置
```bash
<dependency>
		<groupId>org.springframework.cloud</groupId>
		<artifactId>spring-cloud-starter-config</artifactId>
</dependency>
```
---- config的地址默认是http://localhost:8888,如需更在bootstrap.properties(bootstrap.yml)中配置
```bash
spring.cloud.config.uri: http://myconfigserver.com
```


```bash

```