--- 
categories: 
  - PHP
comments: true
layout: post
published: true
status: publish
tags: 
  - file_exists
  - php
  - urldecode
  - 汉字
  - 编码
title: 被冤枉的file_exists
type: post
---
我在做项目的时候需要把图片进行压缩，当然进行压缩之前要先检查一下原图在不在，压缩完后也要检查一下新图有没有被压缩出来，但是我使用 file_exists 进行检查的时候却一直给我false。 代码如下： <div class="cnblogs_code">
{% codeblock %}
<img id="Code_Closed_Image_828909" onclick="this.style.display='none'; document.getElementById('Code_Closed_Text_828909').style.display='none'; document.getElementById('Code_Open_Image_828909').style.display='inline'; document.getElementById('Code_Open_Text_828909').style.display='inline';" height="16" src="http://www.cnblogs.com/Images/OutliningIndicators/ContractedBlock.gif" width="11" align="top"><img id="Code_Open_Image_828909" style="display: none" onclick="this.style.display='none'; document.getElementById('Code_Open_Text_828909').style.display='none'; getElementById('Code_Closed_Image_828909').style.display='inline'; getElementById('Code_Closed_Text_828909').style.display='inline';" height="16" src="http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockStart.gif" width="11" align="top"><span class="cnblogs_code_Collapse" id="Code_Closed_Text_828909"></span><span id="Code_Open_Text_828909" style="display: none">if (file_exists($desimage)) {
    $ok_num += 1;
} else {
   $fail_num += 1;
}
{% endcodeblock %}
</span>
</div>仔细检查了一下才发现，我拿到的图片url中包含 汉字 ，例如：<div class="cnblogs_code">
{% codeblock %}
<img id="Code_Closed_Image_828909" onclick="this.style.display='none'; document.getElementById('Code_Closed_Text_828909').style.display='none'; document.getElementById('Code_Open_Image_828909').style.display='inline'; document.getElementById('Code_Open_Text_828909').style.display='inline';" height="16" src="http://www.cnblogs.com/Images/OutliningIndicators/ContractedBlock.gif" width="11" align="top"><img id="Code_Open_Image_828909" style="display: none" onclick="this.style.display='none'; document.getElementById('Code_Open_Text_828909').style.display='none'; getElementById('Code_Closed_Image_828909').style.display='inline'; getElementById('Code_Closed_Text_828909').style.display='inline';" height="16" src="http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockStart.gif" width="11" align="top"><span class="cnblogs_code_Collapse" id="Code_Closed_Text_828909"></span><span id="Code_Open_Text_828909" style="display: none">if (file_exists($desimage)) {
    $ok_num += 1;
} else {
   $fail_num += 1;
}
{% endcodeblock %}
</span>
</div>而这些汉字在拿到的时候都会转变成 已编码的 URL 字符串，如：<div class="cnblogs_code">
{% codeblock %}
<img id="Code_Closed_Image_828909" onclick="this.style.display='none'; document.getElementById('Code_Closed_Text_828909').style.display='none'; document.getElementById('Code_Open_Image_828909').style.display='inline'; document.getElementById('Code_Open_Text_828909').style.display='inline';" height="16" src="http://www.cnblogs.com/Images/OutliningIndicators/ContractedBlock.gif" width="11" align="top"><img id="Code_Open_Image_828909" style="display: none" onclick="this.style.display='none'; document.getElementById('Code_Open_Text_828909').style.display='none'; getElementById('Code_Closed_Image_828909').style.display='inline'; getElementById('Code_Closed_Text_828909').style.display='inline';" height="16" src="http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockStart.gif" width="11" align="top"><span class="cnblogs_code_Collapse" id="Code_Closed_Text_828909"></span><span id="Code_Open_Text_828909" style="display: none">if (file_exists($desimage)) {
    $ok_num += 1;
} else {
   $fail_num += 1;
}
{% endcodeblock %}
</span>
</div>那么很明显我通过  已编码的 URL 字符串 去到服务器中找这个文件是肯定找不到的。唉，郁闷了。。解决方法很简单:<div class="cnblogs_code">
{% codeblock %}
<img id="Code_Closed_Image_828909" onclick="this.style.display='none'; document.getElementById('Code_Closed_Text_828909').style.display='none'; document.getElementById('Code_Open_Image_828909').style.display='inline'; document.getElementById('Code_Open_Text_828909').style.display='inline';" height="16" src="http://www.cnblogs.com/Images/OutliningIndicators/ContractedBlock.gif" width="11" align="top"><img id="Code_Open_Image_828909" style="display: none" onclick="this.style.display='none'; document.getElementById('Code_Open_Text_828909').style.display='none'; getElementById('Code_Closed_Image_828909').style.display='inline'; getElementById('Code_Closed_Text_828909').style.display='inline';" height="16" src="http://www.cnblogs.com/Images/OutliningIndicators/ExpandedBlockStart.gif" width="11" align="top"><span class="cnblogs_code_Collapse" id="Code_Closed_Text_828909"></span><span id="Code_Open_Text_828909" style="display: none">if (file_exists($desimage)) {
    $ok_num += 1;
} else {
   $fail_num += 1;
}
{% endcodeblock %}
</span>
</div>记下以示警示！
