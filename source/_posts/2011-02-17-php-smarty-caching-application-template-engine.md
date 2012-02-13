--- 
categories: 
  - PHP
comments: true
layout: post
published: true
status: publish
tags: 
  - php
  - Smarty
  - 缓存
title: PHP模板引擎Smarty缓存应用
type: post
---
1：smarty 缓存的配置  Php代码<a href="http://writeblog.csdn.net/#"></a>  2:smarty缓存的使用和清除  Php代码<a href="http://writeblog.csdn.net/#"></a>  <div>   
{% codeblock %}
$<span style="color: #800000">smarty-</span>><span style="color: #800000">display</span>('<span style="color: #800000">cache</span>.<span style="color: #800000">tpl</span>', <span style="color: #800000">cache</span>_<span style="color: #800000">id</span>);  //<span style="color: #800000">创建带ID的缓存</span>,<span style="color: #800000">cache</span>.<span style="color: #800000">tpl</span>  <span style="color: #800000">模板文件</span>
$<span style="color: #800000">smarty-</span>><span style="color: #800000">clear</span>_<span style="color: #800000">all</span>_<span style="color: #800000">cache</span>(); //<span style="color: #800000">清除所有缓存</span>
$<span style="color: #800000">smarty-</span>><span style="color: #800000">clear</span>_<span style="color: #800000">cache</span>('<span style="color: #800000">index</span>.<span style="color: #800000">htm</span>'); //<span style="color: #800000">清除index</span>.<span style="color: #800000">tpl的缓存</span> 
$<span style="color: #800000">smarty-</span>><span style="color: #800000">clear</span>_<span style="color: #800000">cache</span>('<span style="color: #800000">index</span>.<span style="color: #800000">htm</span>',<span style="color: #800000">cache</span>_<span style="color: #800000">id</span>); //<span style="color: #800000">清除指定id的缓存</span>
{% endcodeblock %}

</div>
<!--more-->

3：smarty的局部缓存

insert 函数默认是不缓存的。并且这个熟悉不能修改

Html代码<a href="http://writeblog.csdn.net/#"></a>

模板 index.htm   

<div>
  
{% codeblock %}
$<span style="color: #800000">smarty-</span>><span style="color: #800000">display</span>('<span style="color: #800000">cache</span>.<span style="color: #800000">tpl</span>', <span style="color: #800000">cache</span>_<span style="color: #800000">id</span>);  //<span style="color: #800000">创建带ID的缓存</span>,<span style="color: #800000">cache</span>.<span style="color: #800000">tpl</span>  <span style="color: #800000">模板文件</span>
$<span style="color: #800000">smarty-</span>><span style="color: #800000">clear</span>_<span style="color: #800000">all</span>_<span style="color: #800000">cache</span>(); //<span style="color: #800000">清除所有缓存</span>
$<span style="color: #800000">smarty-</span>><span style="color: #800000">clear</span>_<span style="color: #800000">cache</span>('<span style="color: #800000">index</span>.<span style="color: #800000">htm</span>'); //<span style="color: #800000">清除index</span>.<span style="color: #800000">tpl的缓存</span> 
$<span style="color: #800000">smarty-</span>><span style="color: #800000">clear</span>_<span style="color: #800000">cache</span>('<span style="color: #800000">index</span>.<span style="color: #800000">htm</span>',<span style="color: #800000">cache</span>_<span style="color: #800000">id</span>); //<span style="color: #800000">清除指定id的缓存</span>
{% endcodeblock %}

</div>

index.php   

<div>
  
{% codeblock %}
$<span style="color: #800000">smarty-</span>><span style="color: #800000">display</span>('<span style="color: #800000">cache</span>.<span style="color: #800000">tpl</span>', <span style="color: #800000">cache</span>_<span style="color: #800000">id</span>);  //<span style="color: #800000">创建带ID的缓存</span>,<span style="color: #800000">cache</span>.<span style="color: #800000">tpl</span>  <span style="color: #800000">模板文件</span>
$<span style="color: #800000">smarty-</span>><span style="color: #800000">clear</span>_<span style="color: #800000">all</span>_<span style="color: #800000">cache</span>(); //<span style="color: #800000">清除所有缓存</span>
$<span style="color: #800000">smarty-</span>><span style="color: #800000">clear</span>_<span style="color: #800000">cache</span>('<span style="color: #800000">index</span>.<span style="color: #800000">htm</span>'); //<span style="color: #800000">清除index</span>.<span style="color: #800000">tpl的缓存</span> 
$<span style="color: #800000">smarty-</span>><span style="color: #800000">clear</span>_<span style="color: #800000">cache</span>('<span style="color: #800000">index</span>.<span style="color: #800000">htm</span>',<span style="color: #800000">cache</span>_<span style="color: #800000">id</span>); //<span style="color: #800000">清除指定id的缓存</span>
{% endcodeblock %}

</div>

<strong>转自：<a href="http://blog.csdn.net/webdesman/archive/2009/09/12/4541627.aspx">http://blog.csdn.net/webdesman/archive/2009/09/12/4541627.aspx</a></strong>
