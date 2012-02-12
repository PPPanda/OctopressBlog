--- 
categories: 
  - JavaScript
comments: true
layout: post
published: true
status: publish
tags: 
  - isNaN
  - java
  - JavaScript
  - 数字
title: "Javascript 检查字符串是否是数字的几种方法"
type: post
---
<img src="http://www.cnblogs.com/Images/OutliningIndicators/None.gif" alt="" align="top">//判断是否是正整数
<img src="http://www.cnblogs.com/Images/OutliningIndicators/None.gif" alt="" align="top">function IsNum(s)
<img id="Codehighlighter1_29_192_Open_Image" src="http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockStart.gif" alt="" align="top">{
<img id="Codehighlighter1_46_172_Open_Image" src="http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif" alt="" align="top"> if(s!=null){
<img src="http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif" alt="" align="top"> var r,re;
<img src="http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif" alt="" align="top"> re = /\d*/i; //\d表示数字,*表示匹配多个数字
<img src="http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif" alt="" align="top"> r = s.match(re);
<img src="http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif" alt="" align="top"> return (r==s)?true:false;
<img src="http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif" alt="" align="top"> }
<img src="http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif" alt="" align="top"> return false;
<img src="http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockEnd.gif" alt="" align="top">}
<img src="http://www.cnblogs.com/Images/OutliningIndicators/None.gif" alt="" align="top"><img src="http://www.cnblogs.com/Images/OutliningIndicators/None.gif" alt="" align="top">//判断是否为数字
<img src="http://www.cnblogs.com/Images/OutliningIndicators/None.gif" alt="" align="top">function IsNum(s)
<img id="Codehighlighter1_222_307_Open_Image" src="http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockStart.gif" alt="" align="top">{
<img src="http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif" alt="" align="top"> if (s!=null && s!="")
<img id="Codehighlighter1_254_287_Open_Image" src="http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockStart.gif" alt="" align="top"> {
<img src="http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif" alt="" align="top"> return !isNaN(s);
<img src="http://www.cnblogs.com/Images/OutliningIndicators/ExpandedSubBlockEnd.gif" alt="" align="top"> }
<img src="http://www.cnblogs.com/Images/OutliningIndicators/InBlock.gif" alt="" align="top"> return false;
<img src="http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockEnd.gif" alt="" align="top">}
<img src="http://www.cnblogs.com/Images/OutliningIndicators/None.gif" alt="" align="top"><img src="http://www.cnblogs.com/Images/OutliningIndicators/None.gif" alt="" align="top">
