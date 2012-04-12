---
layout: post
title: "配置MongoDB，使其运行在XAMPP下面"
date: 2012-04-12 13:45
comments: true
categories: 
  - php
tags: 
  - php
  - mongodb
  - xampp
---

今天在 [oschina](http://my.oschina.net/luckyperson2012/blog/53143) 上看到了这篇文章，讲怎么在 windows 下配置 MongoDB , 结果，我就跟着搞起来了，说下我的过程吧。

1. 下载mongodb压缩包 http://downloads.mongodb.org/win32/mongodb-win32-i386-2.0.4.zip；

2. 解压到 E:\xampp\mongodb;

3. 建立两个目录，一个是日志目录E:\xampp\mongodb\logs\logs.log，一个是存放数据文件的目录E:\xampp\mongodb\mongo_data，然后打开cmd命令行，执行

        E:\xampp\mongodb\bin\mongod --journal --logpath E:\xampp\mongodb\logs\logs.log --logappend --dbpath E:\xampp\mongodb\mongo_data --directoryperdb，

    显示：

        E:\>E:\xampp\mongodb\bin\mongod --journal --logpath E:\xampp\mongodb\logs\logs.l
        og --logappend --dbpath E:\xampp\mongodb\mongo_data --directoryperdb
        all output going to: E:\xampp\mongodb\logs\logs.log


    表示启动成功，默认使用端口分别是27017和28017，在浏览器中打开 [http://localhost:28017](http://localhost:28017)，可以看到其相关的一些信息。 可以通过添加参数--port的方式，来修改数据库端口

4. 为了方便起见，写了连个批处理命令来启动和关闭 mongodb

    mongodb_start.bat

        @echo off
        echo Diese Eingabeforderung nicht waehrend des Running beenden
        echo Please dont close Window while MongoDB is running
        echo MongoDB is trying to start
        echo Please wait  ...
        echo MongoDB is starting with --journal --logpath mongodb\logs\logs.log --logappend --dbpath mongodb\mongo_data --directoryperdb

        mongodb\bin\mongod --journal --logpath mongodb\logs\logs.log --logappend --dbpath mongodb\mongo_data --directoryperdb

        if errorlevel 1 goto error
        goto finish

        :error
        echo.
        echo MongoDB konnte nicht gestartet werden
        echo MongoDB could not be started
        pause

        :finish

    mongodb_stop.bat

        @echo off
        echo MongoDB shutdowm ...
        apache\bin\pv -f -k mongod.exe -q

        :exit


5. 下载php的mongodb插件，http://cloud.github.com/downloads/mongodb/mongo-php-driver/php_mongo-1.2.10.zip，按照你的php版本解压适合的dll文件到php的ext目录中，然后修改php.ini，添加类似 extension=php_mongo-1.2.10-5.3-vc9.dll 的语句，重启apache就OK了。这样你的PHP里就可以使用MongoDB了。

6. 常用的 mongodb 启动参数


        基本配置

        --------------------------------------------------------------------------------

         --quiet                          # 安静输出 
         --port arg                       # 指定服务端口号，默认端口27017 
         --bind_ip arg                    # 绑定服务IP，若绑定127.0.0.1，则只能本机访问，不指定默认本地所有IP 
         --logpath arg                    # 指定MongoDB日志文件，注意是指定文件不是目录 
         --logappend                      # 使用追加的方式写日志 
         --pidfilepath arg                # PID File 的完整路径，如果没有设置，则没有PID文件 
         --keyFile arg                    # 集群的私钥的完整路径，只对于Replica Set 架构有效 
         --unixSocketPrefix arg           # UNIX域套接字替代目录,(默认为 /tmp) 
         --fork                           # 以守护进程的方式运行MongoDB，创建服务器进程 
         --auth                           # 启用验证 
         --cpu                            # 定期显示CPU的CPU利用率和iowait 
         --dbpath arg                     # 指定数据库路径 
         --diaglog arg                    # diaglog选项 0=off 1=W 2=R 3=both 7=W+some reads 
         --directoryperdb                 # 设置每个数据库将被保存在一个单独的目录 
         --journal                        # 启用日志选项，MongoDB的数据操作将会写入到journal文件夹的文件里 
         --journalOptions arg             # 启用日志诊断选项 
         --ipv6                           # 启用IPv6选项 
         --jsonp                          # 允许JSONP形式通过HTTP访问（有安全影响） 
         --maxConns arg                   # 最大同时连接数 默认2000 
         --noauth                         # 不启用验证 
         --nohttpinterface                # 关闭http接口，默认关闭27018端口访问 
         --noprealloc                     # 禁用数据文件预分配(往往影响性能) 
         --noscripting                    # 禁用脚本引擎 
         --notablescan                    # 不允许表扫描 
         --nounixsocket                   # 禁用Unix套接字监听 
         --nssize arg (=16)               # 设置信数据库.ns文件大小(MB) 
         --objcheck                       # 在收到客户数据,检查的有效性， 
          --quota                          # 限制每个数据库的文件数，设置默认为8 
         --quotaFiles arg                 #  number of files allower per db, requires --quota 
         --rest                           # 开启简单的rest API 
         --repair                         # 修复所有数据库run repair on all dbs 
         --repairpath arg                 # 修复库生成的文件的目录,默认为目录名称dbpath 
         --profile arg         0=off 1=slow, 2=all  (0表示关闭profile,1表示只记录执行时间超过slowms配置的值的执行内容,2表示记录所有执行内容)
          --slowms arg (=100)   value of slow for profile and console log (如果profile配置为1并且没有配置slowms的话默认是100毫秒)
         --smallfiles                     # 使用较小的默认文件 
         --syncdelay arg (=60)            # 数据写入磁盘的时间秒数(0=never,不推荐) 
         --sysinfo                        # 打印一些诊断系统信息 
         --upgrade                        # 如果需要升级数据库 
         * Replicaton 参数

        --------------------------------------------------------------------------------

         --fastsync                      # 从一个dbpath里启用从库复制服务，该dbpath的数据库是主库的快照，可用于快速启用同步 
         --autoresync                    # 如果从库与主库同步数据差得多，自动重新同步， 
         --oplogSize arg                 # 设置oplog的大小(MB) 
         * 主/从参数

        --------------------------------------------------------------------------------

         --master                        # 主库模式 
         --slave                         # 从库模式 
         --source arg                    # 从库 端口号 
         --only arg                      # 指定单一的数据库复制 
         --slavedelay arg                # 设置从库同步主库的延迟时间 
          
         * Replica set(副本集)选项：

        --------------------------------------------------------------------------------

         --replSet arg                   # 设置副本集名称 
         * Sharding(分片)选项

        --------------------------------------------------------------------------------

         --configsvr                    # 声明这是一个集群的config服务,默认端口27019，默认目录/data/configdb 
         --shardsvr                     # 声明这是一个集群的分片,默认端口27018 
         --noMoveParanoia               # 关闭偏执为moveChunk数据保存? 


7. 上述参数都可以写入 mongod.conf 配置文档里例如：

        dbpath = mongodb\mongo_data
        directoryperdb = true
        logpath = mongodb\logs\logs.log
        logappend = true
        journal = true

8. 然后使用类似下面的语句启动 mongodb

        E:\xampp>mongodb\bin\mongod.exe --config  mongodb\mongodb.conf