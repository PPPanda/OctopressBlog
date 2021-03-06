--- 
categories: 
  - SVN
comments: true
layout: post
published: true
status: publish
tags: 
  - "42"
  - apache
  - book
  - cat
  - chmod
  - General
  - hostname
  - ie
  - Linux
  - OS
  - server
  - ssh
  - SVN
  - User
  - Username
  - web
  - 乌班图
  - 分类
  - 同步
  - 在线
  - 密码
  - 数字
  - post
  - 计算机
  - 论坛
  - 软件
title: SubVersion
type: post
---
<div>SubVersion<br>目录<br>[隐藏]<br>1 SubVersion服务安装设置<br>1.1 简介<br>1.2 假设<br>1.3 本文涉及的范围<br>1.4 安装<br>1.5 服务器配置<br>1.5.1 创建 SVN 仓库<br>1.6 访问方式<br>1.6.1 直接访问文件仓库(file://)<br>1.6.2 通过 WebDAV 协议访问(http://)<!--more--><br>1.6.3 通过具有安全套接字(SSL)的 WebDAV 协议访问(https://)<br>1.6.4 通过自带协议访问(svn://)<br>1.6.5 通过具被SSH隧道保护的自带协议访问(svn+ssh://)<br>1.7 参考资料<br>[编辑] SubVersion服务安装设置<br>原文出处：https://wiki.ubuntu.com/SubVersion<br><div> </div>原文作者：ubuntu.com<br><div> </div>授权许可：创作共用协议<br><div> </div>翻译人员：XueCan<br><div> </div>校对人员：无<br><div> </div>适用版本：所有版本<br><div> </div>文章状态：翻译中<br><div> </div>本文档阐述了如何在 Ubuntu 上设置 Subversion（通常也被称为 svn）。我们假设本文的读者是具有一定经验的 Linux 用户和系统管理员。<br><div> </div>
<div> </div>[编辑] 简介<br>如果您对 Subversion 还比较陌生，本节将给您一个关于 Subversion 的简要介绍。<br><div> </div>Subversion 是一款开放源代码的版本控制系统。使用 Subversion，您可以重新加载源代码和文档的历史版本。Subversion 管理了源代码在各个时期的版本。一个文件树被集中放置在文件仓库中。这个文件仓库很像是一个传统的文件服务器，只不过它能够记住文件和目录的每一次变化。<br><div> </div>[编辑] 假设<br>首先我们假设您能够在 Ubuntu 中操作 Linux 的命令、编辑文件、启动和停止服务。当然，我们还认为您的 Ubuntu 正在运行中，您可以使用<br><div> </div>[编辑] 本文涉及的范围<br>要通过 HTTP 协议访问 SVN 文件仓库，您需要安装并配置好 Web 服务器。Apache 2 被证实可以很好的与 SVN 一起工作。关于 Apache 2 的安装超出了本文的范围，尽管如此，本文还是会涉及如何配置 Apache 2 使用 SVN。<br><div> </div>类似的，要通过 HTTPS 协议访问 SVN 文件仓库，您需要在您的 Apache 2 中安装并配置好数字证书，这也不在本文的讨论范围之中。<br><div> </div>[编辑] 安装<br>幸运的，Subversion 已经包含在 main 仓库中。所以，要安装 Subversion，您只需要简单的运行：<br><div> </div>$ sudo apt-get install subversion<br>$ sudo apt-get install libapache2-svn<br>如果系统报告了依赖关系的错误，请找出相应的软件包并安装它们。如果存在其它问题，也请自行解决。如果您是再不能解决这些问题，可以考虑通过 Ubuntu 的网站、Wiki、论坛或邮件列表寻求支持。<br><div> </div>[编辑] 服务器配置<br>您应该已经安装了上述的软件包。本节将阐述如何创建 SVN 文件仓库以及如何设置项目的访问权限。<br><div> </div>[编辑] 创建 SVN 仓库<br>许多位置都可以放置 Subversion 文件仓库，其中两个最常用的是：/usr/local/svn 以及 /home/svn。为了在下面的描述中简单明了，我们假设您的 Subversion 文件仓库放在 /home/svn，并且你的项目名称是简单的“myproject”。<br><div> </div>同样的，也有许多常用的方式设置文件仓库的访问权限。然而，这也是安装过程中最经常出现错误的地方，因此我们会对此进行一个详细说明。典型的情况下，您应该创建一个名为“Subversion”的组来拥有文件仓库所在的目录。下面是一个快速的操作说明，有关内容请参考相关文档的详细说明：<br><div> </div>在 Ubuntu 菜单上选择“系统->系统管理->用户和组”；<br>切换到“组”标签；<br>点击“添加组”按钮；<br>组名为“subversion”；<br>将您自己和“www-data”(Apache 用户)加入组成员中；<br>点击“OK”以确认修改，关闭该程序。<br>或者使用命令完成上述功能（增加组，并且把用户加到组里）：<br><div> </div>sudo addgroup subversion<br>sudo usermod -G subversion -a www-data<br>再或者直接使用命令编辑组文件"sudo vi /etc/group"，增加组和成员（不推荐）：<br><div> </div>$ sudo vi /etc/group<br>结果看上去，像这样。<br><div> </div>$ cat /etc/group|grep subversion<br>subversion:x:1001:www-data,exp<br>您需要注销然后再登录以便您能够成为 subversion 组的一员，然后就可以执行签入文件（Check in，也称提交文件）的操作了。<br><div> </div>现在执行下面的命令<br><div> </div>$ sudo mkdir /home/svn<br>$ cd /home/svn<br>$ sudo mkdir myproject<br>$ sudo chown -R root:subversion myproject<br>下面的命令用于创建 SVN 文件仓库：<br><div> </div>$ sudo svnadmin create /home/svn/myproject<br>赋予组成员对所有新加入文件仓库的文件拥有相应的权限：<br><div> </div>$ sudo chmod -R g+rws myproject<br>如果上面这个命令在创建SVN文件仓库之前运行，你可能在后续Check in的时候遇到如下错误：<br><div> </div>Can't open '/home/svn/myproject/db/txn-current-lock': Permission denied<br>查看txn-current-lock文件的权限和用户以及组信息，应该类似于：<br><div> </div>$ ls -l /home/svn/myproject/db/txn-current-lock<br>-rw-rwSr-- 1 root subversion 0 2009-06-18 15:33 txn-current-lock<br>除了权限以外，用户及其组如果不对，则仍然会遇到上述问题，可以再次运行命令：<br><div> </div>$ sudo chown -R root:subversion myproject<br>[编辑] 访问方式<br>Subversion 文件仓库可以通过许多不同的方式进行访问（Check Out，签出）——通过本地硬盘，或者通过各种网络协议。无论如何，文件仓库的位置总是使用 URL 来表示。下表显示了不同的 URL 模式对应的访问方法：<br><div> </div>模式    访问方法<br>file:///    直接访问本地硬盘上文件仓库<br>http://    通过 WebDAV 协议访问支持 Subversion 的 Apache 2 Web 服务器<br>https://    类似 http://，支持 SSL 加密<br>svn://    通过自带协议访问 svnserve 服务器<br>svn+ssh://    类似 svn://，支持通过 SSH 通道<br><div> </div>本节中，我们将看到如何配置 SVN 以使之能够通过所有的方法得以访问。当然这里我们之讨论基本的方法。要了解更高级的用途，我们推荐您阅读《使用 Subversion 进行版本控制》在线电子书。<br><div> </div>[编辑] 直接访问文件仓库(file://)<br>这是所有访问方式中最简单的。它不需要事先运行任何 SVN 服务。这种访问方式用于访问本地的 SVN 文件仓库。语法是：<br><div> </div>$ svn co file:///home/svn/myproject<br>或者<br>$ svn co file://localhost/home/svn/myproject<br>注意：如果您并不确定主机的名称，您必须使用三个斜杠(///)，而如果您指定了主机的名称，则您必须使用两个斜杠(//).<br><div> </div>对文件仓库的访问权限基于文件系统的权限。如果该用户具有读/写权限，那么他/她就可以签出/提交修改。如果您像前面我们说描述的那样设置了相应的组，您可以简单的将一个用户添加到“subversion”组中以使其具有签出和提交的权限。<br><div> </div>[编辑] 通过 WebDAV 协议访问(http://)<br>要通过 WebDAV 协议访问 SVN 文件仓库，您必须配置您的 Apache 2 Web 服务器。您必须加入下面的代码片段到您的 /etc/apache2/mods-available/dav_svn.conf中：<br><div> </div><Location /svn/myproject><br>DAV svn<br>SVNPath /home/svn/myproject<br>AuthType Basic<br>AuthName "myproject subversion repository"<br>AuthUserFile /etc/subversion/passwd<br><LimitExcept GET PROPFIND OPTIONS REPORT><br>Require valid-user<br></LimitExcept><br></Location><br>如果需要用户每次登录时都进行用户密码验证，请将<LimitExcept GET PROPFIND OPTIONS REPORT>与</LimitExcept>两行注释掉。<br><div> </div>当您添加了上面的内容，您必须重新起动 Apache 2 Web 服务器，请输入下面的命令：<br><div> </div>sudo /etc/init.d/apache2 restart<br>接下来，您需要创建 /etc/subversion/passwd 文件，该文件包含了用户授权的详细信息。要添加用户，您可以执行下面的命令：<br><div> </div>sudo htpasswd -c /etc/subversion/passwd user_name<br>它会提示您输入密码，当您输入了密码，该用户就建立了。“-c”选项表示创建新的/etc/subversion/passwd文件，所以user_name所指的用户将是文件中唯一的用户。如果要添加其他用户，则去掉“-c”选项即可：<br><div> </div>sudo htpasswd /etc/subversion/passwd other_user_name<br>您可以通过下面的命令来访问文件仓库：<br><div> </div>$ svn co http://hostname/svn/myproject myproject --username user_name<br>它会提示您输入密码。您必须输入您使用 htpasswd 设置的密码。当通过验证，项目的文件就被签出了。<br><div> </div>警告：密码是通过纯文本传输的。如果您担心密码泄漏的问题，我们建议您使用 SSL 加密，有关详情请看下一节。<br><div> </div>[编辑] 通过具有安全套接字(SSL)的 WebDAV 协议访问(https://)<br>通过具有 SSL 加密的 WebDAV 协议访问 SVN 文件仓库(https://)非常类似上节所述的内容，除了您必须为您的 Apache 2 Web 服务器设置数字证书之外。<br><div> </div>您可以安装由诸如 Verisign 发放的数字签名，或者您可以安装您自己的数字签名。<br><div> </div>我们假设您已经为 Apache 2 Web 服务器安装和配置好了相应的数字证书。现在按照上一节所描述的方法访问 SVN 文件仓库，别忘了把 http:// 换成 https://。如何，几乎是一模一样的！<br><div> </div>[编辑] 通过自带协议访问(svn://)<br>当您创建了 SVN 文件仓库，您可以修改 /home/svn/myproject/conf/svnserve.conf 来配置其访问控制。<br><div> </div>
<div> </div>例如，您可以取消下面的注释符号来设置授权机制：<br><div> </div># [general]<br># password-db = passwd<br>现在，您可以在“passwd”文件中维护用户清单。编辑同一目录下“passwd”文件，添加新用户。语法如下：<br><div> </div>username = password<br>＃(注意行开始不要有多余空格)<br>要了解详情，请参考该文件。<br><div> </div>
<div> </div>现在，您可以在本地或者远程通过 svn://访问 SVN 了，您可以使用“svnserve”来运行 svnserver，语法如下：<br><div> </div>$ svnserve -d --foreground -r /home/svn<br># -d -- daemon mode<br># --foreground -- run in foreground (useful for debugging)<br># -r -- root of directory to serve<br>要了解更多信息，请输入：<br>$ svnserve --help<br>当您执行了该命令，SVN 就开始监听默认的端口(3690)。您可以通过下面的命令来访问文件仓库：<br><div> </div>$ svn co svn://hostname/myproject myproject --username user_name<br>基于服务器的配置，它会要求输入密码。一旦通过验证，就会签出文件仓库中的代码。<br><div> </div>
<div> </div>要同步文件仓库和本地的副本，您可以执行 update 子命令，语法如下：<br><div> </div>$ cd project_dir<br>$ svn update<br>要了解更多的 SVN 子命令，您可以参考手册。例如要了解 co (checkout) 命令，请执行：<br><div> </div>$ svn co --help<br>或者这样<br>$ svn --help commit<br>或者直接<br>☎ svn help co<br>checkout (co): 从版本库签出工作副本。<br>使用: checkout URL[@REV]... [PATH]<br>。。。。。<br>一个实例：<br><div> </div>☎ killall svnserve; svnserve -d -r /home/svn/<br>/home/svn/lj12-source/conf ☎ dog *<br>authz:[groups]<br>authz:lj12 = veexp<br>authz:[lj12-source:/] <-注意写法。<br>authz:veexp = rw<br>authz:@lj12 = rw<br>authz:* = passwd:[users] <-2个用户和密码。<br>passwd:veexp = icep<br>passwd:test = test <br>svnserve.conf:[general]<br>svnserve.conf:anon-access = none<br>svnserve.conf:auth-access = write<br>svnserve.conf:password-db = passwd<br>svnserve.conf:authz-db = authz <-如果不启用authz，则test也可以取出。<br>☎ svn co svn://localhost/lj12-source --username veexp<br>认证领域: <svn://localhost:3690> a712643f-661e-0410-8ad4-f0554cd88977<br>用户名: veexp “veexp”的密码:<br>A lj12-source/tim.h A lj12-source/en.c<br>......<br>认证失败的密码缓冲记录位置，明文密码。到1.6版本，可能使用keyring管理。如果调试密码，直接删除如下文件就可。<br><div> </div>~/.subversion/auth/svn.simple/:<br><div> </div>eea34a6f7baa67a3639cacd6a428dba4<br>[编辑] 通过具被SSH隧道保护的自带协议访问(svn+ssh://)<br>配置和服务器进程于上节所述相同。我们假设您已经运行了“svnserve”命令。<br><div> </div>我们还假设您运行了 ssh 服务并允许接入。要验证这一点，请尝试使用 ssh 登录计算机。如果您可以登录，那么大功告成，如果不能，请在执行下面的步骤前解决它。<br><div> </div>svn+ssh:// 协议使用 SSH 加密来访问 SVN 文件仓库。如您所知，数据传输是加密的。要访问这样的文件仓库，请输入：<br><div> </div>$ svn co svn+ssh://hostname/home/svn/myproject myproject --username user_name<br>注意：在这种方式下，您必须使用完整的路径(/home/svn/myproject)来访问 SVN 文件仓库<br><div> </div>基于服务器的配置，它会要求输入密码。您必须输入您用于登录 ssh 的密码，一旦通过验证，就会签出文件仓库中的代码。<br><div> </div>您还应该参考 SVN book 以了解关于 svn+ssh:// 协议的详细信息。<br><div> </div>[编辑] 参考资料<br>Setting up Apache on Ubuntu<br>SVN Home page<br>SVN Book<br>Apache 2 Documentation<br>Mod-SSL<br>Apache-SSL<br>1个分类: 程序开发<br><!--WizHtmlContent-->
</div>
<div><a title="Wiz，个人知识管理，PKM。" href="http://wiz.cn">通过Wiz发布</a></div>
