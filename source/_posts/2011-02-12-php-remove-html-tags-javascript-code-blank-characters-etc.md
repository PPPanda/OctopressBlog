--- 
categories: 
  - PHP
comments: true
layout: post
published: true
status: publish
tags: 
  - html
  - ie
  - java
  - JavaScript
  - php
  - 去掉
  - 空白字符
title: "PHP去掉 HTML标记、javascript 代码、空白字符等"
type: post
---
{% codeblock %}

preg_replace("'([\r\n])[\s]+'", "", $content) //去除回车换行符


{% codeblock %}


// $document 应包含一个 HTML 文档。

// 本例将去掉 HTML 标记，javascript 代码

// 和空白字符。还会将一些通用的

// HTML 实体转换成相应的文本。

$search = array ("'<script>]*?>.*?</script>'si",  // 去掉 javascript

"']*?>'si",           // 去掉 HTML 标记

"'([\r\n])[\s]+'",                 // 去掉空白字符

"'&(quot|#34);'i",                 // 替换 HTML 实体

"'&(amp|#38);'i",

"'&(lt|#60);'i",

"'&(gt|#62);'i",

"'&(nbsp|#160);'i",

"'&(iexcl|#161);'i",

"'&(cent|#162);'i",

"'&(pound|#163);'i",

"'&(copy|#169);'i",

"'(\d+);'e");                    // 作为 PHP 代码运行

$replace = array ("",

"",

"

// $document 应包含一个 HTML 文档。

// 本例将去掉 HTML 标记，javascript 代码

// 和空白字符。还会将一些通用的

// HTML 实体转换成相应的文本。

$search = array ("'<script>]*?>.*?</script>'si",  // 去掉 javascript

"']*?>'si",           // 去掉 HTML 标记

"'([\r\n])[\s]+'",                 // 去掉空白字符

"'&(quot|#34);'i",                 // 替换 HTML 实体

"'&(amp|#38);'i",

"'&(lt|#60);'i",

"'&(gt|#62);'i",

"'&(nbsp|#160);'i",

"'&(iexcl|#161);'i",

"'&(cent|#162);'i",

"'&(pound|#163);'i",

"'&(copy|#169);'i",

"'(\d+);'e");                    // 作为 PHP 代码运行

$replace = array ("",

"",

"\1",

"\"",

"&",

"",

" ",

chr(161),

chr(162),

chr(163),

chr(169),

"chr(\1)");

$text = preg_replace ($search, $replace, $document);

",

"\"",

"&",

"",

" ",

chr(161),

chr(162),

chr(163),

chr(169),

"chr(

// $document 应包含一个 HTML 文档。

// 本例将去掉 HTML 标记，javascript 代码

// 和空白字符。还会将一些通用的

// HTML 实体转换成相应的文本。

$search = array ("'<script>]*?>.*?</script>'si",  // 去掉 javascript

"']*?>'si",           // 去掉 HTML 标记

"'([\r\n])[\s]+'",                 // 去掉空白字符

"'&(quot|#34);'i",                 // 替换 HTML 实体

"'&(amp|#38);'i",

"'&(lt|#60);'i",

"'&(gt|#62);'i",

"'&(nbsp|#160);'i",

"'&(iexcl|#161);'i",

"'&(cent|#162);'i",

"'&(pound|#163);'i",

"'&(copy|#169);'i",

"'(\d+);'e");                    // 作为 PHP 代码运行

$replace = array ("",

"",

"\1",

"\"",

"&",

"",

" ",

chr(161),

chr(162),

chr(163),

chr(169),

"chr(\1)");

$text = preg_replace ($search, $replace, $document);

)");

$text = preg_replace ($search, $replace, $document);


{% endcodeblock %}


{% endcodeblock %}
 
