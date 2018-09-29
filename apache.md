---
title: apache
date: 2018-03-23 10:03:55
tags:
---

[How To Install the Apache Web Server on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-install-the-apache-web-server-on-ubuntu-16-04)

### Step 1: Install Apache
``` bash
sudo apt-get update
sudo apt-get install apache2
```
### Step 2: Check your Web Server
``` bash
sudo systemctl status apache2
```
### file dictory
/var/www/html