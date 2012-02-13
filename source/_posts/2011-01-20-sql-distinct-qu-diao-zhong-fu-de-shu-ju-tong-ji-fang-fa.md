--- 
categories: 
  - SQL
comments: true
layout: post
published: true
status: publish
tags: 
  - server
  - 分类
  - 转载
title: "SQL DISTINCT去掉重复的数据统计方法"
type: post
---
SQL DISTINCT去掉重复的数据统计方法(2009-01-13 15:05:43)转载 标签：sqldistinct杂谈     分类：SQL<br><div> </div>
<div> </div>SELECT指令让我们能够读取表格中一个或数个栏位的所有资料。这将把所有的资料都抓出，无论资料值有无重复。在资料处理中，我们会经常碰到需要找出表格内的不同资料值的情况。换句话说，我们需要知道这个表格/栏位内有哪些不同的值，而每个值出现的次数并不重要。这要如何达成呢？在SQL中，这是很容易做到的。我们只要在SELECT后加上一个DISTINCT就可以了。 DISTINCT的语法如下：<br><div> </div>
<div> </div>
<div> </div> SELECT DISTINCT "栏位名"<br><div> </div>
<div> </div>
<div> </div> FROM "表格名"<br><div> </div>
<div> </div>
<div> </div>举例来说，若要在以下的表格，Store_Information，找出所有不同的店名时，Store_Information 表格<br>store_name    <br>Sales    <br>Date<br><div> </div>1    <br>$1500    <br>Jan-05-1999<br><div> </div>2    <br>$250    <br>Jan-07-1999<br><div> </div>1    <br>$300    <br>Jan-08-1999<br><div> </div>3    <br>$700    <br>Jan-08-1999<br><div> </div>
<div> </div>我們就鍵入，<br><div> </div>SELECT DISTINCT store_name FROM Store_Information<br><div> </div>結果:<br><div> </div>1<br><div> </div>2<br><div> </div>3<br>DISTINCT 关键字可从 SELECT 语句的结果中除去重复的行。如果没有指定 DISTINCT，那么将返回所有行，包括重复的行。  <br><div> </div>select count(distinct t.destaddr) from nbyd_send t where t.input_time > to_date('2007-2-1','yyyy-mm-dd') and t.input_time < to_date('2007-3-1','yyyy-mm-dd')<br><div> </div>可以统计出一个月中的用户数量。<br><div> </div>关于如何快速得知里面每一个号码重复的个数问题的解答:<br><div> </div>利用分组函数的SQL语句<br>select t.tel,count(*) from nbyd_deliver t group by t.tel ;<br><div> </div>group by 解决重复数据的个数统计<br><div> </div>适用于各种关系型数据库,如oracle,SQL Server<br><div> </div>查询重复的数据<br>select * from (select v.xh,count(v.xh) num from sms.vehicle v group by v.xh) where num>1;--169<br><div> </div>select v.xh,count(v.xh) num from sms.vehicle v group by v.xh having count(v.xh)=2;<br><div> </div>删除重复的数据<br><div> </div>create table mayong as (select distinct* from sms.vehicle);<br><div> </div>delete from sms.vehicle ;<br><div> </div>insert into sms.vehicle select * from mayong;<br><div> </div>在oracle中，有个隐藏了自动rowid，里面给每条记录一个唯一的rowid，我们如果想保留最新的一条记录，我们就可以利用这个字段，保留重复数据中rowid最大的一条记录就可以了。<br><div> </div>
<div> </div>
<div> </div>　　下面是查询重复数据的一个例子：<br><div> </div>select a.rowid,a.* from 表名 a<br>where a.rowid !=<br>(<br>select max(b.rowid) from 表名 b<br>where a.字段1 = b.字段1 and<br>a.字段2 = b.字段2<br>)<br><div> </div>　　下面我就来讲解一下，上面括号中的语句是查询出重复数据中rowid最大的一条记录。<br><div> </div>　　而外面就是查询出除了rowid最大之外的其他重复的数据了。<br>　　由此，我们要删除重复数据，只保留最新的一条数据，就可以这样写了：<br>delete from 表名 a<br>where a.rowid !=<br>(<br>select max(b.rowid) from 表名 b<br>where a.字段1 = b.字段1 and<br>a.字段2 = b.字段2<br>)<br><div> </div>　　随便说一下，上面语句的执行效率是很低的，可以考虑建立临时表，讲需要判断重复的字段、rowid插入临时表中，然后删除的时候在进行比较。<br>create table 临时表 as<br>    select a.字段1,a.字段2,MAX(a.ROWID) dataid from 正式表 a GROUP BY a.字段1,a.字段2;<br>delete from 表名 a<br>where a.rowid !=<br>(<br>select b.dataid from 临时表 b<br>where a.字段1 = b.字段1 and<br>a.字段2 = b.字段2<br>);<br>commit;<br><div> </div>　　二、对于完全重复记录的删除<br><div> </div>　　对于表中两行记录完全一样的情况，可以用下面语句获取到去掉重复数据后的记录：<br>select distinct * from 表名<br>可以将查询的记录放到临时表中，然后再将原来的表记录删除，最后将临时表的数据导回原来的表中。如下：<br>CREATE TABLE 临时表 AS (select distinct * from 表名);<br>drop table 正式表;<br>insert into 正式表 (select * from 临时表);<br>drop table 临时表;<br><div> </div>　　如果想删除一个表的重复数据，可以先建一个临时表，将去掉重复数据后的数据导入到临时表，然后在从临时表将数据导入正式表中，如下：<br><div> </div>INSERT INTO t_table_bak<br>select distinct * from t_table;<br><div><!--WizHtmlContent--></div>
<div><a title="Wiz，个人知识管理，PKM。" href="http://wiz.cn">通过Wiz发布</a></div>
