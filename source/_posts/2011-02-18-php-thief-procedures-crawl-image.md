--- 
categories: 
  - PHP
comments: true
layout: post
published: true
status: publish
tags: 
  - php
  - 抓取图片
title: "php小偷程序[抓取图片]"
type: post
---
详见代码 <div class="cnblogs_code">
{% codeblock %}
<img id="Code_Closed_Image_40744" onclick="this.style.display='none'; document.getElementById('Code_Closed_Text_40744').style.display='none'; document.getElementById('Code_Open_Image_40744').style.display='inline'; document.getElementById('Code_Open_Text_40744').style.display='inline';" height="16" src="http://www.cnblogs.com/Images/OutliningIndicators/ContractedBlock.gif" width="11" align="top"><img id="Code_Open_Image_40744" style="display: none" onclick="this.style.display='none'; document.getElementById('Code_Open_Text_40744').style.display='none'; getElementById('Code_Closed_Image_40744').style.display='inline'; getElementById('Code_Closed_Text_40744').style.display='inline';" height="16" src="http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockStart.gif" width="11" align="top"><span class="cnblogs_code_Collapse" id="Code_Closed_Text_40744"></span><span id="Code_Open_Text_40744" style="display: none"><span style="color: #0000ff"><?</span>php
$id=$_GET["<span style="color: #8b0000">GroupID</span>"];
$disp=$_GET["<span style="color: #8b0000">disp</span>"];
$page=$_GET["<span style="color: #8b0000">PageNo</span>"];
<a style="color: #0000ff" href="http://www.php.net/if">if</a>(!$disp) {
    $cut='<span style="color: #8b0000"><table width="570" border="0" cellspacing="0" cellpadding="3"></span>';
    $cut2='<span style="color: #8b0000"><table width="770" height="31"  border="0" align="center" cellpadding="0" cellspacing="0"></span>';
    $url="<span style="color: #8b0000">http://www.6642.com/Index.asp?PageNo=$page&GroupID=$id</span>";
    $data =<a style="color: #ffa500" href="http://www.php.net/explode">explode</a>("<span style="color: #8b0000">$cut</span>",openu($url));
    $datat=<a style="color: #ffa500" href="http://www.php.net/explode">explode</a>("<span style="color: #8b0000">$cut2</span>",$data[3]);
    $chjia_com=<a style="color: #ffa500" href="http://www.php.net/str_replace">str_replace</a>("<span style="color: #8b0000">Image/newsbg.gif</span>","<span style="color: #8b0000">images/newsbg.gif</span>","<span style="color: #8b0000"><table border=0 width=100% cellspacing=0 cellpadding=0><tr align=center><td> $cut$data[1]$cut$data[2]$cut$datat[0]</span>");<span style="color: #008000">//</span>
    $chjia_com=<a style="color: #ffa500" href="http://www.php.net/str_replace">str_replace</a>('<span style="color: #8b0000"><img src="image/istop</span>','<span style="color: #8b0000"><img src="images/istop</span>',$chjia_com);
    $chjia_com=<a style="color: #ffa500" href="http://www.php.net/str_replace">str_replace</a>('<span style="color: #8b0000">href="disp/</span>','<span style="color: #8b0000">href="?disp=</span>',$chjia_com);
    $chjia_com=<a style="color: #ffa500" href="http://www.php.net/str_replace">str_replace</a>('<span style="color: #8b0000">href="Disp/</span>','<span style="color: #8b0000">href="?disp=</span>',$chjia_com);
    $chjia_com=<a style="color: #ffa500" href="http://www.php.net/str_replace">str_replace</a>('<span style="color: #8b0000">?disp=2028.htm</span>','<span style="color: #8b0000">http://www.chjia.com</span>',$chjia_com);
    $chjia_com=<a style="color: #ffa500" href="http://www.php.net/str_replace">str_replace</a>('<span style="color: #8b0000">?disp=121.htm</span>','<span style="color: #8b0000">http://mm.chjia.com/</span>',$chjia_com);
    
}<a style="color: #0000ff" href="http://www.php.net/else">else</a> {
    $cut='<span style="color: #8b0000"><table width="770" height="26" border="0" align="center" cellpadding="0" cellspacing="0"></span>';
    $cut2='<span style="color: #8b0000"><table width="770" height="55" border="0" align="center" cellPadding="0" cellSpacing="2"></span>';
    $url="<span style="color: #8b0000">http://www.6642.com/disp/$disp</span>";
    $data =<a style="color: #ffa500" href="http://www.php.net/explode">explode</a>("<span style="color: #8b0000">$cut</span>",openu($url));
    $datat=<a style="color: #ffa500" href="http://www.php.net/explode">explode</a>("<span style="color: #8b0000">$cut2</span>",$data[1]);
    $chjia_com=<a style="color: #ffa500" href="http://www.php.net/str_replace">str_replace</a>('<span style="color: #8b0000"><script language=javascript>document.write(ClickCount)</script></span>','<span style="color: #8b0000"><script>var uid=10361</script><script src=http://code.5k3g.com/tl/picDIY/float_right.js></script></span>',"<span style="color: #8b0000">$cut$datat[0]</span>");
}


<a style="color: #0000ff" href="http://www.php.net/function">function</a> openu($url) {
    $url = <a style="color: #ffa500" href="http://www.php.net/eregi_replace">eregi_replace</a>('<span style="color: #8b0000">^http://</span>', '<span style="color: #8b0000"></span>', $url);
    $temp = <a style="color: #ffa500" href="http://www.php.net/explode">explode</a>('<span style="color: #8b0000">/</span>', $url);
    $host = <a style="color: #ffa500" href="http://www.php.net/array_shift">array_shift</a>($temp);
    $path = '<span style="color: #8b0000">/</span>'.<a style="color: #ffa500" href="http://www.php.net/implode">implode</a>('<span style="color: #8b0000">/</span>', $temp);
    $temp = <a style="color: #ffa500" href="http://www.php.net/explode">explode</a>('<span style="color: #8b0000">:</span>', $host);
    $host = $temp[0];
    $port = isset($temp[1]) ? $temp[1] : 80;
    $fp = @<a style="color: #ffa500" href="http://www.php.net/fsockopen">fsockopen</a>($host, $port, &$errno, &$errstr, 30);
    <a style="color: #0000ff" href="http://www.php.net/if">if</a> ($fp) {
        @<a style="color: #ffa500" href="http://www.php.net/fputs">fputs</a>($fp, "<span style="color: #8b0000">GET $path HTTP/1.1\r\nHost: $host\r\nAccept: */*\r\nReferer:$url\r\nUser-Agent: Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1)\r\nConnection: Close\r\n\r\n</span>");
    }
    $Content = '<span style="color: #8b0000"></span>';
    <a style="color: #0000ff" href="http://www.php.net/while">while</a> ($str = @<a style="color: #ffa500" href="http://www.php.net/fread">fread</a>($fp, 4096))
        $Content .= $str;
    @<a style="color: #ffa500" href="http://www.php.net/fclose">fclose</a>($fp);
<span style="color: #008000">//$Content=preg_replace("~(?:\r)?\n~s","",$Content); </span>
    <a style="color: #0000ff" href="http://www.php.net/return">return</a> $Content;
}
{% endcodeblock %}
</span>
</div>
<br>
