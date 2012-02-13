--- 
categories: 
  - SVN
comments: true
layout: post
published: true
status: publish
tags: 
  - apache
  - Asia
  - cat
  - chmod
  - ie
  - Linux
  - OS
  - php
  - server
  - SVN
  - 乌班图
  - 同步
title: "SVN 遇到的一些问题"
type: post
---
<div>
<span class="Apple-style-span"><span class="Apple-style-span">SVN 遇到的一些问题 因为同样的告警，产生的原因会有很多，所以以下问题解决方案，仅供参考。一：Can't open file '/home/svn/develop/db/txn-current-lock': Permission denied此问题产生，是在commit一个问题时产生的。原因就是对仓库下的文件或文件夹，没有写权限。<br>解决办法，例； chmod 777 -R /home/svn/develop 当然这不是好的解决方法。最好是将apache用户(也就是svn的http管理用户)成为该目录的拥有者。chown -R apache:apache /home/svn/develop 前提是你有这个用户和组<br>二:认证失败svnsync init svn://localhost/develop https://svn.asianux.net/develop<br>提示错误为：认证失败网上得出结论，将源地址的两个认证文件拷贝到目的地址就可以了，可是竟然没把哪两个文件名写出来。我猜测是工程文件下的 conf/authz 和 conf/passwd. 由于时间问题，换了下面命令svnsync init file:///home/svn/develop https://svn.asianux.net/develop<br>我用的这种。第二个命令，我这里也会报出错误。做了如下修改后通过。<br>cd $(工程目录)/hooks<br>cp pre-revprop-change.tmpl pre-revprop-change<br>chmod 755 pre-revprop-change<br>vim pre-revprop-change<br>＃注释掉如下三行<br>#if [ "$ACTION" = "M" -a "$PROPNAME" = "svn:log" ]; then exit 0; fi<br>#echo "Changing revision properties other than svn:log is prohibited" >&2<br>#exit 1<br>#同时添加一行<br>exit 0三：svnsync sync同步时的路径<br>svnsync sync file:////home/svn/develop<span class="Apple-converted-space"> </span><br>注意，后者为绝对路径 /home/svn/develop四：405 Method Not Allowed<br>当然，这个只可能是许多这种问题中其中的一个解决办法<br>错误：<br>svn: 服务器发送了意外的返回值(405 Method Not Allowed)，在响应 “PROPFIND” 的请求 “/develop” 中<br>原因：<br>配置时，没有将对应的目录加入到apache的配置文件中。apache说了:不和我说，你也别想被人搜到。<br>好了，看下下面的文件-----ubuntu 9.04------------------------------------------<br>/etc/httpd/conf.d/subversion.conf<br>打开文件，有如下两行：<br>SVNParentPath /home/svn<br>AuthzSVNAccessFile /home/svn/etc/svn-auth-file<br>那么我们就打开 /home/svn/etc/svn-auth-file文件。增加如下内容<br>[develop:/]<br>* = wr<br>不用我详细说明了吧, wr 就是read and write 登录下看看<br>注意：这里输入地址时为： http://$(ip/domain)/svn/develop--------服务器 系统为：Everest Linux 0.5pre2--------------<br>/etc/httpd/conf.d/subversion.conf<br>其他一样了五：访问server的路径<br>如我的ip为192.168.0.129 按照上面3.3 则应该输入 http://192.168.0.129/svn/develop 而不是http://192.168.0.129/develop六：访问仓库根目录<br>解决方法<br>一、首先，Subversion1.3及以后版本支持SVNListParentPath ON，之前的版本只能使用PHP自己做。<br>二、Location 设置中最后要加上/，应该是<Location /svn/>而不是<Location /svn>否则可能不能访问。<br>三、通过“http://localhost/svn/” 来访问仓库列表，如果想让“http://localhost/svn”也起作用的话，需要在</Location>的后面增加重定向的设 置：RedirectMatch ^(/svn)$ $1/ ，当然也可以采用RewriteEngine之类的办法。</span></span><!--WizHtmlContent-->
</div>
<div><a title="Wiz，个人知识管理，PKM。" href="http://wiz.cn">通过Wiz发布</a></div>
