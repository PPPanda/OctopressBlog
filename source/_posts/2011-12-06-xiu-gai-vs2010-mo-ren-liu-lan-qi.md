--- 
categories: 
  - "C#"
comments: true
layout: post
published: true
status: publish
tags: []
title: "修改 vs2010 默认浏览器"
type: post
---
修改该目录里的配置文件

C:\Users\[登陆账户ID]\AppData\Local\Microsoft\VisualStudio\10.0\browsers.xml
修改为

{% codeblock %}

<?xml version="1.0"?><browserinfo><browser><name>Mozilla Firefox</name><path>"C:\Program Files (x86)\Mozilla Firefox\firefox.exe"</path><resolution>0</resolution><isdefault>True</isdefault></browser><browser><name>Internet Explorer</name><path>"C:\Program Files (x86)\Internet Explorer\iexplore.exe"</path><resolution>0</resolution><isdefault>False</isdefault><dde><service>IExplore</service><topicopenurl>WWW_OpenURL</topicopenurl><itemopenurl>"%s",,0xffffffff,3,,,,</itemopenurl><topicactivate>WWW_Activate</topicactivate><itemactivate>0xffffffff,0</itemactivate></dde></browser></browserinfo>

{% endcodeblock %}


然后保存为只读，Ok了
