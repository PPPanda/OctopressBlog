--- 
categories: 
  - PHP
comments: true
layout: post
published: true
status: publish
tags: 
  - php
title: "PHP: 构造函数和析构函数 - Manual"
type: post
---
<div>
<div class="sect2">
<h3 class="title">构造函数</h3>
<div class="methodsynopsis">
<span class="type">void</span> <span class="methodname"><b><b>__construct</b></b></span> ([ <span class="methodparam"><span class="type">mixed</span> <tt>$args</tt></span> [, <span class="methodparam"><tt>$...</tt></span> ]] )</div>
PHP 5 允行开发者在一个类中定义一个方法作为构造函数。具有构造函数的类会在每次创建对象时先调用此方法，所以非常适合在使用对象之前做一些初始化工作。 
{% codeblock %}
<b>Note</b>: <span class="simpara">如果子类中定义了构造函数则不会暗中调用其父类的构造函数。要执行父类的构造函数，需要在子类的构造函数中调用 <b>parent::__construct()</b>。 </span>
{% endcodeblock %}
<div class="example">
<b>Example#1 使用新标准的构造函数</b><div class="example-contents"><div class="phpcode">
{% codeblock %}
<span><span><?php<br></span><span>class </span><span>BaseClass </span><span>{<br>   function </span><span>__construct</span><span>() {<br>       print </span><span>"In BaseClass constructor\n"</span><span>;<br>   }<br>}<br><br>class </span><span>SubClass </span><span>extends </span><span>BaseClass </span><span>{<br>   function </span><span>__construct</span><span>() {<br>       </span><span>parent</span><span>::</span><span>__construct</span><span>();<br>       print </span><span>"In SubClass constructor\n"</span><span>;<br>   }<br>}<br><br></span><span>$obj </span><span>= new </span><span>BaseClass</span><span>();<br></span><span>$obj </span><span>= new </span><span>SubClass</span><span>();<br></span><span>?></span> </span>
{% endcodeblock %}
</div></div>
</div>为了实现向后兼容性，如果 PHP 5 在类中找不到 <b>__construct()</b> 函数，它就会尝试寻找旧式的构造函数，也就是和类同名的函数。因此唯一会产生兼容性问题的情况是：类中已有一个名为 <b>__construct()</b> 的方法，但它却又不是构造函数。 </div>
<div class="sect2">
<h3 class="title">析构函数</h3>
<div class="methodsynopsis">
<span class="type">void</span> <span class="methodname"><b><b>__destruct</b></b></span> ( <span class="methodparam">void</span> )</div>PHP 5 引入了析构函数的概念，这类似于其它面向对象的语言，如 C++。析构函数会在到某个对象的所有引用都被删除或者当对象被显式销毁时执行。 <div class="example">
<b>Example#2 析构函数示例</b><div class="example-contents"><div class="phpcode">
{% codeblock %}
<span><span><?php<br></span><span>class </span><span>BaseClass </span><span>{<br>   function </span><span>__construct</span><span>() {<br>       print </span><span>"In BaseClass constructor\n"</span><span>;<br>   }<br>}<br><br>class </span><span>SubClass </span><span>extends </span><span>BaseClass </span><span>{<br>   function </span><span>__construct</span><span>() {<br>       </span><span>parent</span><span>::</span><span>__construct</span><span>();<br>       print </span><span>"In SubClass constructor\n"</span><span>;<br>   }<br>}<br><br></span><span>$obj </span><span>= new </span><span>BaseClass</span><span>();<br></span><span>$obj </span><span>= new </span><span>SubClass</span><span>();<br></span><span>?></span> </span>
{% endcodeblock %}
</div></div>
</div>和构造函数一样，父类的析构函数不会被引擎暗中调用。要执行父类的析构函数，必须在子类的析构函数体中显式调用 <b>parent::__destruct()</b>。 
{% codeblock %}
<b>Note</b>: <span class="simpara">如果子类中定义了构造函数则不会暗中调用其父类的构造函数。要执行父类的构造函数，需要在子类的构造函数中调用 <b>parent::__construct()</b>。 </span>
{% endcodeblock %}

{% codeblock %}
<b>Note</b>: <span class="simpara">如果子类中定义了构造函数则不会暗中调用其父类的构造函数。要执行父类的构造函数，需要在子类的构造函数中调用 <b>parent::__construct()</b>。 </span>
{% endcodeblock %}
</div>
</div>
<div><a title="Wiz，个人知识管理，PKM。" href="http://wiz.cn">通过Wiz发布</a></div>
