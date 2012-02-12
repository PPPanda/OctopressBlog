--- 
categories: 
  - CSS
comments: true
layout: post
published: true
status: publish
tags: 
  - BUG
  - ie6
title: "一个IE6的div 高度BUG"
type: post
---
我也不想管IE6的，但是这里毕竟是中国，使用IE6的人还是很多地！

今天做项目的时候发现了一个IE6的BUG

BUG表现：

div 的height 明明设为1px了，但是在IE6下显示出来高度是10px。

解决方法：

加上样式:font-size:0;

至于为什么，我忘掉了。。。
