--- 
categories: 
  - SQL
comments: true
layout: post
published: true
status: publish
tags: 
  - memcache
  - mysql
  - oracle
title: "MySQL 数据库引入 memcached，支持 NoSQL"
type: post
---
mysql 也开始支持NoSql了，这样一来如果可以直接用sql语句进行检索查询的话无疑会把原先的Memcache等给排挤出去，如果效率方面又很高的话，那么memcache还活什么啊？

嗯。。。期待。。。

{% codeblock %}
Oracle 前天在 <strong>2011 MySQL user conference and expo</strong> 大会上发布的 MySQL 5.6.2 测试版本，详情请看<a href="http://www.oschina.net/news/17118/mysql-5-6-2-dev">这里</a>。

该版本最值得关注的便是对 NoSQL 技术的支持，尽管目前还是实验阶段，该技术使得 MySQL 内置 NoSQL 技术，该技术可减少 memcached 的查询延迟。在单台机器中，NoSQL 当前只适用一张 InnoDB 表，但未来将支持多个表。在 memcached 中的 key和value 分别对应表中的相应字段，同时可为 key定义多列的值。所有这些数据都存储在一张 InnoDB 表，可通过 SQL 命令来进行检索和修改。目前集成 memcached 守护进程的版本只能用于 Linux。

来自 InnoDB 的<a href="http://blogs.innodb.com/wp/2011/04/get-started-with-innodb-memcached-daemon-plugin/" target="_blank">博客</a>向你介绍如何启用该功能

下图是该技术的架构图：

<img src="http://pic003.cnblogs.com/2011/66372/201104/2011041310182092.jpg" alt="" width="627" height="468">

来自:<a href="http://news.cnblogs.com/n/97243/">http://news.cnblogs.com/n/97243/</a>
{% endcodeblock %}
