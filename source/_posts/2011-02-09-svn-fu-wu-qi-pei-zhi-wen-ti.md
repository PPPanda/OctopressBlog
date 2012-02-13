--- 
categories: 
  - SVN
comments: true
layout: post
published: true
status: publish
tags: 
  - chmod
  - code
  - General
  - ie
  - nginx
  - OS
  - server
  - shell
  - SVN
  - User
  - Username
  - web
  - win
  - 乌班图
  - 分类
  - 同步
  - 密码
  - 教程
  - update
  - 浏览器
title: SVN服务器配置问题
type: post
---
<div><span class="Apple-style-span"><span class="Apple-style-span"><div class="postbody"><span class="Apple-style-span"><span class="Apple-style-span">按照教程：<br>我的SVN服务跑起来了，在win7上也可以访问了，update,commit 也对，但是我看SVN目录的时候只能看到<br><div class="codetitle"><b>代码:</b></div>
<div class="codecontent">drwxrwsrwx 2 root subversion 4096 2010-06-18 16:21 conf<br>drwxrwsrwx 6 root subversion 4096 2010-06-18 18:33 db<br>-rwxrwxrwx 1 root subversion    2 2010-06-18 16:21 format<br>drwxrwsrwx 2 root subversion 4096 2010-06-18 16:21 hooks<br>drwxrwsrwx 2 root subversion 4096 2010-06-18 16:21 locks<br>-rwxrwxrwx 1 root subversion  229 2010-06-18 16:21 README.txt<br>
</div>
<br>我怎么在web浏览器里看到我修改后的项目啊？我更新之后的数据那里去了？我原来是想直接对我的www项目进行管理呢，结果我把www给做成svn项目目录了，www算是废掉了，在浏览器下只能看到下面这些东西了，我怎么才能通过浏览器直接访问我的项目呢？求助，SVN这个东西服务端要怎么配置啊？<br><br>我服务器用的nginx！svn就用的svnserve跑的服务。<br><div class="codetitle"><b>代码:</b></div>
<div class="codecontent">Index of /<br><br>--------------------------------------------------------------------------------<br><br>../<br>conf/                                              18-Jun-2010 16:21       -<br>db/                                                18-Jun-2010 18:33       -<br>hooks/                                             18-Jun-2010 16:21       -<br>locks/                                             18-Jun-2010 16:21       -<br>README.txt                                         18-Jun-2010 16:21     229<br>format                                             18-Jun-2010 16:21       2<br><br><br>--------------------------------------------------------------------------------<br>
</div>
<br><br><div class="quotetitle"><b>引用:</b></div>
<div class="quotecontent">一、SVN安装<br>1.安装包<br>$ sudo apt-get install subversion<br><br>2.添加svn管理用户及subversion组<br>$ sudo adduser svnuser<br>$ sudo addgroup subversion<br>$ sudo addgroup svnuser subversion<span class="Apple-converted-space"> </span><br><br>3.创建项目目录<br>$ sudo mkdir /home/svn<br>$ cd /home/svn<br>$ sudo mkdir fitness<br>$ sudo chown -R root:subversion fitness<br>$ sudo chmod -R g+rws fitness<br><br>4.创建SVN文件仓库<br>$ sudo svnadmin create /home/svn/fitness<br><br>5.访问方式及项目导入：<br>$ svn co file:///home/svn/fitness<br>或者<br>$ svn co<span class="Apple-converted-space"> </span><a class="postlink" href="///home/svn/fitness">file://localhost/home/svn/fitness</a><br>* 注意：<br>如果您并不确定主机的名称，您必须使用三个斜杠(///)，而如果您指定了主机的名称，则您必须使用两个斜杠(//).<br>//--<br>下面的命令用于将项目导入到SVN 文件仓库：<br>$ svn import -m "New import" /home/svn/fitness file:///home/svnuser/src/fitness<br>一定要注明导入信息<br><br>//--------------------------//<br>6.访问权限设置<br>修改 /home/svn/fitness目录下：<br>svnserve.conf 、passwd 、authz三个文件,行最前端不允许有空格<br>//--<br>编辑svnserve.conf文件,把如下两行取消注释<br>password-db = password<br>authz-db = authz<br><br>//补充说明<br># [general]<br>anon-access = read<br>auth-access = write<br>password-db = passwd<br>其中 anon-access 和 auth-access 分别为匿名和有权限用户的权限，默认给匿名用户只读的权限,但如果想拒绝匿<br><br>名用户的访问，只需把 read 改成 none 就能达到目的。<br><br>//--<br>编辑/home/svnuser/etc/passwd 如下:<br>[users]<br>mirze = 123456<br>test1 = 123456<br>test2 = 123456<br>//--<br>编辑/home/svnuser/etc/authz如下<br>[groups]<br>admin = mirze,test1<br>test = test2<br>[/]<br>@admin=rw<br>*=r<br>这里设置了三个用户mirze,test1,test2密码都是123456<br>其中mirze和test1属于admin组，有读和写的权限,test2属于test组只有读的权限<br><br>7.启动SVN服务<br>svnserve -d -r /home/svn<br>描述说明：<br>-d 表示svnserver以“守护”进程模式运行<br>-r 指定文件系统的根位置（版本库的根目录），这样客户端不用输入全路径，就可以访问版本库<br>如:<span class="Apple-converted-space"> </span><a class="postlink" href="svn://192.168.12.118/fitness">svn://192.168.12.118/fitness</a><br><br>这时SVN安装就完成了.<br>局域网访问方式：<br>例如：svn checkout<span class="Apple-converted-space"> </span><a class="postlink" href="svn://192.168.12.118/fitness">svn://192.168.12.118/fitness</a><span class="Apple-converted-space"> </span>--username mirze --password 123456 /var/www/fitness</div></span></span></div>
<div class="postbody"> </div>
<div class="postbody"><span class="Apple-style-span"><span class="Apple-style-span">SVN服務啟動關閉命令<br><div class="codetitle"><b>代码:</b></div>
<div class="codecontent">we@ubuntu:~$ svnserve -d -r /home/we/svn/<br>we@ubuntu:~$ ps -A<br>we@ubuntu:~$ kill 10000</div></span></span></div>
<div class="postbody"> </div>
<div class="postbody"> </div>
<div class="postbody">好吧，我找了一下午资料，找到解决方法了，果然求人不如求己！<span class="Apple-converted-space"> </span><img alt=":em20" src="%5CUsers%5CWe%5CAppData%5CLocal%5CTemp%5CWizHtmlEditor%5C78690648%5Cimages%5Csmilies%5Cem20.gif"><span class="Apple-converted-space"> </span><br><br><div class="codetitle"><b>代码:</b></div>
<div class="codecontent">Import: 將整個 project_directory 的資料 import 進 svn 裡面<br><br>svn import project_directory http://DOMAIN/svn_project<br>svn import project_directory file:///SVN_PATH/svn_project</div>
<br><br>先将整个项目目录导入SVN管理目录中。<br><br>然后SVN就会将project_directory 目录中的所有东西复制到SVN数据中svn_project分类中，这个project_directory 目录就可以删掉了。<br><br>然后就可以在本地使用<br><div class="codetitle"><b>代码:</b></div>
<div class="codecontent">Checkout: (checkout 可簡寫成 co), 將資料 checkout 回來<br><br>svn co http://SVN_PATH/svn_project<br>svn co file:///SVN_PATH/svn_project<br>svn co -r 12 file:///var/lib/svn/dev/projects # 出第12版的 projcets code</div>
<br><br>中途可以<br><div class="codetitle"><b>代码:</b></div>
<div class="codecontent">List: (list 可簡寫成 ls), 看上面有哪些檔案/資料<br><br>svn ls http://SVN_PATH/svn_project<br>svn ls file:///SVN_PATH/svn_project</div>
<br><br>再然后因为我的项目是放在www目录中，而www目录是我网站的根目录，我想让www目录中的代码自动跟SVN中的数据同步，这样的话可以每次更新之后运行 <div class="codetitle"><b>代码:</b></div>
<div class="codecontent">svn co svn://192.168.124.133/we --username zhou --password 123456<br>
</div>检出，但是这样很麻烦，每次都要自己检出，可以使用shell命令自动在每次提交之后自动检出，编辑 <div class="codetitle"><b>代码:</b></div>
<div class="codecontent">we@ubuntu:~/svn/hooks$ ls<br>post-commit               post-unlock.tmpl         pre-unlock.tmpl<br>post-commit.tmpl          pre-commit.tmpl          start-commit.tmpl<br>post-lock.tmpl            pre-lock.tmpl<br>post-revprop-change.tmpl  pre-revprop-change.tmpl<br>we@ubuntu:~/svn/hooks$ sudo nano post-commit<br>
</div>下的post-commit.tmpl文件，另存为post-commit，这样每次有数据提交就会自动执行里面的代码。我在里面写的是： <div class="codetitle"><b>代码:</b></div>
<div class="codecontent">#!/bin/sh<br><br>cd /home/we/www/<br>svn co svn://192.168.124.133/we --username zhou --password 123456<br>svn co svn://192.168.124.133/wp3-tw --username zhou --password 123456<br>cd<br>
</div>
<br><br>这样每次提交，我的we和wp3-tw项目就会自动更新。<br><br><span class="Apple-style-span"><span class="Apple-style-span"><div class="codetitle">刪除項目目錄的方法<strong></strong>
</div>
<div class="codetitle"><strong>代码:</strong></div>
<div class="codecontent">we@ubuntu:~$ svn list  svn://192.168.124.133/<br>project/<br>we/<br>wp28-zh/<br>wp3-tw/<br>we@ubuntu:~$ svn delete  svn://192.168.124.133/project/<br><br>Error reading /home/we/.nano_history: Permission denied<br><br>Press Enter to continue starting nano.<br><br><br>Log message unchanged or not specified<br>(a)bort, (c)ontinue, (e)dit:<br>c<br><br>Committed revision 26.<br>we@ubuntu:~$ svn list  svn://192.168.124.133/<br>we/<br>wp28-zh/<br>wp3-tw/<br>we@ubuntu:~$<br>
</div>
<br><br></span></span>
</div></span></span></div>
<div><a title="Wiz，个人知识管理，PKM。" href="http://wiz.cn">通过Wiz发布</a></div>
