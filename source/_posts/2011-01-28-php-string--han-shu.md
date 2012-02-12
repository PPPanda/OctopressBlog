--- 
categories: 
  - PHP
comments: true
layout: post
published: true
status: publish
tags: 
  - code
  - html
  - ie
  - OS
  - php
  - 数字
title: "PHP String 函数"
type: post
---
<h2>PHP String 函数</h2>
<div><ul class="prenext">
<li class="pre">
<a href="http://www.w3school.com.cn/php/php_ref_simplexml.asp">Previous Page</a>   </li>  <li class="next">
<a href="http://www.w3school.com.cn/php/php_ref_xml.asp">Next   Page</a> </li>
</ul></div>
<div>
<h2>PHP String 简介</h2>String 字符串函数允许您对字符串进行操作。</div>
<div>
<h2>安装</h2>String 函数是 PHP 核心的组成部分。无需安装即可使用这些函数。</div>
<div>
<h2>PHP String 函数</h2>
<span><strong>PHP：</strong></span>指示支持该函数的最早的 PHP 版本。<table class="dataintable"><tbody>
<tr>
<th>函数</th>    <th>描述</th>    <th>PHP</th>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_addcslashes.asp"><font color="#900b09">addcslashes()</font></a></td>    <td>在指定的字符前添加反斜杠。</td>    <td>4</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_addslashes.asp"><font color="#900b09">addslashes()</font></a></td>    <td>在指定的预定义字符前添加反斜杠。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_bin2hex.asp"><font color="#900b09">bin2hex()</font></a></td>    <td>把 ASCII 字符的字符串转换为十六进制值。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_chop.asp"><font color="#900b09">chop()</font></a></td>    <td>rtrim() 的别名。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_chr.asp"><font color="#900b09">chr()</font></a></td>    <td>从指定的 ASCII 值返回字符。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_chunk_split.asp"><font color="#900b09">chunk_split()</font></a></td>    <td>把字符串分割为一连串更小的部分。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_convert_cyr_string.asp"><font color="#900b09">convert_cyr_string()</font></a></td>    <td>把字符由一种 Cyrillic 字符转换成另一种。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_convert_uudecode.asp"><font color="#900b09">convert_uudecode()</font></a></td>    <td>对 uuencode 编码的字符串进行解码。</td>    <td>5</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_convert_uuencode.asp"><font color="#900b09">convert_uuencode()</font></a></td>    <td>使用 uuencode 算法对字符串进行编码。</td>    <td>5</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_count_chars.asp"><font color="#900b09">count_chars()</font></a></td>    <td>返回字符串所用字符的信息。</td>    <td>4</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_crc32.asp"><font color="#900b09">crc32()</font></a></td>    <td>计算一个字符串的 32-bit CRC。</td>    <td>4</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_crypt.asp"><font color="#900b09">crypt()</font></a></td>    <td>单向的字符串加密法 (hashing)。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_echo.asp"><font color="#900b09">echo()</font></a></td>    <td>输出字符串。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_explode.asp"><font color="#900b09">explode()</font></a></td>    <td>把字符串打散为数组。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_fprintf.asp"><font color="#900b09">fprintf()</font></a></td>    <td>把格式化的字符串写到指定的输出流。</td>    <td>5</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_get_html_translation_table.asp"><font color="#900b09">get_html_translation_table()</font></a></td>    <td>返回翻译表。</td>    <td>4</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_hebrev.asp"><font color="#900b09">hebrev()</font></a></td>    <td>把希伯来文本从右至左的流转换为左至右的流。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_hebrevc.asp"><font color="#900b09">hebrevc()</font></a></td>    <td>同上，同时把(\n) 转为 <br />。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_html_entity_decode.asp"><font color="#900b09">html_entity_decode()</font></a></td>    <td>把 HTML 实体转换为字符。</td>    <td>4</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_htmlentities.asp"><font color="#900b09">htmlentities()</font></a></td>    <td>把字符转换为 HTML 实体。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_htmlspecialchars_decode.asp"><font color="#900b09">htmlspecialchars_decode()</font></a></td>    <td>把一些预定义的 HTML 实体转换为字符。</td>    <td>5</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_htmlspecialchars.asp"><font color="#900b09">htmlspecialchars()</font></a></td>    <td>把一些预定义的字符转换为 HTML 实体。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_implode.asp"><font color="#900b09">implode()</font></a></td>    <td>把数组元素组合为一个字符串。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_join.asp"><font color="#900b09">join()</font></a></td>    <td>implode() 的别名。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_levenshtein.asp"><font color="#900b09">levenshtein()</font></a></td>    <td>返回两个字符串之间的 Levenshtein 距离。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_localeconv.asp"><font color="#900b09">localeconv()</font></a></td>    <td>返回包含本地数字及货币信息格式的数组。</td>    <td>4</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_ltrim.asp"><font color="#900b09">ltrim()</font></a></td>    <td>从字符串左侧删除空格或其他预定义字符。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_md5.asp"><font color="#900b09">md5()</font></a></td>    <td>计算字符串的 MD5 散列。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_md5_file.asp"><font color="#900b09">md5_file()</font></a></td>    <td>计算文件的 MD5 散列。</td>    <td>4</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_metaphone.asp"><font color="#900b09">metaphone()</font></a></td>    <td>计算字符串的 metaphone 键。</td>    <td>4</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_money_format.asp"><font color="#900b09">money_format()</font></a></td>    <td>把字符串格式化为货币字符串。</td>    <td>4</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_nl_langinfo.asp"><font color="#900b09">nl_langinfo()</font></a></td>    <td>返回指定的本地信息。</td>    <td>4</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_nl2br.asp"><font color="#900b09">nl2br()</font></a></td>    <td>在字符串中的每个新行之前插入 HTML 换行符。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_number_format.asp"><font color="#900b09">number_format()</font></a></td>    <td>通过千位分组来格式化数字。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_ord.asp"><font color="#900b09">ord()</font></a></td>    <td>返回字符串第一个字符的 ASCII 值。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_parse_str.asp"><font color="#900b09">parse_str()</font></a></td>    <td>把查询字符串解析到变量中。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_print.asp"><font color="#900b09">print()</font></a></td>    <td>输出一个或多个字符串。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_printf.asp"><font color="#900b09">printf()</font></a></td>    <td>输出格式化的字符串。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_quoted_printable_decode.asp"><font color="#900b09">quoted_printable_decode()</font></a></td>    <td>解码 quoted-printable 字符串。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_quotemeta.asp"><font color="#900b09">quotemeta()</font></a></td>    <td>在字符串中某些预定义的字符前添加反斜杠。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_rtrim.asp"><font color="#900b09">rtrim()</font></a></td>    <td>从字符串的末端开始删除空白字符或其他预定义字符。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_setlocale.asp"><font color="#900b09">setlocale()</font></a></td>    <td>设置地区信息（地域信息）。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_sha1.asp"><font color="#900b09">sha1()</font></a></td>    <td>计算字符串的 SHA-1 散列。</td>    <td>4</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_sha1_file.asp"><font color="#900b09">sha1_file()</font></a></td>    <td>计算文件的 SHA-1 散列。</td>    <td>4</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_similar_text.asp"><font color="#900b09">similar_text()</font></a></td>    <td>计算两个字符串的匹配字符的数目。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_soundex.asp"><font color="#900b09">soundex()</font></a></td>    <td>计算字符串的 soundex 键。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_sprintf.asp"><font color="#900b09">sprintf()</font></a></td>    <td>把格式化的字符串写写入一个变量中。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_sscanf.asp"><font color="#900b09">sscanf()</font></a></td>    <td>根据指定的格式解析来自一个字符串的输入。</td>    <td>4</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_str_ireplace.asp"><font color="#900b09">str_ireplace()</font></a></td>    <td>替换字符串中的一些字符。（对大小写不敏感）</td>    <td>5</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_str_pad.asp"><font color="#900b09">str_pad()</font></a></td>    <td>把字符串填充为新的长度。</td>    <td>4</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_str_repeat.asp"><font color="#900b09">str_repeat()</font></a></td>    <td>把字符串重复指定的次数。</td>    <td>4</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_str_replace.asp"><font color="#900b09">str_replace()</font></a></td>    <td>替换字符串中的一些字符。（对大小写敏感）</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_str_rot13.asp"><font color="#900b09">str_rot13()</font></a></td>    <td>对字符串执行 ROT13 编码。</td>    <td>4</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_str_shuffle.asp"><font color="#900b09">str_shuffle()</font></a></td>    <td>随机地打乱字符串中的所有字符。</td>    <td>4</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_str_split.asp"><font color="#900b09">str_split()</font></a></td>    <td>把字符串分割到数组中。</td>    <td>5</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_str_word_count.asp"><font color="#900b09">str_word_count()</font></a></td>    <td>计算字符串中的单词数。</td>    <td>4</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_strcasecmp.asp"><font color="#900b09">strcasecmp()</font></a></td>    <td>比较两个字符串。（对大小写不敏感）</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_strchr.asp"><font color="#900b09">strchr()</font></a></td>    <td>搜索字符串在另一字符串中的第一次出现。strstr() 的别名</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_strcmp.asp"><font color="#900b09">strcmp()</font></a></td>    <td>比较两个字符串。（对大小写敏感）</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_strcoll.asp"><font color="#900b09">strcoll()</font></a></td>    <td>比较两个字符串（根据本地设置）。</td>    <td>4</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_strcspn.asp"><font color="#900b09">strcspn()</font></a></td>    <td>返回在找到任何指定的字符之前，在字符串查找的字符数。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_strip_tags.asp"><font color="#900b09">strip_tags()</font></a></td>    <td>剥去 HTML、XML 以及 PHP 的标签。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_stripcslashes.asp"><font color="#900b09">stripcslashes()</font></a></td>    <td>删除由 addcslashes() 函数添加的反斜杠。</td>    <td>4</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_stripslashes.asp"><font color="#900b09">stripslashes()</font></a></td>    <td>删除由 addslashes() 函数添加的反斜杠。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_stripos.asp"><font color="#900b09">stripos()</font></a></td>    <td>返回字符串在另一字符串中第一次出现的位置(大小写不敏感)</td>    <td>5</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_stristr.asp"><font color="#900b09">stristr()</font></a></td>    <td>查找字符串在另一字符串中第一次出现的位置(大小写不敏感)</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_strlen.asp"><font color="#900b09">strlen()</font></a></td>    <td>返回字符串的长度。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_strnatcasecmp.asp"><font color="#900b09">strnatcasecmp()</font></a></td>    <td>使用一种“自然”算法来比较两个字符串（对大小写不敏感）</td>    <td>4</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_strnatcmp.asp"><font color="#900b09">strnatcmp()</font></a></td>    <td>使用一种“自然”算法来比较两个字符串（对大小写敏感）</td>    <td>4</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_strncasecmp.asp"><font color="#900b09">strncasecmp()</font></a></td>    <td>前 n 个字符的字符串比较（对大小写不敏感）。</td>    <td>4</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_strncmp.asp"><font color="#900b09">strncmp()</font></a></td>    <td>前 n 个字符的字符串比较（对大小写敏感）。</td>    <td>4</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_strpbrk.asp"><font color="#900b09">strpbrk()</font></a></td>    <td>在字符串中搜索指定字符中的任意一个。</td>    <td>5</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_strpos.asp"><font color="#900b09">strpos()</font></a></td>    <td>返回字符串在另一字符串中首次出现的位置（对大小写敏感）</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_strrchr.asp"><font color="#900b09">strrchr()</font></a></td>    <td>查找字符串在另一个字符串中最后一次出现的位置。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_strrev.asp"><font color="#900b09">strrev()</font></a></td>    <td>反转字符串。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_strripos.asp"><font color="#900b09">strripos()</font></a></td>    <td>查找字符串在另一字符串中最后出现的位置(对大小写不敏感)</td>    <td>5</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_strrpos.asp"><font color="#900b09">strrpos()</font></a></td>    <td>查找字符串在另一字符串中最后出现的位置(对大小写敏感)</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_strspn.asp"><font color="#900b09">strspn()</font></a></td>    <td>返回在字符串中包含的特定字符的数目。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_strstr.asp"><font color="#900b09">strstr()</font></a></td>    <td>搜索字符串在另一字符串中的首次出现（对大小写敏感）</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_strtok.asp"><font color="#900b09">strtok()</font></a></td>    <td>把字符串分割为更小的字符串。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_strtolower.asp"><font color="#900b09">strtolower()</font></a></td>    <td>把字符串转换为小写。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_strtoupper.asp"><font color="#900b09">strtoupper()</font></a></td>    <td>把字符串转换为大写。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_strtr.asp"><font color="#900b09">strtr()</font></a></td>    <td>转换字符串中特定的字符。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_substr.asp"><font color="#900b09">substr()</font></a></td>    <td>返回字符串的一部分。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_substr_compare.asp"><font color="#900b09">substr_compare()</font></a></td>    <td>从指定的开始长度比较两个字符串。</td>    <td>5</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_substr_count.asp"><font color="#900b09">substr_count()</font></a></td>    <td>计算子串在字符串中出现的次数。</td>    <td>4</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_substr_replace.asp"><font color="#900b09">substr_replace()</font></a></td>    <td>把字符串的一部分替换为另一个字符串。</td>    <td>4</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_trim.asp"><font color="#900b09">trim()</font></a></td>    <td>从字符串的两端删除空白字符和其他预定义字符。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_ucfirst.asp"><font color="#900b09">ucfirst()</font></a></td>    <td>把字符串中的首字符转换为大写。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_ucwords.asp"><font color="#900b09">ucwords()</font></a></td>    <td>把字符串中每个单词的首字符转换为大写。</td>    <td>3</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_vfprintf.asp"><font color="#900b09">vfprintf()</font></a></td>    <td>把格式化的字符串写到指定的输出流。</td>    <td>5</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_vprintf.asp"><font color="#900b09">vprintf()</font></a></td>    <td>输出格式化的字符串。</td>    <td>4</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_vsprintf.asp"><font color="#900b09">vsprintf()</font></a></td>    <td>把格式化字符串写入变量中。</td>    <td>4</td>
</tr>
<tr>
<td><a href="http://www.w3school.com.cn/php/func_string_wordwrap.asp"><font color="#900b09">wordwrap()</font></a></td>    <td>按照指定长度对字符串进行折行处理。</td>    <td>4</td>
</tr>
</tbody></table>
</div>
<div>
<h2>PHP String 常量</h2>
<span><strong>PHP：</strong></span>指示支持该常量的最早的 PHP 版本。<table class="dataintable"><tbody>
<tr>
<th>常量</th>    <th>描述</th>    <th>PHP</th>
</tr>
<tr>
<td>CRYPT_SALT_LENGTH</td>    <td>包含系统默认加密方法的长度。对于标准 DES 加密，长度是 2。</td>    <td> </td>
</tr>
<tr>
<td>CRYPT_STD_DES</td>    <td>如果支持 2 字符 salt 的 DES 加密，则设置为 1，否则为 0。</td>    <td> </td>
</tr>
<tr>
<td>CRYPT_EXT_DES</td>    <td>如果支持 9 字符 salt 的 DES 加密，则设置为 1，否则为 0。</td>    <td> </td>
</tr>
<tr>
<td>CRYPT_MD5</td>    <td>如果支持以$1$开始的 12 字符 salt 的MD5加密，则设置为1，否则为0。</td>    <td> </td>
</tr>
<tr>
<td>CRYPT_BLOWFISH</td>    <td>如果支持以 $2$ 或 $2a$ 开始的 16 字符 salt 的 Blowfish 加密，则设置为 1，否则为 0。</td>    <td> </td>
</tr>
<tr>
<td>HTML_SPECIALCHARS</td>    <td> </td>    <td> </td>
</tr>
<tr>
<td>HTML_ENTITIES</td>    <td> </td>    <td> </td>
</tr>
<tr>
<td>ENT_COMPAT</td>    <td> </td>    <td> </td>
</tr>
<tr>
<td>ENT_QUOTES</td>    <td> </td>    <td> </td>
</tr>
<tr>
<td>ENT_NOQUOTES</td>    <td> </td>    <td> </td>
</tr>
<tr>
<td>CHAR_MAX</td>    <td> </td>    <td> </td>
</tr>
<tr>
<td>LC_CTYPE</td>    <td> </td>    <td> </td>
</tr>
<tr>
<td>LC_NUMERIC</td>    <td> </td>    <td> </td>
</tr>
<tr>
<td>LC_TIME</td>    <td> </td>    <td> </td>
</tr>
<tr>
<td>LC_COLLATE</td>    <td> </td>    <td> </td>
</tr>
<tr>
<td>LC_MONETARY</td>    <td> </td>    <td> </td>
</tr>
<tr>
<td>LC_ALL</td>    <td> </td>    <td> </td>
</tr>
<tr>
<td>LC_MESSAGES</td>    <td> </td>    <td> </td>
</tr>
<tr>
<td>STR_PAD_LEFT</td>    <td> </td>    <td> </td>
</tr>
<tr>
<td>STR_PAD_RIGHT</td>    <td> </td>    <td> </td>
</tr>
<tr>
<td>STR_PAD_BOTH</td>    <td> </td>    <td> </td>
</tr>
</tbody></table>
</div>
<div><ul class="prenext">
<li class="pre">
<a href="http://www.w3school.com.cn/php/php_ref_simplexml.asp">Previous Page</a>   </li>  <li class="next">
<a href="http://www.w3school.com.cn/php/php_ref_xml.asp">Next   Page</a> </li>
</ul></div>
<div><a title="Wiz，个人知识管理，PKM。" href="http://wiz.cn">通过Wiz发布</a></div>
