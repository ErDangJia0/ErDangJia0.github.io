---
layout:     post
title:      远程连接mongodb和Mysql数据库时的问题
subtitle:   主要针对爬虫时出现“由于目标计算机积极拒绝，无法连接”的解决方法
date:       2017-10-26
author:     WHY
header-img: img/post-bg-universe.jpg
catalog: true
tags:
    - mysql
    - mongodb
    - 爬虫
    - 远程连接
---

# 1、配置修改
Mongodb：若要开放远程连接，在MongoDB的配置文件中将bindIp从127.0.0.1修改为0.0.0.0即可，MongoDB的配置文件的目录为/etc/mongod.conf。

Mysql：Mysql比较复杂，首先，cd /etc/mysql/mysql.conf.d，打开 mysqld.cnf文件，将[mysqld]下的bind-address = 127.0.0.1加#注释掉，然后/etc/init.d/mysql restart 重启mysql服务。
然后，添加授权用户，在mysql中：

mysql>grant all privileges on *.* to '用户名'@'%' identified by ‘密码' with grant option;

mysql>mysql>flush privileges;

注意，root用户不得作为远程访问的用户名。

# 2、防火墙设置
Ubuntu中同样存在防火墙，下面介绍几个防火墙的命令：

1、查看状态 ：sudo ufw status

2、打开     ：sudo ufw enable

3、关闭     ：sudo ufw disable

4、添加规则 ：sudo ufw allow 3306(mysql端口号)/27017(Mongodb端口号)

设置完后，记得重启，大部分都能解决。
