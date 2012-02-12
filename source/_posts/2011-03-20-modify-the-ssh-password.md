--- 
categories: 
  - Linux
comments: true
layout: post
published: true
status: publish
tags: 
  - passwd
  - root
  - ssh
title: 修改SSH登录密码
type: post
---
SSH登录时要求输入的其实是系统的用户与密码，所以如果要修改ssh登录密码的话，只要更改系统用户的密码就可以了。命令如下：


{% codeblock %}
passwd root #root就是你要修改密码的用户名,键入命令之后就会要求你修改这个用户的密码，键入两次就OK了。
{% endcodeblock %}


 
