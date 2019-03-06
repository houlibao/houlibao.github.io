---
layout:     post
title:      centos6开机自动启动kafka
no-post-nav: true
category: kafka
tags: [kafka]
excerpt: kafka
---


1.下载稳定版本的kafka,解压即可

2.将kafka配置为服务

    将kafka的开机脚本文件新建到/etc/inti.d目录下

  vi /etc/init.d/kafka

    修改执行的权限 

chmod 755 /etc/init.d/kafka

   接着对脚本进行修改

		#!/bin/sh
		#chkconfig: 2345 10 90
		#description: kafka  service
		#设置java安装路径
		export JAVA_HOME=/usr/local/java/jdk1.8.0_201
		#kafka auto start
		echo "zookeeper start.............."
		#切换到kafka的解压目录
		cd /home/yvan/software/kafka_2.12-0.11.0.0/bin/
		./zookeeper-server-start.sh -daemon ../config/zookeeper.properties
		sleep 3s
		echo "kafka start .............."
		./kafka-server-start.sh -daemon ../config/server.properties
		echo "kafka end ................"
   
3.使用chkconfig -add kafka 将其添加为服务

chkconfig --add kafka

4.配置开机启动

chkconfig kafka on


说明：此方法的前提是centos已经安装好jdk,另外只做开机自动启动的作用，如果需要杀死进程，请使用jps查看kafka端口号，配合kill命令使用。

命令行启动kafka使用 service kafka start

zookeeper start..............

kafka start ..............

kafka end ................


