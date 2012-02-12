--- 
categories: 
  - SQL
comments: true
layout: post
published: true
status: publish
tags: 
  - opera
  - TOM
title: "SQL GROUP BY 语句"
type: post
---
<div>SQL GROUP BY 语句<br>Previous Page<br>Next Page<br><div> </div>合计函数 (比如 SUM) 常常需要添加 GROUP BY 语句。<br>GROUP BY 语句<br><div> </div>GROUP BY 语句用于结合合计函数，根据一个或多个列对结果集进行分组。<br>SQL GROUP BY 语法<br>SELECT column_name, aggregate_function(column_name)<br>FROM table_name<br>WHERE column_name operator value<br>GROUP BY column_name<br>SQL GROUP BY 实例<br><div> </div>我们拥有下面这个 "Orders" 表：O_Id    OrderDate    OrderPrice    Customer<br>1    2008/12/29    1000    Bush<br>2    2008/11/23    1600    Carter<br>3    2008/10/05    700    Bush<br>4    2008/09/28    300    Bush<br>5    2008/08/06    2000    Adams<br>6    2008/07/21    100    Carter<br><div> </div>
<div> </div>现在，我们希望查找每个客户的总金额（总订单）。<br><div> </div>我们想要使用 GROUP BY 语句对客户进行组合。<br><div> </div>我们使用下列 SQL 语句：<br>SELECT Customer,SUM(OrderPrice) FROM Orders<br>GROUP BY Customer<br><div> </div>结果集类似这样：Customer    SUM(OrderPrice)<br>Bush    2000<br>Carter    1700<br>Adams    2000<br><div> </div>
<div> </div>很棒吧，对不对？<br><div> </div>让我们看一下如果省略 GROUP BY 会出现什么情况：<br>SELECT Customer,SUM(OrderPrice) FROM Orders<br><div> </div>结果集类似这样：Customer    SUM(OrderPrice)<br>Bush    5700<br>Carter    5700<br>Bush    5700<br>Bush    5700<br>Adams    5700<br>Carter    5700<br><div> </div>
<div> </div>上面的结果集不是我们需要的。<br><div> </div>那么为什么不能使用上面这条 SELECT 语句呢？解释如下：上面的 SELECT 语句指定了两列（Customer 和 SUM(OrderPrice)）。"SUM(OrderPrice)" 返回一个单独的值（"OrderPrice" 列的总计），而 "Customer" 返回 6 个值（每个值对应 "Orders" 表中的每一行）。因此，我们得不到正确的结果。不过，您已经看到了，GROUP BY 语句解决了这个问题。<br>GROUP BY 一个以上的列<br><div> </div>我们也可以对一个以上的列应用 GROUP BY 语句，就像这样：<br>SELECT Customer,OrderDate,SUM(OrderPrice) FROM Orders<br>GROUP BY Customer,OrderDate<br><!--WizHtmlContent-->
</div>
<div><a title="Wiz，个人知识管理，PKM。" href="http://wiz.cn">通过Wiz发布</a></div>
