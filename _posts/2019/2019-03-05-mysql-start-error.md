---
layout:     post
title:      mysql启动报错
no-post-nav: true
category: mysql
tags: [mysql]
excerpt: mysql
---

centos6启动mysql启动时出现以下错误：
[root@VM_0_6_centos mysql]# service mysql start
Starting MySQL.. ERROR! The server quit without updating PID file (/var/lib/mysql/VM_0_6_centos.pid).

解决办法：
你手动安装的mysql路径下有个my.cnf文件，删除./usr/local/mysql/my.cnf，删除这个文件，启动MySql服务，查看是否成功。
如果还是报错,接着可以查看
[root@VM_0_6_centos mysql]# vi  /etc/my.cnf
注释掉如下两行
datadir=/var/lib/mysql
socket=/var/lib/mysql/mysql.sock
重启mysql
[root@VM_0_6_centos mysql]# service mysql start
Starting MySQL.. SUCCESS! 






