--- 
categories: 
  - SQL
comments: true
layout: post
published: true
status: publish
tags: 
  - "42"
  - cat
  - email
  - free
  - ie
  - mysql
  - OS
  - server
  - User
  - 同步
  - 更新
  - 转载
title: "SET 和 SHOW语法（三）"
type: post
---
 
<span class="style1">译者：叶金荣（Email:<img style="border: 0px none initial;" src="http://imysql.cn/files/pictures/email.gif" border="0" alt="">），来源：MySQL手册版本 5.0.20，转载请注明译者和出处，并且不能用于商业用途，违者必究。</span>


<h4 style="font-weight: normal; font-family: 'Times New Roman'; font-size: 16px; padding: 0px; margin: 0px;"><a name="SHOW_PROCESSLIST"></a></h4>



{% codeblock %}
SHOW [FULL] PROCESSLIST
{% endcodeblock %}


{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 显示了有哪些线程在运行。也可以执行 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 命令来得到这些信息。如果有 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 权限，则可以看到全部的线程，否则，只能看到自己发起的线程（这是指，当前对应的MySQL帐户运行的线程）。详情请看“<a style="color: #027ac6; text-decoration: none;" href="http://imysql.cn/?q=node/15">14.5.4.3 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 Syntax</a>”。如果没有使用关键字 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
，则只能看到每个查询的前100个字符。
从MySQL 4.0.12起，结果中还会以的 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 格式来显示通过TCP/IP方式连接过来的客户端的主机名，这就可以知道每个客户端都正在做什么。
这个语句在出现“too many connections”错误时想看看都正在执行什么查询非常有用。MySQL为拥有 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 权限的账户保留了一个额外的连接，这就保证让管理员总是可以连上检查系统状况（假定没有给每个系统账户都授予这个权限）。<!--more-->

{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 结果中一些常见的状态如下：

<dl style="margin-top: 0.5em; margin-right: 0px; margin-bottom: 1em; margin-left: 1.5em;">


<dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">正在检查数据表（这是自动的）。


</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">正在将表中修改的数据刷新到磁盘中，同时正在关闭已经用完的表。这是一个很快的操作，如果不是这样的话，就应该确认磁盘空间是否已经满了或者磁盘是否正处于重负中。



</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">同步从服务器正在连接主服务器。


</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">由于临时结果集大于 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
，正在将临时表从内存存储转为磁盘存储以节省内存。


</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">正在创建临时表以存放部分查询结果。



</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">服务器正在执行多表删除中的第一部分，刚删除第一个表。



</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">服务器正在执行多表删除中的第二部分，正在删除其他表的记录。


</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}



</dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">正在执行 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
，等待其他线程关闭数据表。


</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">发送了一个 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 请求给某线程，那么这个线程将会检查 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 标志位，同时会放弃下一个 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 请求。MySQL会在每次的主循环中检查 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 标志位，不过有些情况下该线程可能会过一小段才能死掉。如果该线程程被其他线程锁住了，那么 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 请求会在锁释放时马上生效。



</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">被其他查询锁住了。


</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">正在处理 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 查询的记录，同时正在把结果发送给客户端。


</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">正在为 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 做排序。


</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">正在为 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 做排序。


</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">这个过程应该会很快，除非受到其他因素的干扰。例如，在执 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 或 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 语句行完以前，数据表无法被其他线程打开。 正尝试打开一个表。



</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">正在执行一个 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 方式的查询，但是MySQL无法在前一个阶段优化掉那些重复的记录。因此，MySQL需要再次去掉重复的记录，然后把结果发送给客户端。


</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">获得对一个表的锁，但是被通知到得到锁之后该表结构会发生变化。因此就先释放锁，关闭表，重新打开它


</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">修复指令正在用排序算法创建索引。


</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">修复指令正在利用索引缓存一个个地创建新索引。它会比 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 慢很多。


</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">正在将符合条件的记录找出来以备更新。它必须在 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 要修改相关的记录之前就完成了。


</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">正在等待客户端发送新请求.


</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">正在等待取得一个外部系统锁。如果当前没有需要运行多个 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 服务器同时来请求同一个表，那么可以通过增加 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 参数来禁止外部系统锁。


</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 处理程序正在尝试取得一个锁表以插入新记录。


</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">正在搜索需要更新的记录，并正在更新。


</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">正在等待 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
。


</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">该线程得到通知，数据表结构已经被修改了，需要重新打开数据表以取得新的结构。然后，为了能的重新打开数据表，必须等到所有其他线程关闭这个表。以下几种情况下会产生这个通知：
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
, 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
, 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
, 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
, 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
, 或 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
。


</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 已经处理完了所有待处理的插入操作，正在等待新的请求。


</dd> </dl>
大部分状态对应很快的操作，只要有一个线程保持同一个状态好几秒钟，那么可能是有问题发生了，需要检查一下。
还有其他的状态没在上面中列出来，不过它们大部分只是在查看服务器是否产生错误了时才用得着。


<h4 style="font-weight: normal; font-family: 'Times New Roman'; font-size: 16px; padding: 0px; margin: 0px;"><a name="SHOW_STATUS"></a></h4>



{% codeblock %}
SHOW [FULL] PROCESSLIST
{% endcodeblock %}


{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 显示了各种服务器状态信息。也可以通过运行 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 命令来得到结果。
这里有部分输出结果，某些变量和它对应的值可能跟你的系统不大一样。各种变量所代表的意义详情请看“<a style="color: #027ac6; text-decoration: none;" href="http://imysql.cn/?q=node/15">5.2.4 Server Status Variables</a>”。


{% codeblock %}
SHOW [FULL] PROCESSLIST
{% endcodeblock %}

可以通过 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 分句，就可以值显示匹配的变量及其值：


{% codeblock %}
SHOW [FULL] PROCESSLIST
{% endcodeblock %}



<h4 style="font-weight: normal; font-family: 'Times New Roman'; font-size: 16px; padding: 0px; margin: 0px;"><a name="SHOW_TABLE_STATUS"></a></h4>



{% codeblock %}
SHOW [FULL] PROCESSLIST
{% endcodeblock %}


{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
(在MySQL 3.23新增的)跟 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
类似，它还显示每个表的许多相关信息。也可以通过运行 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 命令来显示同样的结果。

{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 返回了以下几个字段的信息：

<dl style="margin-top: 0.5em; margin-right: 0px; margin-bottom: 1em; margin-left: 1.5em;">


<dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">表名。



</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">数据表的存储引擎类型，在MySQL 4.1.2以前，这个值被标志为 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
。详情请看“<a style="color: #027ac6; text-decoration: none;" href="http://imysql.cn/?q=node/15">15 MySQL Storage Engines and Table Types</a>”。



</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">数据表的 <tt>`.frm'</tt> 文件版本号。



</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">记录存储格式（
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
—固定的, 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
—动态的, 或 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
—压缩的）。



</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">记录数。在某些存储引擎中，例如
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 和 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 他们存储了精确的记录数。不过其他存储引擎中，例如 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
，它可能只是近似值。



</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">记录的平均长度。



</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">数据文件长度。



</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">数据文件的最大长度。对固定格式存储记录的表来说，它是表的最大记录数。对动态存储记录的表来说，它是数据表存储的最大字节数，给出了数据指针使用的大小。



</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">索引文件的长度。



</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">已经分配还未使用的字节数。



</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">下一个 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 的值。



</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">表的创建时间。



</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">表最后一次更新时间。



</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">表最后一次检查时间。



</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">表的字符集和校正字符集（在中MySQL4.1.1新增的）。



</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">实时的校验和值（如果有的话） （在中MySQL4.1.1新增的）。



</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">额外留给 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 的选项。



</dd> <dt>
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 </dt> <dd style="margin-top: 0px; margin-right: 0px; margin-bottom: 0.5em; margin-left: 1.5em;">创建表时的备注（或者一些MySQL无法存取改表的相关信息）。 </dd> </dl>
表注释一栏，
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 类型的表会报告它所属的表剩余表空间。对一个使用共享表空间的表来说，它是指共享表空间的剩余空间。如果使用多表空间并且该表有自己的表空间，那么剩余空间就是全部属于这个表的。
对 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 (
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
) （内存）表来说，
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
, 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
, 和 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 的值接近内存实际分配结果。分配算法预留了大量内存空间以减少重复分配内存的操作。


<h4 style="font-weight: normal; font-family: 'Times New Roman'; font-size: 16px; padding: 0px; margin: 0px;"><a name="SHOW_TABLES"></a></h4>



{% codeblock %}
SHOW [FULL] PROCESSLIST
{% endcodeblock %}


{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 列出了给定数据库中的非临时（non-
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
）表。也可以通过命令 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 来列出这些表。
在MySQL 5.0.1以前，
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 的结果中只有一个字段显示表名。从MySQL 5.0.1开始，
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 还列出了数据库中的视图，还有第二个字段。第二字段的值是表的 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 （基表）或者视图名。
<strong>请注意</strong>，如果没有表的相应权限，那么在 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 或
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 结果中就不会列出该表。

{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 列出了所有当前正被打开的表。详情请看“<a style="color: #027ac6; text-decoration: none;" href="http://imysql.cn/?q=node/15">7.4.8 How MySQL Opens and Closes Tables</a>”。显示结果中的 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 字段告诉我们该表被 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 和 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 的时间。从MySQL 3.23.33开始，可以使用 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 关键字。


<h4 style="font-weight: normal; font-family: 'Times New Roman'; font-size: 16px; padding: 0px; margin: 0px;"><a name="SHOW_VARIABLES"></a></h4>



{% codeblock %}
SHOW [FULL] PROCESSLIST
{% endcodeblock %}


{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 显示了一些MySQL的系统变量值。这些信息也可以通过运行命令 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 来得到。

{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 和 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 可选项是从MySQL 4.0.3开始可以用的。如果是 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
，就会得到每次新连接中使用的变量值。如果是

{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
，则得到当前连接中变量的值。如果你不加任何选选项，那么 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 就是默认的。
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 和 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 一样。
如果变量的默认值不大合适，则可以在 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 启动时通过命令行增加相关选项或者通过 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 语句来做到。详情请看“<a style="color: #027ac6; text-decoration: none;" href="http://imysql.cn/?q=node/15">5.2.1 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 Command-Line Options</a>”和“<a style="color: #027ac6; text-decoration: none;" href="http://imysql.cn/?q=node/15">14.5.3.1 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
Syntax</a>. ”。
以下列出了部分结果，这些结果值可能与您的系统的值不一样。每个变量的值对应的意义详情请看“<a style="color: #027ac6; text-decoration: none;" href="http://imysql.cn/?q=node/15">5.2.3 Server System Variables</a>”。如何协调这些变量详情请看“<a style="color: #027ac6; text-decoration: none;" href="http://imysql.cn/?q=node/15">7.5.2 Tuning Server Parameters</a>”。


{% codeblock %}
SHOW [FULL] PROCESSLIST
{% endcodeblock %}

可以使用 
{% codeblock %}
SHOW PROCESSLIST
{% endcodeblock %}
 分句列出匹配的变量：


{% codeblock %}
SHOW [FULL] PROCESSLIST
{% endcodeblock %}
