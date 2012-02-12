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
  - 断点续传
  - 超大文件
title: "php 断点续传功能"
type: post
---
断点续传指的是在上传时，将上传任务（一个文件或一个压缩包）人为的划分为几个部分，每一个部分采用一个线程进行上传，下面我们来看看php 断点续传功能的实现方法吧。 <div class="cnblogs_code">
{% codeblock %}
<img id="Code_Closed_Image_146453" onclick="this.style.display='none'; document.getElementById('Code_Closed_Text_146453').style.display='none'; document.getElementById('Code_Open_Image_146453').style.display='inline'; document.getElementById('Code_Open_Text_146453').style.display='inline';" height="16" src="http://www.cnblogs.com/Images/OutliningIndicators/ContractedBlock.gif" width="11" align="top"><img id="Code_Open_Image_146453" style="display: none" onclick="this.style.display='none'; document.getElementById('Code_Open_Text_146453').style.display='none'; getElementById('Code_Closed_Image_146453').style.display='inline'; getElementById('Code_Closed_Text_146453').style.display='inline';" height="16" src="http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockStart.gif" width="11" align="top"><span class="cnblogs_code_Collapse" id="Code_Closed_Text_146453"></span><span id="Code_Open_Text_146453" style="display: none"><span style="color: #0000ff"><?</span>php
<span style="color: #008000">/**
 * 作者 于恩水<yuenshui@126.com>
 * 支持断点续传下载
 * 实例代码：
 *           $down = new SD_DownLoad();
 *          $down->Down('E:/iso/MS.Office2003SP1.CHS.iso');
 **/</span>
<a style="color: #0000ff" href="http://www.php.net/class">class</a> SD_DownLoad {
    
    <span style="color: #008000">/**
     * 下载的开始点
     * 
     * @access private
     * @var integer
     */</span>
    private $mDownStart;
    
    <span style="color: #008000">/**
     * 文件大小
     * 
     * @access private
     * @var integer
     */</span>
    private $mFileSize;
    
    <span style="color: #008000">/**
     * 文件句柄
     * 
     * @access private
     * @var integer
     */</span>
    private $mFileHandle;
    
    <span style="color: #008000">/**
     * 文件全路径
     * 
     * @access private
     * @var string
     */</span>
    private $mFilePath;
    
    <span style="color: #008000">/**
     * 文件下载时显示的文件名
     * 
     * @access private
     * @var string
     */</span>
    private $mFileName;
    
    <span style="color: #008000">/**
     * 构造函数
     * 
     * @access public
     * @return void
     **/</span>
    public <a style="color: #0000ff" href="http://www.php.net/function">function</a> __construct() {
    }
    
    <span style="color: #008000">/**
     * 下载
     * 
     * @param string $pFilePath 文件全路径
     * @param string pFileName 文件下载时显示的文件名，缺省为实际文件名
     * @access public
     * @return void
     **/</span>
    public <a style="color: #0000ff" href="http://www.php.net/function">function</a> Down($pFilePath, $pFileName = '<span style="color: #8b0000"></span>') {
        $this->mFilePath = $pFilePath;
        <a style="color: #0000ff" href="http://www.php.net/if">if</a>(!$this->IniFile()) $this->SendError();
        $this->mFileName = empty($pFileName) ? $this->GetFileName() : $pFileName;
        
        $this->IniFile();
        $this->SetStart();
        $this->SetHeader();
        
        $this-><a style="color: #ffa500" href="http://www.php.net/Send">Send</a>();
    }
    
    <span style="color: #008000">/**
     * 初始化文件信息
     * 
     * @access private
     * @return boolean
     **/</span>
    private <a style="color: #0000ff" href="http://www.php.net/function">function</a> IniFile() {
        <a style="color: #0000ff" href="http://www.php.net/if">if</a>(!<a style="color: #ffa500" href="http://www.php.net/is_file">is_file</a>($this->mFilePath)) <a style="color: #0000ff" href="http://www.php.net/return">return</a> <a style="color: #0000ff" href="http://www.php.net/false">false</a>;
        $this->mFileHandle = <a style="color: #ffa500" href="http://www.php.net/fopen">fopen</a>($this->mFilePath, '<span style="color: #8b0000">rb</span>');
        $this->mFileSize = <a style="color: #ffa500" href="http://www.php.net/filesize">filesize</a>($this->mFilePath);
        <a style="color: #0000ff" href="http://www.php.net/return">return</a> <a style="color: #0000ff" href="http://www.php.net/true">true</a>;
    }
    
    <span style="color: #008000">/**
     * 设置下载开始点
     * 
     * @access private
     * @return void
     **/</span>
    private <a style="color: #0000ff" href="http://www.php.net/function">function</a> SetStart() {
        <a style="color: #0000ff" href="http://www.php.net/if">if</a> (!empty($_SERVER['<span style="color: #8b0000">HTTP_RANGE</span>']) && <a style="color: #ffa500" href="http://www.php.net/preg_match">preg_match</a>("<span style="color: #8b0000">/^bytes=([d]?)-([d]?)$/i</span>", $_SERVER['<span style="color: #8b0000">HTTP_RANGE</span>'], $match)) {
            <a style="color: #0000ff" href="http://www.php.net/if">if</a>(empty($match[1])) $this->mDownStart = $match[1];
            <a style="color: #ffa500" href="http://www.php.net/fseek">fseek</a>($this->mFileHandle, $this->mDownStart);
        }
        <a style="color: #0000ff" href="http://www.php.net/else">else</a> {
            $this->mDownStart = 0;
        }
    }
    
    <span style="color: #008000">/**
     * 设置http头
     * 
     * @access private
     * @return void
     **/</span>
    private <a style="color: #0000ff" href="http://www.php.net/function">function</a> SetHeader() {
        @<a style="color: #ffa500" href="http://www.php.net/header">header</a>("<span style="color: #8b0000">Cache-control: public</span>");
        @<a style="color: #ffa500" href="http://www.php.net/header">header</a>("<span style="color: #8b0000">Pragma: public</span>");
        <a style="color: #ffa500" href="http://www.php.net/Header">Header</a>("<span style="color: #8b0000">Content-Length: </span>" . ($this->mFileSize - $this->mDownStart));
        <a style="color: #0000ff" href="http://www.php.net/if">if</a> ($this->mDownStart > 0) {
            @<a style="color: #ffa500" href="http://www.php.net/Header">Header</a>("<span style="color: #8b0000">HTTP/1.1 206 Partial Content</span>");
            <a style="color: #ffa500" href="http://www.php.net/Header">Header</a>("<span style="color: #8b0000">Content-Ranges: bytes</span>" . $this->mDownStart . "<span style="color: #8b0000">-</span>" . ($this->mFileSize - 1) . "<span style="color: #8b0000">/</span>" . $this->mFileSize);
        }
        <a style="color: #0000ff" href="http://www.php.net/else">else</a> {
            <a style="color: #ffa500" href="http://www.php.net/Header">Header</a>("<span style="color: #8b0000">Accept-Ranges: bytes</span>");
        }
        @<a style="color: #ffa500" href="http://www.php.net/header">header</a>("<span style="color: #8b0000">Content-Type: application/octet-stream</span>");
        @<a style="color: #ffa500" href="http://www.php.net/header">header</a>("<span style="color: #8b0000">Content-Disposition: attachment;filename=</span>" . $this->mFileName);
    }
    
    <span style="color: #008000">/**
     * 获取全路径里的文件名部分
     * 
     * @access private
     * @return string
     **/</span>
    private <a style="color: #0000ff" href="http://www.php.net/function">function</a> GetFileName() {
        <a style="color: #0000ff" href="http://www.php.net/return">return</a> <a style="color: #ffa500" href="http://www.php.net/basename">basename</a> ($this->mFilePath);
    }
    
    <span style="color: #008000">/**
     * 发送数据
     * 
     * @access private
     * @return void
     **/</span>
    private <a style="color: #0000ff" href="http://www.php.net/function">function</a> <a style="color: #ffa500" href="http://www.php.net/Send">Send</a>() {
        <a style="color: #ffa500" href="http://www.php.net/fpassthru">fpassthru</a>($this->mFileHandle);
    }
    
    <span style="color: #008000">/**
     * 发送错误
     * 
     * @access public
     * @return void
     **/</span>
    public <a style="color: #0000ff" href="http://www.php.net/function">function</a> SendError() {
        @<a style="color: #ffa500" href="http://www.php.net/header">header</a>("<span style="color: #8b0000">HTTP/1.0 404 Not Found</span>");
        @<a style="color: #ffa500" href="http://www.php.net/header">header</a>("<span style="color: #8b0000">Status: 404 Not Found</span>");
        <a style="color: #0000ff" href="http://www.php.net/exit">exit</a>();
    }
}
<span style="color: #0000ff">?></span>
{% endcodeblock %}
</span>
</div>
<br>
