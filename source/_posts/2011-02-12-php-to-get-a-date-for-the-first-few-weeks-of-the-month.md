--- 
categories: 
  - PHP
comments: true
layout: post
published: true
status: publish
tags: 
  - date
  - php
  - week
  - 星期
title: php获取一个日期为当月的第几周
type: post
---
{% codeblock %}


{% codeblock %}


function checkweek($day)

{

$month = date('m', time()); // 获取本月

$year = date('Y', time()); // 获取本年

$firstday = date('w', mktime(0, 0, 0, $month, 1, $year)); //本月1号星期数

$firstweek = 7 - $firstday; // 第1周天数

$week = ceil(($day - $firstweek) / 7) + 1; return $year.'年'.$month.'月'.$day . '号属于本月第' . $week . '周';

}

$a = checkweek(14); //本月几号

echo $a;


{% endcodeblock %}


{% endcodeblock %}
 
