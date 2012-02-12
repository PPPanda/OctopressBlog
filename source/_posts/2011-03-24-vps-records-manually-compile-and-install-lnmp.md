--- 
categories: 
  - Linux
comments: true
layout: post
published: true
status: publish
tags: 
  - mysql
  - nginx
  - server
title: vps上手动编译安装lnmp记录
type: post
---
按照张宴兄的方法(<a href="http://blog.s135.com/nginx_php_v6/">http://blog.s135.com/nginx_php_v6/</a>)手动编译安装lnmp,其中碰到的一些问题。   1.我的vps上的centos貌似很干净，连gcc.g++.c++都没有，没有就装  
{% codeblock %}
   yum install gcc gcc-c++ 
{% endcodeblock %}
  2.编译mysql的时候又碰到了累死的问题  
{% codeblock %}
   yum install gcc gcc-c++ 
{% endcodeblock %}
  解决办法：  
{% codeblock %}
   yum install gcc gcc-c++ 
{% endcodeblock %}
  
{% codeblock %}
   yum install gcc gcc-c++ 
{% endcodeblock %}
  <font color="#000000">3.mysql make的时候碰到异常</font>  
{% codeblock %}
   yum install gcc gcc-c++ 
{% endcodeblock %}
  <font color="#000000">4.编译php的时候遇到错误</font>  
{% codeblock %}
   yum install gcc gcc-c++ 
{% endcodeblock %}
  
{% codeblock %}
   yum install gcc gcc-c++ 
{% endcodeblock %}



{% codeblock %}
   yum install gcc gcc-c++ 
{% endcodeblock %}



{% codeblock %}
   yum install gcc gcc-c++ 
{% endcodeblock %}



{% codeblock %}
   yum install gcc gcc-c++ 
{% endcodeblock %}


<strong>终于。。编译通过了。。。不容易啊。。。</strong>

<strong>5.编译安装PHP5扩展模块时碰到</strong>


{% codeblock %}
   yum install gcc gcc-c++ 
{% endcodeblock %}



{% codeblock %}
   yum install gcc gcc-c++ 
{% endcodeblock %}
