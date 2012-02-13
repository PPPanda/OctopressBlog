--- 
categories: 
  - Linux
comments: true
layout: post
published: true
status: publish
tags: 
  - ie
  - java
  - jdk
  - OS
  - PLUGIN
  - 乌班图
  - update
title: "ubuntu 环境下 安装 java6-sdk"
type: post
---
<span style="line-height: 18px;"> </span>

<h3><span class="mw-headline">安装sun-java6</span></h3>添加partner源
{% codeblock %}
sudo add-apt-repository "deb http://archive.canonical.com/ubuntu maverick partner"
{% endcodeblock %}
(注：  如果系统提示没有add-apt-repository命令，则需要先安装python-software-properties，命令sudo  apt-get install  python-software-properties。另外，有些版本的ubuntu即使安装了python-software-properties 也无add-apt-repository命令,此时需要手动添加此行"deb <a class="external free" title="http://archive.canonical.com/ubuntu" rel="nofollow" href="http://archive.canonical.com/ubuntu">http://archive.canonical.com/ubuntu</a> maverick partner"到/etc/apt/sources.list文件中。)

更新系统
{% codeblock %}
sudo add-apt-repository "deb http://archive.canonical.com/ubuntu maverick partner"
{% endcodeblock %}
安装jre
{% codeblock %}
sudo add-apt-repository "deb http://archive.canonical.com/ubuntu maverick partner"
{% endcodeblock %}
安装jdk
{% codeblock %}
sudo add-apt-repository "deb http://archive.canonical.com/ubuntu maverick partner"
{% endcodeblock %}
查看版本信息
{% codeblock %}
sudo add-apt-repository "deb http://archive.canonical.com/ubuntu maverick partner"
{% endcodeblock %}
<a id=".E8.AE.BE.E4.B8.BA.E9.BB.98.E8.AE.A4Java" name=".E8.AE.BE.E4.B8.BA.E9.BB.98.E8.AE.A4Java"></a><h3><span class="mw-headline">设为默认Java</span></h3>
{% codeblock %}
sudo add-apt-repository "deb http://archive.canonical.com/ubuntu maverick partner"
{% endcodeblock %}
选择即可 

 
