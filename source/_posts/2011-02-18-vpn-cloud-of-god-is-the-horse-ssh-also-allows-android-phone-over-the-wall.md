--- 
categories: 
  - internet
comments: true
layout: post
published: true
status: publish
tags: 
  - gfw
  - google
  - nginx
  - server
title: VPN神马的都是浮云！SSH也能让Android手机翻墙！
type: post
---
又是热血的标题=_= 其实，这个方法没有大家所想象的那么完美。首先，经过我的测试（测试用机：Motorola Milestone），发现如下的局限性：  <ol>
<li>只能在手机用WIFI上网的时候使用（未严格验证，使用CM 6.12和MIUI得到这个结果，欢迎大家使用各种版本测试） </li>    <li>只对原生的浏览器Chrome Lite有效（未严格验证，使用CM 6.12和MIUI得到这个结果，欢迎大家使用各种版本测试） </li>    <li>你要拥有一个VPS或者购买Puff的SSH服务（已经购买Puff的SSH服务的请直接跳到第二步）</li> </ol>其实VPS这个东西嘛，也不算贵，<a href="https://hellohost.net/members/aff.php?aff=024">在这里</a>最便宜的只要19块大洋一个月，149可以买一年（你可以先买一个月试试）。根据我的<strong>猜测</strong>，一个64MB内存的VPS足够使用了（欢迎反驳）。 惯例，我的教程，都要先表明思路：  <ol>
<li>在VPS上用nginx架设反向代理（架设端口8087） </li>    <li>（其实完成上一步也就差不多了，但是咱的GFW有深度包检测呢，所以要给手机与VPS之间的连接带个套套，这样才安全嘛。本文重点就是教你如何带套） </li>    <li>ConnectBot用SSH连接到VPS，用端口转发，把VPS上的8087端口映射为手机上的8080端口 </li>    <li>设置手机，使用127.0.0.1:8080作为代理。</li> </ol>以下教程仍然以我正在用的CentOS举例。Ubuntu我根本就不会用！（捂脸）  <h4>一、部署nginx</h4>  先安装nginx（已经安装了的可以跳过这一步）  
{% codeblock %}
   yum install nginx 
{% endcodeblock %}
  以上命令我没测试过哦，我用的是编译安装。如果安装不成功，请大家自行Google“<a href="http://www.google.com.hk/search?sourceid=chrome&ie=UTF-8&q=nginx+%E5%AE%89%E8%A3%85">nginx 安装</a>” <img alt=":-D" src="https://psblog.name/wp-includes/images/smilies/icon_biggrin.gif"> 。如果你的VPS内存比较小且不放置PHP程序，建议把php-cgi进程杀掉。  
{% codeblock %}
   yum install nginx 
{% endcodeblock %}
  在nginx.conf里http{}段加入如下内容（咦？制表符显示不出来啊？）：  
{% codeblock %}
   yum install nginx 
{% endcodeblock %}
  为了安全，强烈建议把以上的8087端口改为其他。 保存，然后重启nginx  
{% codeblock %}
   yum install nginx 
{% endcodeblock %}
  <h4>二、连接SSH服务器</h4>  这一步有两种方法。一是使用ConnectBot，从我的测试结果来看，该方法比较稳定；二是使用max.c.lv开发的<a href="http://code.google.com/p/sshtunnel/">SSH Tunnel</a>，其主要源码来自ConnectBot，使用较方便，但是貌似不是很稳定（至少在我的机子上是这样）……  
{% codeblock %}
   yum install nginx 
{% endcodeblock %}
  
{% codeblock %}
   yum install nginx 
{% endcodeblock %}
  <h4>三、设置代理</h4>  如果你用的是SSH Tunnel且Root过且勾选了某个选项，那么就可以跳过这一步了。  在菜市场里面下载【Droid Proxy】。CM系列ROM和MIUI（这个好像也是CM的？）不用下载，系统自带代理设置。  主机名填写127.0.0.1，端口填写8080，保存。用Chrome Lite可以上YouTube了！  <h4>四、思考</h4>  刚才貌似看到有一个app可以设置全局代理……测试之后我发上来。  <h5>PS 强制推荐了你不喜欢的文章，请猛击后留言鄙视</h5>
