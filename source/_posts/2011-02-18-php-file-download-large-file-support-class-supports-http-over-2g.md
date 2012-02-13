--- 
categories: 
  - PHP
comments: true
layout: post
published: true
status: publish
tags: 
  - php
  - server
  - 断点续传，超大文件
title: "php 超大文件下载类 支持2g以上文件 支持断点续传"
type: post
---
<div class="cnblogs_code">
{% codeblock %}
<img id="Code_Closed_Image_218623" onclick="this.style.display='none'; document.getElementById('Code_Closed_Text_218623').style.display='none'; document.getElementById('Code_Open_Image_218623').style.display='inline'; document.getElementById('Code_Open_Text_218623').style.display='inline';" height="16" src="http://www.cnblogs.com/Images/OutliningIndicators/ContractedBlock.gif" width="11" align="top"><img id="Code_Open_Image_218623" style="display: none" onclick="this.style.display='none'; document.getElementById('Code_Open_Text_218623').style.display='none'; getElementById('Code_Closed_Image_218623').style.display='inline'; getElementById('Code_Closed_Text_218623').style.display='inline';" height="16" src="http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockStart.gif" width="11" align="top"><span class="cnblogs_code_Collapse" id="Code_Closed_Text_218623"></span><span id="Code_Open_Text_218623" style="display: none"><span style="color: #0000ff"><?</span>php
<span style="color: #008000">/**
 * <SPAN class=t_tag onclick=tagshow(event) href="tag.php?name=%CE%C4%BC%FE">文件</SPAN>传输，支持断点续传。
 * 2g以上超大文件也有效
 * @author MoXie
 */</span>
<a style="color: #0000ff" href="http://www.php.net/class">class</a> Transfer {
    <span style="color: #008000">/**
     * 缓冲单元
     */</span>
    const BUFF_SIZE = 5120; <span style="color: #008000">// 1024 * 5</span>
    <span style="color: #008000">/**
     * 文件地址
     * @var <String>
     */</span>
    private $filePath;
    <span style="color: #008000">/**
     * 文件大小
     * @var <String> Php超大数字 <SPAN class=t_tag onclick=tagshow(event) href="tag.php?name=%D7%D6%B7%FB">字符</SPAN>串形式描述
     */</span>
    private $<a style="color: #ffa500" href="http://www.php.net/fileSize">fileSize</a>;
    <span style="color: #008000">/**
     * 文件类型
     * @var <String>
     */</span>
    private $mimeType;
    <span style="color: #008000">/**
     * 请求区域（范围）
     * @var <String>
     */</span>
    private $<a style="color: #ffa500" href="http://www.php.net/range">range</a>;
    <span style="color: #008000">/**
     * 是否写入日志
     * @var <Boolean>
     */</span>
    private $isLog = <a style="color: #0000ff" href="http://www.php.net/false">false</a>;
    <span style="color: #008000">/**
     *
     * @param <String> $filePath 文件路径
     * @param <String> $mimeType  文件类型
     * @param <String> $range 请求区域（范围）
     */</span>
    <a style="color: #0000ff" href="http://www.php.net/function">function</a> __construct($filePath, $mimeType = null , $<a style="color: #ffa500" href="http://www.php.net/range">range</a> = null) {
        $this->filePath = $filePath;
        $this-><a style="color: #ffa500" href="http://www.php.net/fileSize">fileSize</a> = <a style="color: #ffa500" href="http://www.php.net/sprintf">sprintf</a>('<span style="color: #8b0000">%u</span>',<a style="color: #ffa500" href="http://www.php.net/filesize">filesize</a>($filePath));
        $this->mimeType = ($mimeType != null)?$mimeType:"<span style="color: #8b0000">application/octet-stream</span>"; <span style="color: #008000">//  bin</span>
        $this-><a style="color: #ffa500" href="http://www.php.net/range">range</a> = <a style="color: #ffa500" href="http://www.php.net/trim">trim</a>($<a style="color: #ffa500" href="http://www.php.net/range">range</a>);
    }
    <span style="color: #008000">/**
     *  获取文件区域
     * @return <Map> {'start':long,'end':long} or null
     */</span>
    private <a style="color: #0000ff" href="http://www.php.net/function">function</a> getRange() {
        <span style="color: #008000">/**
         *  Range: bytes=-128
         *  Range: bytes=-128
         *  Range: bytes=28-175,382-399,510-541,644-744,977-980
         *  Range: bytes=28-175n380
         *  type 1
         *  RANGE: bytes=1000-9999
         *  RANGE: bytes=2000-9999
         *  type 2
         *  RANGE: bytes=1000-1999
         *  RANGE: bytes=2000-2999
         *  RANGE: bytes=3000-3999
         */</span>
        <a style="color: #0000ff" href="http://www.php.net/if">if</a> (!empty($this-><a style="color: #ffa500" href="http://www.php.net/range">range</a>)) {
            $<a style="color: #ffa500" href="http://www.php.net/range">range</a> = <a style="color: #ffa500" href="http://www.php.net/preg_replace">preg_replace</a>('<span style="color: #8b0000">/[s|,].*/</span>','<span style="color: #8b0000"></span>',$this-><a style="color: #ffa500" href="http://www.php.net/range">range</a>);
            $<a style="color: #ffa500" href="http://www.php.net/range">range</a> = <a style="color: #ffa500" href="http://www.php.net/explode">explode</a>('<span style="color: #8b0000">-</span>',<a style="color: #ffa500" href="http://www.php.net/substr">substr</a>($<a style="color: #ffa500" href="http://www.php.net/range">range</a>,6));
            <a style="color: #0000ff" href="http://www.php.net/if">if</a> (<a style="color: #ffa500" href="http://www.php.net/count">count</a>($<a style="color: #ffa500" href="http://www.php.net/range">range</a>) < 2 ) {
                $<a style="color: #ffa500" href="http://www.php.net/range">range</a>[1] = $this-><a style="color: #ffa500" href="http://www.php.net/fileSize">fileSize</a>; <span style="color: #008000">// Range: bytes=-100</span>
            }
            $<a style="color: #ffa500" href="http://www.php.net/range">range</a> = array_combine(<a style="color: #ffa500" href="http://www.php.net/array">array</a>('<span style="color: #8b0000">start</span>','<span style="color: #8b0000">end</span>'),$<a style="color: #ffa500" href="http://www.php.net/range">range</a>);
            <a style="color: #0000ff" href="http://www.php.net/if">if</a> (empty($<a style="color: #ffa500" href="http://www.php.net/range">range</a>['<span style="color: #8b0000">start</span>'])) {
                $<a style="color: #ffa500" href="http://www.php.net/range">range</a>['<span style="color: #8b0000">start</span>'] = 0;
            }
            <a style="color: #0000ff" href="http://www.php.net/if">if</a> (!isset ($<a style="color: #ffa500" href="http://www.php.net/range">range</a>['<span style="color: #8b0000">end</span>']) || empty($<a style="color: #ffa500" href="http://www.php.net/range">range</a>['<span style="color: #8b0000">end</span>'])) {
                $<a style="color: #ffa500" href="http://www.php.net/range">range</a>['<span style="color: #8b0000">end</span>'] = $this-><a style="color: #ffa500" href="http://www.php.net/fileSize">fileSize</a>;
            }
            <a style="color: #0000ff" href="http://www.php.net/return">return</a> $<a style="color: #ffa500" href="http://www.php.net/range">range</a>;
        }
        <a style="color: #0000ff" href="http://www.php.net/return">return</a> null;
    }
    <span style="color: #008000">/**
     * 向客户端发送文件
     */</span>
    public <a style="color: #0000ff" href="http://www.php.net/function">function</a> <a style="color: #ffa500" href="http://www.php.net/send">send</a>() {
        $fileHande = <a style="color: #ffa500" href="http://www.php.net/fopen">fopen</a>($this->filePath, '<span style="color: #8b0000">rb</span>');
        <a style="color: #0000ff" href="http://www.php.net/if">if</a> ($fileHande) {
            <span style="color: #008000">// setting</span>
            <a style="color: #ffa500" href="http://www.php.net/ob_end_clean">ob_end_clean</a>();<span style="color: #008000">// clean cache</span>
            <a style="color: #ffa500" href="http://www.php.net/ob_start">ob_start</a>();
            <a style="color: #ffa500" href="http://www.php.net/ini_set">ini_set</a>('<span style="color: #8b0000">output_buffering</span>', '<span style="color: #8b0000">Off</span>');
            <a style="color: #ffa500" href="http://www.php.net/ini_set">ini_set</a>('<span style="color: #8b0000">zlib.output_compression</span>', '<span style="color: #8b0000">Off</span>');
            $magicQuotes = <a style="color: #ffa500" href="http://www.php.net/get_magic_quotes_gpc">get_magic_quotes_gpc</a>();
            <a style="color: #ffa500" href="http://www.php.net/set_magic_quotes_runtime">set_magic_quotes_runtime</a>(0);
            <span style="color: #008000">// init</span>
            $lastModified = <a style="color: #ffa500" href="http://www.php.net/gmdate">gmdate</a>('<span style="color: #8b0000">D, d M Y H:i:s</span>', <a style="color: #ffa500" href="http://www.php.net/filemtime">filemtime</a>($this->filePath)).'<span style="color: #8b0000"> GMT</span>';
            $etag = <a style="color: #ffa500" href="http://www.php.net/sprintf">sprintf</a>('<span style="color: #8b0000">w/"%s:%s"</span>',md5($lastModified),$this-><a style="color: #ffa500" href="http://www.php.net/fileSize">fileSize</a>);
            $ranges = $this->getRange();
            <span style="color: #008000">// headers</span>
            <a style="color: #ffa500" href="http://www.php.net/header">header</a>(<a style="color: #ffa500" href="http://www.php.net/sprintf">sprintf</a>('<span style="color: #8b0000">Last-Modified: %s</span>',$lastModified));
            <a style="color: #ffa500" href="http://www.php.net/header">header</a>(<a style="color: #ffa500" href="http://www.php.net/sprintf">sprintf</a>('<span style="color: #8b0000">ETag: %s</span>',$etag));
            <a style="color: #ffa500" href="http://www.php.net/header">header</a>(<a style="color: #ffa500" href="http://www.php.net/sprintf">sprintf</a>('<span style="color: #8b0000">Content-Type: %s</span>',$this->mimeType));
            $disposition = '<span style="color: #8b0000">attachment</span>';
            <a style="color: #0000ff" href="http://www.php.net/if">if</a> (<a style="color: #ffa500" href="http://www.php.net/strpos">strpos</a>($this->mimeType,'<span style="color: #8b0000">image/</span>') !== FALSE) {
                $disposition = '<span style="color: #8b0000">inline</span>';
            }
            <a style="color: #ffa500" href="http://www.php.net/header">header</a>(<a style="color: #ffa500" href="http://www.php.net/sprintf">sprintf</a>('<span style="color: #8b0000">Content-Disposition: %s; filename="%s"</span>',$disposition,<a style="color: #ffa500" href="http://www.php.net/basename">basename</a>($this->filePath)));
            
            <a style="color: #0000ff" href="http://www.php.net/if">if</a> ($ranges != null) {
                <a style="color: #0000ff" href="http://www.php.net/if">if</a> ($this->isLog) {
                    $this-><a style="color: #ffa500" href="http://www.php.net/log">log</a>(json_encode($ranges).'<span style="color: #8b0000"> </span>'.$_SERVER['<span style="color: #8b0000">HTTP_RANGE</span>']);
                }
                <a style="color: #ffa500" href="http://www.php.net/header">header</a>('<span style="color: #8b0000">HTTP/1.1 206 Partial Content</span>');
                <a style="color: #ffa500" href="http://www.php.net/header">header</a>('<span style="color: #8b0000">Accept-Ranges: bytes</span>');
                <a style="color: #ffa500" href="http://www.php.net/header">header</a>(<a style="color: #ffa500" href="http://www.php.net/sprintf">sprintf</a>('<span style="color: #8b0000">Content-Length: %u</span>',$ranges['<span style="color: #8b0000">end</span>'] - $ranges['<span style="color: #8b0000">start</span>']));
                <a style="color: #ffa500" href="http://www.php.net/header">header</a>(<a style="color: #ffa500" href="http://www.php.net/sprintf">sprintf</a>('<span style="color: #8b0000">Content-Range: bytes %s-%s/%s</span>', $ranges['<span style="color: #8b0000">start</span>'], $ranges['<span style="color: #8b0000">end</span>'],$this-><a style="color: #ffa500" href="http://www.php.net/fileSize">fileSize</a>));
                <span style="color: #008000">//</span>
                <a style="color: #ffa500" href="http://www.php.net/fseek">fseek</a>($fileHande, <a style="color: #ffa500" href="http://www.php.net/sprintf">sprintf</a>('<span style="color: #8b0000">%u</span>',$ranges['<span style="color: #8b0000">start</span>']));
            }<a style="color: #0000ff" href="http://www.php.net/else">else</a> {
                <a style="color: #ffa500" href="http://www.php.net/header">header</a>("<span style="color: #8b0000">HTTP/1.1 200 OK</span>");
                <a style="color: #ffa500" href="http://www.php.net/header">header</a>(<a style="color: #ffa500" href="http://www.php.net/sprintf">sprintf</a>('<span style="color: #8b0000">Content-Length: %s</span>',$this-><a style="color: #ffa500" href="http://www.php.net/fileSize">fileSize</a>));
            }
            <span style="color: #008000">// read file</span>
            $lastSize = 0;
            <a style="color: #0000ff" href="http://www.php.net/while">while</a>(!<a style="color: #ffa500" href="http://www.php.net/feof">feof</a>($fileHande) && !<a style="color: #ffa500" href="http://www.php.net/connection_aborted">connection_aborted</a>()) {
                $lastSize = <a style="color: #ffa500" href="http://www.php.net/sprintf">sprintf</a>("<span style="color: #8b0000">%u</span>", <a style="color: #ffa500" href="http://www.php.net/bcsub">bcsub</a>($this-><a style="color: #ffa500" href="http://www.php.net/fileSize">fileSize</a>,<a style="color: #ffa500" href="http://www.php.net/sprintf">sprintf</a>("<span style="color: #8b0000">%u</span>",<a style="color: #ffa500" href="http://www.php.net/ftell">ftell</a>($fileHande))));
                <a style="color: #0000ff" href="http://www.php.net/if">if</a> (<a style="color: #ffa500" href="http://www.php.net/bccomp">bccomp</a>($lastSize,self::BUFF_SIZE) > 0) {
                    $lastSize = self::BUFF_SIZE;
                }
                <a style="color: #0000ff" href="http://www.php.net/echo">echo</a> <a style="color: #ffa500" href="http://www.php.net/fread">fread</a>($fileHande, $lastSize);
                <a style="color: #ffa500" href="http://www.php.net/flush">flush</a>();
                ob_flush();
            }
            <a style="color: #ffa500" href="http://www.php.net/set_magic_quotes_runtime">set_magic_quotes_runtime</a>($magicQuotes);
            <a style="color: #ffa500" href="http://www.php.net/ob_end_flush">ob_end_flush</a>();
        }
        <a style="color: #0000ff" href="http://www.php.net/if">if</a> ($fileHande != null) {
            <a style="color: #ffa500" href="http://www.php.net/fclose">fclose</a>($fileHande);
        }
    }
    <span style="color: #008000">/**
     * 设置记录
     * @param <Boolean> $isLog  是否记录
     */</span>
    public <a style="color: #0000ff" href="http://www.php.net/function">function</a> setIsLog($isLog = <a style="color: #0000ff" href="http://www.php.net/true">true</a>) {
        $this->isLog = $isLog;
    }
    <span style="color: #008000">/**
     * 记录
     * @param <String> $msg  记录信息
     */</span>
    private <a style="color: #0000ff" href="http://www.php.net/function">function</a> <a style="color: #ffa500" href="http://www.php.net/log">log</a>($msg) {
        try {
            $handle = <a style="color: #ffa500" href="http://www.php.net/fopen">fopen</a>('<span style="color: #8b0000">transfer_log.txt</span>', '<span style="color: #8b0000">a</span>');
            <a style="color: #ffa500" href="http://www.php.net/fwrite">fwrite</a>($handle, <a style="color: #ffa500" href="http://www.php.net/sprintf">sprintf</a>('<span style="color: #8b0000">%s : %s</span>'."<span style="color: #8b0000"><SPAN class=t_tag onclick=tagshow(event) href=\"tag.php?name=PHP\">PHP</SPAN>_EOL</span>",<a style="color: #ffa500" href="http://www.php.net/date">date</a>('<span style="color: #8b0000">Y-m-d H:i:s</span>'),$msg));
            <a style="color: #ffa500" href="http://www.php.net/fclose">fclose</a>($handle);
        }catch(Exception $e) {
            <span style="color: #008000">// null;</span>
        }
    }
}
date_default_timezone_set('<span style="color: #8b0000">Asia/Shanghai</span>');
<a style="color: #ffa500" href="http://www.php.net/error_reporting">error_reporting</a>(E_STRICT);
<a style="color: #0000ff" href="http://www.php.net/function">function</a> errorHandler($errno, $errstr, $errfile, $errline) {
    <a style="color: #0000ff" href="http://www.php.net/echo">echo</a> '<span style="color: #8b0000"><p>error:</span>',$errstr,'<span style="color: #8b0000"></p></span>';
    <a style="color: #0000ff" href="http://www.php.net/exit">exit</a>();
}
<a style="color: #ffa500" href="http://www.php.net/set_error_handler">set_error_handler</a>('<span style="color: #8b0000">errorHandler</span>');
<a style="color: #ffa500" href="http://www.php.net/define">define</a>('<span style="color: #8b0000">IS_DEBUG</span>',<a style="color: #0000ff" href="http://www.php.net/true">true</a>);

<span style="color: #008000">//</span>
<span style="color: #008000">//</span>
$filePath = '<span style="color: #8b0000">/Movie/The.Hurt.Locker.2008.x264.AC3-WAF.mkv</span>';
$mimeType = '<span style="color: #8b0000">audio/x-matroska</span>';
$<a style="color: #ffa500" href="http://www.php.net/range">range</a> = isset($_SERVER['<span style="color: #8b0000">HTTP_RANGE</span>'])?$_SERVER['<span style="color: #8b0000">HTTP_RANGE</span>']:null;
<a style="color: #0000ff" href="http://www.php.net/if">if</a> (IS_DEBUG) {
    <span style="color: #008000">//    $range = "bytes=1000-1999n2000";</span>
    <span style="color: #008000">//    $range = "bytes=1000-1999,2000";</span>
    <span style="color: #008000">//    $range = "bytes=1000-1999,-2000";</span>
    <span style="color: #008000">//    $range = "bytes=1000-1999,2000-2999";</span>
}
<a style="color: #ffa500" href="http://www.php.net/set_time_limit">set_time_limit</a>(0);
$transfer = new Transfer($filePath,$mimeType,$<a style="color: #ffa500" href="http://www.php.net/range">range</a>);
<a style="color: #0000ff" href="http://www.php.net/if">if</a> (IS_DEBUG) {
    $transfer->setIsLog(<a style="color: #0000ff" href="http://www.php.net/true">true</a>);
}
$transfer-><a style="color: #ffa500" href="http://www.php.net/send">send</a>();
<span style="color: #0000ff">?></span>
{% endcodeblock %}
</span>
</div>
<br>
