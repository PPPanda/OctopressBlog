---
layout: post
title: "关于CI放在二级路径下面，URL下面带二级目录的时候全部页面404的问题"
date: 2012-03-29 15:23
comments: true
categories: 
  - php
tags: 
  - php
  - ci
  - CodeIgniter
---

今天心血来潮下了最新版的CI框架，想研究一下它的URI跳转是怎么做的，没想到搭建起来之后访问任何地址全部都是404。仔细研究后发现，原来是CI不支持二级目录的URL路径，例如：http://localhost/CodeIgniter_2.1.0_1/，CI 就会以为 CodeIgniter_2.1.0_1 是控制器，然后就去 controllers 目录里去找，但事实上那个是二级目录。

这个问题我有提交到[CI论坛](http://codeigniter.org.cn/forums/thread-12167-1-1.html)，不知道算不算一个BUG。


以下是解决方法：
1.首先在CI根目录添加了一个.htaccess 文件，内容是这样：

{% codeblock %}
RewriteEngine On
RewriteBase /CodeIgniter_2.1.0_1/
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)$ /CodeIgniter_2.1.0_1/index.php?/$1 [L]
{% endcodeblock %}


修改了 system/core/URI.php 文件的 _set_uri_string 函数和 _explode_segments 函数
{% codeblock %}

    /**
     * Set the URI String
     *
     * @access  public
     * @param   string
     * @return  string
     */
    function _set_uri_string($str) {
        if ($this->config->item("base_folder")) {
            if ($str == $this->config->item("base_folder")) {
                $str = "";
            }
        }
 
        // Filter out control characters        
        $str = remove_invisible_characters($str, FALSE);
 
        // If the URI contains only a slash we'll kill it
        $this->uri_string = ($str == '/') ? '' : $str;
    }
 
 
    /**
     * Explode the URI Segments. The individual segments will
     * be stored in the $this->segments array.
     *
     * @access  private
     * @return  void
     */
    function _explode_segments() {
        $is_ignored = FALSE;
        foreach (explode("/", preg_replace("|/*(.+?)/*$|", "\1", $this->uri_string)) as $val) {
            // Filter segments for security
            $val = trim($this->_filter_uri($val));
 
            if ($val != '') {
                if (!$is_ignored && $this->config->item("base_folder")) {
                    if ($val == $this->config->item("base_folder")) {
                        $is_ignored = TRUE;
                        continue;
                    }
                }
                $this->segments[] = $val;
            }
        }
    }

{% endcodeblock %}


在 application/config/config.php 里面增加了配置：

{% codeblock %}
$config['base_folder']  = 'CodeIgniter_2.1.0_1';
{% endcodeblock %}


OK，现在就可以运行了。