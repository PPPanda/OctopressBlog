--- 
categories: 
  - PHP
comments: true
layout: post
published: true
status: publish
tags: 
  - loggers
  - "message log"
  - php
  - plog
title: php日志系统——plog
type: post
---
我在使用的时候发现了一个问题，就是要想在不同的文件夹下面记录不同的状况，例如：

在/logs/debug/ 下面记录debug 的日志， 在/logs/error/ 下面记录error的日志 就需要分别建立filedebug.php 和 fileerror.php 作为写入的引擎，事实上这两个类在类内部的代码里面是完全一模一样的。

好吧，这不算什么致命的问题，重新集成一次file.php就可以了。

总的来说，这个日志系统还是不错的。

<!--more-->

plog的介绍：

{% codeblock %}
日志是一个应用程序的重要组成部分，今天在看pylons对日志的处理时，受到启发，于是plog就诞生了。

很多php框架都忽略了日志的重要性(如kohana)，往往只是能用，自定义和可扩展性不够，等到程序出了问题，再想找原因时就比较麻烦了。
<h3>plog简介</h3>
plog是一款轻量级，易定制，易使用，易扩展的php日志系统。可以很方便地添加日志处理工具、自定义输出格式、自定义日志类型等等。
<h3>plog使用</h3>
使用plog很简单，在每个要加日志的文件里，输入以下代码
<div>

{% codeblock %}

{% codeblock %}
<?php
// 载入plog类
require '../../plog/classes/plog.php';

// 设置config，config文件位置可以自定义
// 对于单入口文件，这两段代码可以放在入口文件处
Plog::set_config(include 'path/to/config.php');

// 把下面这段代码放到对应的文件里
$log = Plog::factory(__FILE__);

// 使用
$log->debug('this is debug message');
$log->info('this is info message');

{% endcodeblock %}

{% endcodeblock %}

</div>
<h3>plog的配置</h3>
plog的配置很灵活，下面是个demo config
<div>

{% codeblock %}

{% codeblock %}
<?php
// 载入plog类
require '../../plog/classes/plog.php';

// 设置config，config文件位置可以自定义
// 对于单入口文件，这两段代码可以放在入口文件处
Plog::set_config(include 'path/to/config.php');

// 把下面这段代码放到对应的文件里
$log = Plog::factory(__FILE__);

// 使用
$log->debug('this is debug message');
$log->info('this is info message');

{% endcodeblock %}

{% endcodeblock %}

</div>
<h4>几点说明</h4>
<ul>
<li>levels项，每一个值都是一个方法，不过是小写的，如$log→debug(‘message’)。如果某个方法不在这些levels里会触发异常。</li>
	<li>日志格式的可选变量在plog/formatter.php里，每一个get开头的方法就是，如果觉得不够用，可以自己添加。</li>
</ul>
<h3>日志内容</h3>
日志内容取决于日志格式，下面是demo
<div>

{% codeblock %}

{% codeblock %}
<?php
// 载入plog类
require '../../plog/classes/plog.php';

// 设置config，config文件位置可以自定义
// 对于单入口文件，这两段代码可以放在入口文件处
Plog::set_config(include 'path/to/config.php');

// 把下面这段代码放到对应的文件里
$log = Plog::factory(__FILE__);

// 使用
$log->debug('this is debug message');
$log->info('this is info message');

{% endcodeblock %}

{% endcodeblock %}

</div>
<h3>下载</h3>
<a href="https://github.com/lzyy/plog">https://github.com/lzyy/plog</a>
--EOF--若无特别说明，本站文章均为原创，转载请保留链接，谢谢
来自：http://blog.leezhong.com/project/2010/12/06/plog.html
{% endcodeblock %}
