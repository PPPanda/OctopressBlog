--- 
categories: 
  - internet
comments: true
layout: post
published: true
status: publish
tags: 
  - tinymce
  - wordpress
  - wp
title: "wordpress-3.1.1 版本来了"
type: post
---
2011 年 4 月 5 日，我们发布了 WordPress 3.1.1。<a title="Version 3.1.1" href="http://codex.wordpress.org/Version_3.1.1">3.1.1 版本</a>的数据库版本号（<strong>wp_options</strong> 中的 <strong>db_version</strong>）已改为 17516。这是一个包含安全修补的修订版本。

<a id=".E5.AE.89.E8.A3.85.E5.92.8C.E5.8D.87.E7.BA.A7.E4.BF.A1.E6.81.AF" name=".E5.AE.89.E8.A3.85.E5.92.8C.E5.8D.87.E7.BA.A7.E4.BF.A1.E6.81.AF"></a>
<h2>安装和升级信息</h2>
要下载中文版本的 3.1.1 请访问：<a title="http://cn.wordpress.org/releases/" href="http://cn.wordpress.org/releases/">http://cn.wordpress.org/releases/</a>

详细的安装、升级步骤：
<ul>
<li>
<a title="zh-cn:升级WordPress" href="http://codex.wordpress.org/zh-cn:%E5%8D%87%E7%BA%A7WordPress">zh-cn:升级WordPress</a>（中文，但翻译需要完善）</li>
</ul>
如果您是新手，我们推荐您查看：
<ul>
<li>
<a title="zh-cn:WordPress 新手 - 如何开始" href="http://codex.wordpress.org/zh-cn:WordPress_%E6%96%B0%E6%89%8B_-_%E5%A6%82%E4%BD%95%E5%BC%80%E5%A7%8B">zh-cn:WordPress_新手_-_如何开始</a>（中文，但翻译需要完善）</li>
	<li>
<a title="First Steps With WordPress" href="http://codex.wordpress.org/First_Steps_With_WordPress">First Steps With WordPress</a>（英文）或 <a title="zh-cn:升级 WordPress 进阶" href="http://codex.wordpress.org/zh-cn:%E5%8D%87%E7%BA%A7_WordPress_%E8%BF%9B%E9%98%B6">zh-cn:升级_WordPress_进阶</a>（中文，但翻译需要完善）</li>
	<li>
<a title="WordPress Lessons" href="http://codex.wordpress.org/WordPress_Lessons">WordPress Lessons</a>（英文）</li>
</ul>
<a id=".E6.A6.82.E5.86.B5" name=".E6.A6.82.E5.86.B5"></a>
<h2>概况</h2>
<ul>
<li>加强媒体上传功能（<a title="http://core.trac.wordpress.org/changeset/17569" href="http://core.trac.wordpress.org/changeset/17569">r17569</a>，英文）</li>
	<li>避免了复杂超级链接可能造成 PHP 崩溃的问题（<a title="http://core.trac.wordpress.org/ticket/16892" href="http://core.trac.wordpress.org/ticket/16892">#16892</a>，英文）</li>
	<li>修正了一个数据库升级页面并不严重的 XSS 漏洞（<a title="http://core.trac.wordpress.org/changeset/17583" href="http://core.trac.wordpress.org/changeset/17583">r17583</a>，英文）</li>
	<li>修正了 26 个工单提及的问题。这些问题的细目表可以在 <a title="http://core.trac.wordpress.org/milestone/3.1.1" href="http://core.trac.wordpress.org/milestone/3.1.1">Trac</a> 找到。</li>
</ul>
<a id=".E7.9B.B8.E6.AF.94_3.1_.E7.89.88.E6.9C.AC.E4.BF.AE.E6.94.B9.E7.9A.84.E6.96.87.E4.BB.B6" name=".E7.9B.B8.E6.AF.94_3.1_.E7.89.88.E6.9C.AC.E4.BF.AE.E6.94.B9.E7.9A.84.E6.96.87.E4.BB.B6"></a>
<h2>相比 3.1 版本修改的文件</h2>
英文版本：

{% codeblock %}
wp-includes/admin-bar.php
wp-includes/taxonomy.php
wp-includes/post.php
wp-includes/version.php
wp-includes/js/tinymce/tiny_mce.js
wp-includes/js/tinymce/wp-tinymce.js.gz
wp-includes/functions.php
wp-includes/query.php
wp-includes/link-template.php
wp-includes/wp-db.php
wp-includes/formatting.php
wp-includes/rewrite.php
wp-includes/canonical.php
wp-includes/css/admin-bar.css
wp-includes/css/admin-bar.dev.css
wp-includes/script-loader.php
wp-includes/meta.php
readme.html
wp-admin/network.php
wp-admin/includes/class-wp-ms-sites-list-table.php
wp-admin/includes/dashboard.php
wp-admin/includes/class-wp-upgrader.php
wp-admin/includes/update-core.php
wp-admin/includes/media.php
wp-admin/media-upload.php
wp-admin/network/settings.php
wp-admin/network/admin.php
wp-admin/upgrade.php
wp-admin/user/admin.php
{% endcodeblock %}

中文版本额外修改：

{% codeblock %}
wp-includes/admin-bar.php
wp-includes/taxonomy.php
wp-includes/post.php
wp-includes/version.php
wp-includes/js/tinymce/tiny_mce.js
wp-includes/js/tinymce/wp-tinymce.js.gz
wp-includes/functions.php
wp-includes/query.php
wp-includes/link-template.php
wp-includes/wp-db.php
wp-includes/formatting.php
wp-includes/rewrite.php
wp-includes/canonical.php
wp-includes/css/admin-bar.css
wp-includes/css/admin-bar.dev.css
wp-includes/script-loader.php
wp-includes/meta.php
readme.html
wp-admin/network.php
wp-admin/includes/class-wp-ms-sites-list-table.php
wp-admin/includes/dashboard.php
wp-admin/includes/class-wp-upgrader.php
wp-admin/includes/update-core.php
wp-admin/includes/media.php
wp-admin/media-upload.php
wp-admin/network/settings.php
wp-admin/network/admin.php
wp-admin/upgrade.php
wp-admin/user/admin.php
{% endcodeblock %}


{% codeblock %}
wp-includes/admin-bar.php
wp-includes/taxonomy.php
wp-includes/post.php
wp-includes/version.php
wp-includes/js/tinymce/tiny_mce.js
wp-includes/js/tinymce/wp-tinymce.js.gz
wp-includes/functions.php
wp-includes/query.php
wp-includes/link-template.php
wp-includes/wp-db.php
wp-includes/formatting.php
wp-includes/rewrite.php
wp-includes/canonical.php
wp-includes/css/admin-bar.css
wp-includes/css/admin-bar.dev.css
wp-includes/script-loader.php
wp-includes/meta.php
readme.html
wp-admin/network.php
wp-admin/includes/class-wp-ms-sites-list-table.php
wp-admin/includes/dashboard.php
wp-admin/includes/class-wp-upgrader.php
wp-admin/includes/update-core.php
wp-admin/includes/media.php
wp-admin/media-upload.php
wp-admin/network/settings.php
wp-admin/network/admin.php
wp-admin/upgrade.php
wp-admin/user/admin.php
{% endcodeblock %}
