--- 
categories: 
  - JavaScript
comments: true
layout: post
published: true
status: publish
tags: 
  - css
  - google
  - html
  - java
  - JavaScript
  - News
  - web
  - 主题
  - 插件
  - 教程
  - 数字
  - 文章
  - 新闻
  - 更新
  - 浏览器
  - 计算机
  - 论坛
  - 软件
title: "JavaScript 中的函数式编程实践"
type: post
---
<a name="major1"><span class="atitle">基础知识</span></a><a name="minor1.1"><span class="smalltitle"><font size="3">函数式编程简介</font></span></a>说到函数式编程，人们的第一印象往往是其学院派，晦涩难懂，大概只有那些蓬头散发，不修边幅，甚至有些神经质的大学教授们才会用的编程方式。这可能在历史上的某个阶段的确如此，但是近来函数式编程已经在实际应用中发挥着巨大作用了，而更有越来越多的语言不断的加入诸如 <em>闭包</em>，<em>匿名函数</em>等的支持，从某种程度上来讲，函数式编程正在逐步“同化”命令式编程。<!--more-->函数式编程思想的源头可以追溯到 20 世纪 30 年代，数学家阿隆左 . 丘奇在进行一项关于问题的可计算性的研究，也就是后来的 lambda 演算。lambda 演算的本质为 <em>一切皆函数</em>，函数可以作为另外一个函数的输出或者 / 和输入，一系列的函数使用最终会形成一个表达式链，这个表达式链可以最终求得一个值，而这个过程，即为计算的本质。然而，这种思想在当时的硬件基础上很难实现，历史最终选择了同丘奇的 lambda 理论平行的另一种数学理论：图灵机作为计算理论，而采取另一位科学家冯 . 诺依曼的计算机结构，并最终被实现为硬件。由于第一台计算机即为冯 . 诺依曼的程序存储结构，因此运行在此平台的程序也继承了这种基因，程序设计语言如 C/Pascal 等都在一定程度上依赖于此体系。到了 20 世纪 50 年代，一位 MIT 的教授 John McCarthy 在冯 . 诺依曼体系的机器上成功的实现了 lambda 理论，取名为 LISP(LISt Processor), 至此函数式编程语言便开始活跃于计算机科学领域。<a name="minor1.2"><span class="smalltitle"><font size="3">函数式编程语言特性</font></span></a>在函数式编程语言中，函数是第一类的对象，也就是说，函数 <em>不</em>依赖于任何其他的对象而可以独立存在，而在面向对象的语言中，函数 ( 方法 ) 是依附于对象的，属于对象的一部分。这一点 j 决定了函数在函数式语言中的一些特别的性质，比如作为传出 / 传入参数，作为一个普通的变量等。区别于命令式编程语言，函数式编程语言具有一些专用的概念，我们分别进行讨论：<strong>匿名函数</strong>在函数式编程语言中，函数是可以没有名字的，匿名函数通常表示：“可以完成某件事的一块代码”。这种表达在很多场合是有用的，因为我们有时需要用函数完成某件事，但是这个函数可能只是临时性的，那就没有理由专门为其生成一个顶层的函数对象。比如：<div align="left">
<br><a name="listing1"><b><font face="Arial" size="2">清单 1. map 函数</font></b></a><br>
</div>
<div align="left"><table cellspacing="0" cellpadding="0" width="100%" align="left" border="0"><tbody><tr><td class="code-outline">
{% codeblock %}
				  function map(array, func){   var res = [];   for ( var i = 0, len = array.length; i < len; i++){  res.push(func(array[i])); 	 }   return res;  }  var mapped = map([1, 3, 5, 7, 8],  function (n){   return n = n + 1;  });  print(mapped); 运行这段代码，将会打印： 2,4,6,8,9// 对数组 [1,3,5,7,8] 中每一个元素加 1 
{% endcodeblock %}
</td></tr></tbody></table></div>
<div align="left">
<br> </div>注意 map 函数的调用，map 的第二个参数为一个函数，这个函数对 map 的第一个参数 ( 数组 ) 中的每一个都有作用，但是对于 map 之外的代码可能没有任何意义，因此，我们无需为其专门定义一个函数，匿名函数已经足够。<strong>柯里化</strong>柯里化是把接受多个参数的函数变换成接受一个单一参数（最初函数的第一个参数）的函数，并且返回接受余下的参数而且返回结果的新函数的技术。这句话有点绕口，我们可以通过例子来帮助理解：<div align="left">
<br><a name="listing2"><b><font face="Arial" size="2">清单 2. 柯里化函数</font></b></a><br>
</div>
<div align="left"><table cellspacing="0" cellpadding="0" width="100%" align="left" border="0"><tbody><tr><td class="code-outline">
{% codeblock %}
				  function map(array, func){   var res = [];   for ( var i = 0, len = array.length; i < len; i++){  res.push(func(array[i])); 	 }   return res;  }  var mapped = map([1, 3, 5, 7, 8],  function (n){   return n = n + 1;  });  print(mapped); 运行这段代码，将会打印： 2,4,6,8,9// 对数组 [1,3,5,7,8] 中每一个元素加 1 
{% endcodeblock %}
</td></tr></tbody></table></div>
<div align="left">
<br> </div>结果为：67比较有意思的是：函数 adder 接受一个参数，并返回一个函数，这个返回的函数可以被预期的那样被调用。变量 add5 保持着 adder(5) 返回的函数，<em>这个函数</em>可以接受一个参数，并返回参数与 5 的和。柯里化在 DOM 的回调中非常有用，我们将在下面的小节中看到。<strong>高阶函数</strong>高阶函数即为对函数的进一步抽象，事实上，我们在匿名函数小节提到的 map 函数即为一种高阶函数，在很多的函数式编程语言中均有此函数。map(array, func) 的表达式已经表明，将 func 函数作用于 array 中的每一个元素，最终返回一个新的 array，应该注意的是，map 对 array 和 func 的实现是没有任何预先的假设的，因此称之为“高阶”函数：<div align="left">
<br><a name="listing3"><b><font face="Arial" size="2">清单 3. 高阶函数</font></b></a><br>
</div>
<div align="left"><table cellspacing="0" cellpadding="0" width="100%" align="left" border="0"><tbody><tr><td class="code-outline">
{% codeblock %}
				  function map(array, func){   var res = [];   for ( var i = 0, len = array.length; i < len; i++){  res.push(func(array[i])); 	 }   return res;  }  var mapped = map([1, 3, 5, 7, 8],  function (n){   return n = n + 1;  });  print(mapped); 运行这段代码，将会打印： 2,4,6,8,9// 对数组 [1,3,5,7,8] 中每一个元素加 1 
{% endcodeblock %}
</td></tr></tbody></table></div>
<div align="left">
<br> </div>将会打印如下结果：<div align="left"><table cellspacing="0" cellpadding="0" width="100%" align="left" border="0"><tbody><tr><td class="code-outline">
{% codeblock %}
				  function map(array, func){   var res = [];   for ( var i = 0, len = array.length; i < len; i++){  res.push(func(array[i])); 	 }   return res;  }  var mapped = map([1, 3, 5, 7, 8],  function (n){   return n = n + 1;  });  print(mapped); 运行这段代码，将会打印： 2,4,6,8,9// 对数组 [1,3,5,7,8] 中每一个元素加 1 
{% endcodeblock %}
</td></tr></tbody></table></div>
<div align="left">
<br> </div>mapped 和 mapped2 均调用了 map，但是得到了截然不同的结果，因为 map 的参数本身已经进行了一次抽象，map 函数做的是第二次抽象，高阶的“阶”可以理解为抽象的层次。<div align="left"><div class="ibm-alternate-rule"><hr></div></div>
<div align="left"><a class="ibm-anchor-up-link" href="/Documents%20and%20Settings/Administrator/Local%20Settings/Temp/Wiz/53b706ec-a9fd-4fb3-b910-d83a214e1556_1.htm#ibm-pcon"><strong>回页首</strong></a></div>
<a name="major2"><span class="atitle">JavaScript 中的函数式编程</span></a>JavaScript 是一门被误解甚深的语言，由于早期的 Web 开发中，充满了大量的 copy-paste 代码，因此平时可以见到的 JavaScript 代码质量多半不高，而且 JavaScript 代码总是很飞动的不断闪烁的 gif 广告，限制网页内容的复制等联系在一起的，因此包括 Web 开发者在内的很多人根本不愿意去学习 JavaScript。这种情形在 Ajax 复兴时得到了彻底的扭转，Google Map，Gmail 等 Ajax 应用的出现使人们惊叹：原来 JavaScript 还可以做这样的事！很快，大量优秀的 JavaScript/Ajax 框架不断出现，比如 Dojo，Prototype，jQuery，ExtJS 等等。这些代码在给页面带来绚丽的效果的同时，也让开发者看到函数式语言代码的优雅。<a name="minor2.1"><span class="smalltitle"><font size="3">函数式编程风格</font></span></a>在 JavaScript 中，函数本身为一种特殊对象，属于顶层对象，不依赖于任何其他的对象而存在，因此可以将函数作为传出 / 传入参数，可以存储在变量中，以及一切其他对象可以做的事情 ( 因为函数就是对象 )。JavaScript 被称为有着 C 语法的 LISP，LISP 代码的一个显著的特点是大量的括号以及前置的函数名，比如：<div align="left">
<br><a name="listing4"><b><font face="Arial" size="2">清单 4. LISP 中的加法</font></b></a><br>
</div>
<div align="left"><table cellspacing="0" cellpadding="0" width="100%" align="left" border="0"><tbody><tr><td class="code-outline">
{% codeblock %}
				  function map(array, func){   var res = [];   for ( var i = 0, len = array.length; i < len; i++){  res.push(func(array[i])); 	 }   return res;  }  var mapped = map([1, 3, 5, 7, 8],  function (n){   return n = n + 1;  });  print(mapped); 运行这段代码，将会打印： 2,4,6,8,9// 对数组 [1,3,5,7,8] 中每一个元素加 1 
{% endcodeblock %}
</td></tr></tbody></table></div>
<div align="left">
<br> </div>加号在 LISP 中为一个函数，这条表达式的意思为将加号后边的所有数字加起来，并将值返回，JavaScript 可以定义同样的求和函数：<div align="left">
<br><a name="listing5"><b><font face="Arial" size="2">清单 5. JavaScript 中的求和</font></b></a><br>
</div>
<div align="left"><table cellspacing="0" cellpadding="0" width="100%" align="left" border="0"><tbody><tr><td class="code-outline">
{% codeblock %}
				  function map(array, func){   var res = [];   for ( var i = 0, len = array.length; i < len; i++){  res.push(func(array[i])); 	 }   return res;  }  var mapped = map([1, 3, 5, 7, 8],  function (n){   return n = n + 1;  });  print(mapped); 运行这段代码，将会打印： 2,4,6,8,9// 对数组 [1,3,5,7,8] 中每一个元素加 1 
{% endcodeblock %}
</td></tr></tbody></table></div>
<div align="left">
<br> </div>运行此段代码，得到如下结果：<div align="left"><table cellspacing="0" cellpadding="0" width="100%" align="left" border="0"><tbody><tr><td class="code-outline">
{% codeblock %}
				  function map(array, func){   var res = [];   for ( var i = 0, len = array.length; i < len; i++){  res.push(func(array[i])); 	 }   return res;  }  var mapped = map([1, 3, 5, 7, 8],  function (n){   return n = n + 1;  });  print(mapped); 运行这段代码，将会打印： 2,4,6,8,9// 对数组 [1,3,5,7,8] 中每一个元素加 1 
{% endcodeblock %}
</td></tr></tbody></table></div>
<div align="left">
<br> </div>如果要完全模拟函数式编码的风格，我们可以定义一些诸如：<div align="left">
<br><a name="listing6"><b><font face="Arial" size="2">清单 6. 一些简单的函数抽象</font></b></a><br>
</div>
<div align="left"><table cellspacing="0" cellpadding="0" width="100%" align="left" border="0"><tbody><tr><td class="code-outline">
{% codeblock %}
				  function map(array, func){   var res = [];   for ( var i = 0, len = array.length; i < len; i++){  res.push(func(array[i])); 	 }   return res;  }  var mapped = map([1, 3, 5, 7, 8],  function (n){   return n = n + 1;  });  print(mapped); 运行这段代码，将会打印： 2,4,6,8,9// 对数组 [1,3,5,7,8] 中每一个元素加 1 
{% endcodeblock %}
</td></tr></tbody></table></div>
<div align="left">
<br> </div>这样的小函数以及谓词，那样我们写出的代码就更容易被有函数式编程经验的人所接受：<div align="left">
<br><a name="listing7"><b><font face="Arial" size="2">清单 7. 函数式编程风格</font></b></a><br>
</div>
<div align="left"><table cellspacing="0" cellpadding="0" width="100%" align="left" border="0"><tbody><tr><td class="code-outline">
{% codeblock %}
				  function map(array, func){   var res = [];   for ( var i = 0, len = array.length; i < len; i++){  res.push(func(array[i])); 	 }   return res;  }  var mapped = map([1, 3, 5, 7, 8],  function (n){   return n = n + 1;  });  print(mapped); 运行这段代码，将会打印： 2,4,6,8,9// 对数组 [1,3,5,7,8] 中每一个元素加 1 
{% endcodeblock %}
</td></tr></tbody></table></div>
<div align="left">
<br> </div>
<a name="minor2.2"><span class="smalltitle"><font size="3">闭包及其使用</font></span></a>闭包是一个很有趣的主题，当在一个函数 outter 内部定义另一个函数 inner，而 inner 又引用了 outter 作用域内的变量，在 outter 之外使用 inner 函数，则形成了闭包。描述起来虽然比较复杂，在实际编程中却经常无意的使用了闭包特性。<div align="left">
<br><a name="listing8"><b><font face="Arial" size="2">清单 8. 一个闭包的例子</font></b></a><br>
</div>
<div align="left"><table cellspacing="0" cellpadding="0" width="100%" align="left" border="0"><tbody><tr><td class="code-outline">
{% codeblock %}
				  function map(array, func){   var res = [];   for ( var i = 0, len = array.length; i < len; i++){  res.push(func(array[i])); 	 }   return res;  }  var mapped = map([1, 3, 5, 7, 8],  function (n){   return n = n + 1;  });  print(mapped); 运行这段代码，将会打印： 2,4,6,8,9// 对数组 [1,3,5,7,8] 中每一个元素加 1 
{% endcodeblock %}
</td></tr></tbody></table></div>
<div align="left">
<br> </div>匿名函数 function(){return n++;} 中包含对 outter 的局部变量 n 的引用，因此当 outter 返回时，n 的值被保留 ( 不会被垃圾回收机制回收 )，持续调用 o1()，将会改变 n 的值。而 o2 的值并不会随着 o1() 被调用而改变，第一次调用 o2 会得到 n==0 的结果，用面向对象的术语来说，就是 o1 和 o2 为不同的 <em>实例</em>，互不干涉。总的来说，闭包很简单，不是吗？但是，闭包可以带来很多好处，比如我们在 Web 开发中经常用到的：<div align="left">
<br><a name="listing9"><b><font face="Arial" size="2">清单 9. jQuery 中的闭包</font></b></a><br>
</div>
<div align="left"><table cellspacing="0" cellpadding="0" width="100%" align="left" border="0"><tbody><tr><td class="code-outline">
{% codeblock %}
				  function map(array, func){   var res = [];   for ( var i = 0, len = array.length; i < len; i++){  res.push(func(array[i])); 	 }   return res;  }  var mapped = map([1, 3, 5, 7, 8],  function (n){   return n = n + 1;  });  print(mapped); 运行这段代码，将会打印： 2,4,6,8,9// 对数组 [1,3,5,7,8] 中每一个元素加 1 
{% endcodeblock %}
</td></tr></tbody></table></div>
<div align="left">
<br> </div>上边的代码使用了 jQuery 的选择器，找到 id 为 con 的 div 元素，注册计时器，当两秒中之后，将该 div 的背景色设置为灰色。这个代码片段的神奇之处在于，在调用了 setTimeout 函数之后，con 依旧被保持在函数内部，当两秒钟之后，id 为 con 的 div 元素的背景色确实得到了改变。应该注意的是，setTimeout 在调用之后已经返回了，但是 con 没有被释放，这是因为 con 引用了全局作用域里的变量 con。使用闭包可以使我们的代码更加简洁，关于闭包的更详细论述可以在参考信息中找到。由于闭包的特殊性，在使用闭包时一定要小心，我们再来看一个容易令人困惑的例子：<div align="left">
<br><a name="listing10"><b><font face="Arial" size="2">清单 10. 错误的使用闭包</font></b></a><br>
</div>
<div align="left"><table cellspacing="0" cellpadding="0" width="100%" align="left" border="0"><tbody><tr><td class="code-outline">
{% codeblock %}
				  function map(array, func){   var res = [];   for ( var i = 0, len = array.length; i < len; i++){  res.push(func(array[i])); 	 }   return res;  }  var mapped = map([1, 3, 5, 7, 8],  function (n){   return n = n + 1;  });  print(mapped); 运行这段代码，将会打印： 2,4,6,8,9// 对数组 [1,3,5,7,8] 中每一个元素加 1 
{% endcodeblock %}
</td></tr></tbody></table></div>
<div align="left">
<br> </div>上边的代码片段很简单，将多个这样的 JavaScript 对象存入 outter 数组：<div align="left">
<br><a name="listing11"><b><font face="Arial" size="2">清单 11. 匿名对象</font></b></a><br>
</div>
<div align="left"><table cellspacing="0" cellpadding="0" width="100%" align="left" border="0"><tbody><tr><td class="code-outline">
{% codeblock %}
				  function map(array, func){   var res = [];   for ( var i = 0, len = array.length; i < len; i++){  res.push(func(array[i])); 	 }   return res;  }  var mapped = map([1, 3, 5, 7, 8],  function (n){   return n = n + 1;  });  print(mapped); 运行这段代码，将会打印： 2,4,6,8,9// 对数组 [1,3,5,7,8] 中每一个元素加 1 
{% endcodeblock %}
</td></tr></tbody></table></div>
<div align="left">
<br> </div>我们来运行这段代码：<div align="left">
<br><a name="listing12"><b><font face="Arial" size="2">清单 12. 错误的结果</font></b></a><br>
</div>
<div align="left"><table cellspacing="0" cellpadding="0" width="100%" align="left" border="0"><tbody><tr><td class="code-outline">
{% codeblock %}
				  function map(array, func){   var res = [];   for ( var i = 0, len = array.length; i < len; i++){  res.push(func(array[i])); 	 }   return res;  }  var mapped = map([1, 3, 5, 7, 8],  function (n){   return n = n + 1;  });  print(mapped); 运行这段代码，将会打印： 2,4,6,8,9// 对数组 [1,3,5,7,8] 中每一个元素加 1 
{% endcodeblock %}
</td></tr></tbody></table></div>
<div align="left">
<br> </div>出乎意料的是，这段代码将打印： <div align="left"><table cellspacing="0" cellpadding="0" width="100%" align="left" border="0"><tbody><tr><td class="code-outline">
{% codeblock %}
				  function map(array, func){   var res = [];   for ( var i = 0, len = array.length; i < len; i++){  res.push(func(array[i])); 	 }   return res;  }  var mapped = map([1, 3, 5, 7, 8],  function (n){   return n = n + 1;  });  print(mapped); 运行这段代码，将会打印： 2,4,6,8,9// 对数组 [1,3,5,7,8] 中每一个元素加 1 
{% endcodeblock %}
</td></tr></tbody></table></div>
<div align="left">
<br> </div>而不是 1，2，3，4 这样的序列。让我们来看看发生了什么事，每一个内部变量 x 都填写了自己的 no,text,invoke 字段，但是 invoke 却总是打印最后一个 i。原来，我们为 invoke 注册的函数为：<div align="left">
<br><a name="listing13"><b><font face="Arial" size="2">清单 13. 错误的原因</font></b></a><br>
</div>
<div align="left"><table cellspacing="0" cellpadding="0" width="100%" align="left" border="0"><tbody><tr><td class="code-outline">
{% codeblock %}
				  function map(array, func){   var res = [];   for ( var i = 0, len = array.length; i < len; i++){  res.push(func(array[i])); 	 }   return res;  }  var mapped = map([1, 3, 5, 7, 8],  function (n){   return n = n + 1;  });  print(mapped); 运行这段代码，将会打印： 2,4,6,8,9// 对数组 [1,3,5,7,8] 中每一个元素加 1 
{% endcodeblock %}
</td></tr></tbody></table></div>
<div align="left">
<br> </div>每一个 invoke 均是如此，当调用 outter[i].invoke 时，i 的值才会被去到，由于 i 是闭包中的局部变量，for 循环最后退出时的值为 4，因此调用 outter 中的每个元素都会得到 4。因此，我们需要对这个函数进行一些改造：<div align="left">
<br><a name="listing14"><b><font face="Arial" size="2">清单 14. 正确的使用闭包</font></b></a><br>
</div>
<div align="left"><table cellspacing="0" cellpadding="0" width="100%" align="left" border="0"><tbody><tr><td class="code-outline">
{% codeblock %}
				  function map(array, func){   var res = [];   for ( var i = 0, len = array.length; i < len; i++){  res.push(func(array[i])); 	 }   return res;  }  var mapped = map([1, 3, 5, 7, 8],  function (n){   return n = n + 1;  });  print(mapped); 运行这段代码，将会打印： 2,4,6,8,9// 对数组 [1,3,5,7,8] 中每一个元素加 1 
{% endcodeblock %}
</td></tr></tbody></table></div>
<div align="left">
<br> </div>通过将函数 <em>柯里化</em>，我们这次为 outter 的每个元素注册的其实是这样的函数：<div align="left"><table cellspacing="0" cellpadding="0" width="100%" align="left" border="0"><tbody><tr><td class="code-outline">
{% codeblock %}
				  function map(array, func){   var res = [];   for ( var i = 0, len = array.length; i < len; i++){  res.push(func(array[i])); 	 }   return res;  }  var mapped = map([1, 3, 5, 7, 8],  function (n){   return n = n + 1;  });  print(mapped); 运行这段代码，将会打印： 2,4,6,8,9// 对数组 [1,3,5,7,8] 中每一个元素加 1 
{% endcodeblock %}
</td></tr></tbody></table></div>
<div align="left">
<br> </div>这样，就可以得到正确的结果了。<div align="left"><div class="ibm-alternate-rule"><hr></div></div>
<div align="left"><a class="ibm-anchor-up-link" href="/Documents%20and%20Settings/Administrator/Local%20Settings/Temp/Wiz/53b706ec-a9fd-4fb3-b910-d83a214e1556_1.htm#ibm-pcon"><strong>回页首</strong></a></div>
<a name="major3"><span class="atitle">实际应用中的例子</span></a>好了，理论知识已经够多了，我们下面来看看现实世界中的 JavaScript 函数式编程。有很多人为使 JavaScript 具有面向对象风格而做出了很多努力 (JavaScript 本身具有 <em>可编程性</em>)，事实上，面向对象并非必须，使用函数式编程或者两者混合使用可以使代码更加优美，简洁。jQuery 是一个非常优秀 JavaScript/Ajax 框架，小巧，灵活，具有插件机制，事实上，jQuery 的插件非常丰富，从表达验证，客户端图像处理，UI，动画等等。而 jQuery 最大的特点正如其宣称的那样，改变了人们编写 JavaScript 代码的风格。<strong>优雅的 jQuery</strong>有经验的前端开发工程师会发现，平时做的最多的工作有一定的模式：选择一些 DOM 元素，然后将一些规则作用在这些元素上，比如修改样式表，注册事件处理器等。因此 jQuery 实现了完美的 CSS 选择器，并提供跨浏览器的支持：<div align="left">
<br><a name="listing15"><b><font face="Arial" size="2">清单 15. jQuery 选择器</font></b></a><br>
</div>
<div align="left"><table cellspacing="0" cellpadding="0" width="100%" align="left" border="0"><tbody><tr><td class="code-outline">
{% codeblock %}
				  function map(array, func){   var res = [];   for ( var i = 0, len = array.length; i < len; i++){  res.push(func(array[i])); 	 }   return res;  }  var mapped = map([1, 3, 5, 7, 8],  function (n){   return n = n + 1;  });  print(mapped); 运行这段代码，将会打印： 2,4,6,8,9// 对数组 [1,3,5,7,8] 中每一个元素加 1 
{% endcodeblock %}
</td></tr></tbody></table></div>
<div align="left">
<br> </div>当然，jQuery 的选择器规则非常丰富，这里要说的是：用 jQuery 选择器选择出来的 jQuery 对象本质上是一个 List，正如 LISP 语言那样，所有的函数都是基于 List 的。有了这个 List，我们可以做这样的动作：<div align="left">
<br><a name="listing16"><b><font face="Arial" size="2">清单 16. jQuery 操作 jQuery 对象 (List)</font></b></a><br>
</div>
<div align="left"><table cellspacing="0" cellpadding="0" width="100%" align="left" border="0"><tbody><tr><td class="code-outline">
{% codeblock %}
				  function map(array, func){   var res = [];   for ( var i = 0, len = array.length; i < len; i++){  res.push(func(array[i])); 	 }   return res;  }  var mapped = map([1, 3, 5, 7, 8],  function (n){   return n = n + 1;  });  print(mapped); 运行这段代码，将会打印： 2,4,6,8,9// 对数组 [1,3,5,7,8] 中每一个元素加 1 
{% endcodeblock %}
</td></tr></tbody></table></div>
<div align="left">
<br> </div>想当与对 cons 这个 <em>List</em>中的所有元素使用 map( 还记得我们前面提到的 map 吗？ )，操作结果仍然为一个 List。我们可以任意的扩大 / 缩小这个列表，比如：<div align="left">
<br><a name="listing17"><b><font face="Arial" size="2">清单 17. 扩大 / 缩小 jQuery 集合</font></b></a><br>
</div>
<div align="left"><table cellspacing="0" cellpadding="0" width="100%" align="left" border="0"><tbody><tr><td class="code-outline">
{% codeblock %}
				  function map(array, func){   var res = [];   for ( var i = 0, len = array.length; i < len; i++){  res.push(func(array[i])); 	 }   return res;  }  var mapped = map([1, 3, 5, 7, 8],  function (n){   return n = n + 1;  });  print(mapped); 运行这段代码，将会打印： 2,4,6,8,9// 对数组 [1,3,5,7,8] 中每一个元素加 1 
{% endcodeblock %}
</td></tr></tbody></table></div>
<div align="left">
<br> </div>现在我们来看一个小例子，假设有这样一个页面：<div align="left">
<br><a name="listing18"><b><font face="Arial" size="2">清单 18. 页面的 HTML 结构</font></b></a><br>
</div>
<div align="left"><table cellspacing="0" cellpadding="0" width="100%" align="left" border="0"><tbody><tr><td class="code-outline">
{% codeblock %}
				  function map(array, func){   var res = [];   for ( var i = 0, len = array.length; i < len; i++){  res.push(func(array[i])); 	 }   return res;  }  var mapped = map([1, 3, 5, 7, 8],  function (n){   return n = n + 1;  });  print(mapped); 运行这段代码，将会打印： 2,4,6,8,9// 对数组 [1,3,5,7,8] 中每一个元素加 1 
{% endcodeblock %}
</td></tr></tbody></table></div>
<div align="left">
<br> </div>效果如下：<div align="left">
<br><a name="fig1"><b><font face="Arial" size="2">图 1. 过滤之前的效果</font></b></a><br><font face="Arial" size="2"><img height="192" alt="图 1. 过滤之前的效果" src="/images/uploads/2011/01/wpid-e6af90506d9d7f1e8ef9be6a50d689dd_image0021.gif" width="228"></font> <br>
</div>我们通过 jQuery 对包装集进行一次过滤，jQuery 的过滤函数可以使得选择出来的列表对象只保留符合条件的，在这个例子中，我们保留这样的 div，当且仅当这个 div 中包含一个类名为 title 的 span，并且这个 span 的内容为数字：<div align="left">
<br><a name="listing19"><b><font face="Arial" size="2">清单 19. 过滤集合</font></b></a><br>
</div>
<div align="left"><table cellspacing="0" cellpadding="0" width="100%" align="left" border="0"><tbody><tr><td class="code-outline">
{% codeblock %}
				  function map(array, func){   var res = [];   for ( var i = 0, len = array.length; i < len; i++){  res.push(func(array[i])); 	 }   return res;  }  var mapped = map([1, 3, 5, 7, 8],  function (n){   return n = n + 1;  });  print(mapped); 运行这段代码，将会打印： 2,4,6,8,9// 对数组 [1,3,5,7,8] 中每一个元素加 1 
{% endcodeblock %}
</td></tr></tbody></table></div>
<div align="left">
<br> </div>效果如下图所示：<div align="left">
<br><a name="fig2"><b><font face="Arial" size="2">图 2. 过滤之后的效果</font></b></a><br><font face="Arial" size="2"><img height="137" alt="图 2. 过滤之后的效果" src="/images/uploads/2011/01/wpid-e6af90506d9d7f1e8ef9be6a50d689dd_image0031.gif" width="197"></font> <br>
</div>我们再来看看 jQuery 中对数组的操作 ( 本质上来讲，JavaScript 中的数组跟 List 是很类似的 )，比如我们在前面的例子中提到的 map 函数，过滤器等：<div align="left">
<br><a name="listing20"><b><font face="Arial" size="2">清单 20. jQuery 对数组的函数式操作</font></b></a><br>
</div>
<div align="left"><table cellspacing="0" cellpadding="0" width="100%" align="left" border="0"><tbody><tr><td class="code-outline">
{% codeblock %}
				  function map(array, func){   var res = [];   for ( var i = 0, len = array.length; i < len; i++){  res.push(func(array[i])); 	 }   return res;  }  var mapped = map([1, 3, 5, 7, 8],  function (n){   return n = n + 1;  });  print(mapped); 运行这段代码，将会打印： 2,4,6,8,9// 对数组 [1,3,5,7,8] 中每一个元素加 1 
{% endcodeblock %}
</td></tr></tbody></table></div>
<div align="left">
<br> </div>mapped 将被赋值为 :<div align="left"><table cellspacing="0" cellpadding="0" width="100%" align="left" border="0"><tbody><tr><td class="code-outline">
{% codeblock %}
				  function map(array, func){   var res = [];   for ( var i = 0, len = array.length; i < len; i++){  res.push(func(array[i])); 	 }   return res;  }  var mapped = map([1, 3, 5, 7, 8],  function (n){   return n = n + 1;  });  print(mapped); 运行这段代码，将会打印： 2,4,6,8,9// 对数组 [1,3,5,7,8] 中每一个元素加 1 
{% endcodeblock %}
</td></tr></tbody></table></div>
<div align="left">
<br> </div>而 greped 则为：<div align="left"><table cellspacing="0" cellpadding="0" width="100%" align="left" border="0"><tbody><tr><td class="code-outline">
{% codeblock %}
				  function map(array, func){   var res = [];   for ( var i = 0, len = array.length; i < len; i++){  res.push(func(array[i])); 	 }   return res;  }  var mapped = map([1, 3, 5, 7, 8],  function (n){   return n = n + 1;  });  print(mapped); 运行这段代码，将会打印： 2,4,6,8,9// 对数组 [1,3,5,7,8] 中每一个元素加 1 
{% endcodeblock %}
</td></tr></tbody></table></div>
<div align="left">
<br> </div>我们再来看一个更接近实际的例子：<div align="left">
<br><a name="listing21"><b><font face="Arial" size="2">清单 21. 一个页面刷新的例子</font></b></a><br>
</div>
<div align="left"><table cellspacing="0" cellpadding="0" width="100%" align="left" border="0"><tbody><tr><td class="code-outline">
{% codeblock %}
				  function map(array, func){   var res = [];   for ( var i = 0, len = array.length; i < len; i++){  res.push(func(array[i])); 	 }   return res;  }  var mapped = map([1, 3, 5, 7, 8],  function (n){   return n = n + 1;  });  print(mapped); 运行这段代码，将会打印： 2,4,6,8,9// 对数组 [1,3,5,7,8] 中每一个元素加 1 
{% endcodeblock %}
</td></tr></tbody></table></div>
<div align="left">
<br> </div>首先声明一个柯里化的函数 update，这个函数会将传入的参数作为选择器的 id，并更新这个 div 的内容 (innerHTML)。然后声明一个函数 refresh，refresh 接受两个参数，第一个参数为服务器端的 url，第二个参数为一个回调函数，当服务器端成功返回时，调用该函数。然后我们陆续调用三次 refresh，每次的 url 和 id 都不同，这样可以将 content1,content2,conetent3 的内容通过异步方式更新。这种模式在实际的编程中相当有效，因为关于如何与服务器通信，以及如果选取页面内容的部分被很好的抽象成函数，现在我们需要做的就是将 url 和 id 传递给 refresh，即可完成需要的动作。函数式编程在很大程度上降低了这个过程的复杂性，这正是我们选择使用该思想的最终原因。<div align="left"><div class="ibm-alternate-rule"><hr></div></div>
<div align="left"><a class="ibm-anchor-up-link" href="/Documents%20and%20Settings/Administrator/Local%20Settings/Temp/Wiz/53b706ec-a9fd-4fb3-b910-d83a214e1556_1.htm#ibm-pcon"><strong>回页首</strong></a></div>
<a name="major4"><span class="atitle">结束语</span></a>实际的应用中，不会囿于函数式或者面向对象，通常是两者混合使用，事实上，很多主流的面向对象语言都在不断的完善自己，比如加入一些函数式编程语言的特征等，JavaScript 中，这两者得到了良好的结合，代码不但可以非常简单，优美，而且更易于调试。文中仅仅提到 jQuery 特征的一小部分，如果感兴趣，则可以在参考资料中找到更多的链接，jQuery 非常的流行，因此你可以找到很多论述如何使用它的文章。<!-- CMA ID: 497588 --><!-- Site ID: 10 --><!-- XSLT stylesheet used to transform this file:  dw-article-6.0-beta.xsl --><div align="left">
<br> </div>
<a name="resources"><span class="atitle">参考资料 </span></a><ul>
<li><div align="left">
<a href="http://jquery.org/">jQuery</a>官方网站的地址，可以下载到最新的 jQuery 库。<br><br>
</div></li>
<li><div align="left">
<a href="http://www.jibbering.com/faq/faq_notes/closures.html">JavaScript 中的闭包</a>：一篇优秀的关于 JavaScript 闭包的论述。<br><br>
</div></li>
<li><div align="left">文中提到的 <a href="http://daiyuwen.freeshell.org/gb/rol/roots_of_lisp.html">LISP 之根源</a>的译文，该文详细的描述了 LISP 的其中基本原语，很好的解释了 LISP 的 <em>可编程性</em>。<br><br>
</div></li>
<li><div align="left">
<a href="http://www.hunlock.com/blogs/Functional_Javascript">函数式编程的基本概念</a>：一篇关于 JavaScript 函数式编程的基本概念的文章。<br><br>
</div></li>
<li><div align="left">“<a href="http://www.ibm.com/developerworks/cn/web/wa-jsframeworks/">JavaScript 框架比较</a>”：在本文中，您将了解如何通过 JavaScript 框架更轻松、更快速地创建具有高度交互性和响应性的 Web 站点和 Web 应用程序。<br><br>
</div></li>
<li><div align="left">“<a href="http://www.ibm.com/developerworks/cn/web/lp/jstoolkit/">JavaScript 开发工具包 </a>”：本专题为您收集了一些和目前业界比较流行的 JavaScript 开发工具包相关的资源，从初级的入门介绍到高级的使用以及和其他开发语言、软件集成的内容。<br><br>
</div></li>
<li><div align="left">developerWorks <a href="http://www.ibm.com/developerworks/cn/offers/techbriefings/">技术活动</a>和<a href="http://www.ibm.com/developerworks/cn/swi/">网络广播</a>：随时关注 developerWorks 技术活动和网络广播。 <br><br>
</div></li>
<li><div align="left">
<a href="http://www.ibm.com/developerworks/cn/web/">developerWorks Web development 专区</a>：通过专门关于 Web 技术的文章和教程，扩展您在网站开发方面的技能。<br><br>
</div></li>
<li><div align="left">
<a href="http://www.ibm.com/developerworks/cn/ajax/">developerWorks Ajax 资源中心</a>：这是有关 Ajax 编程模型信息的一站式中心，包括很多文档、教程、论坛、blog、wiki 和新闻。任何 Ajax 的新信息都能在这里找到。<br><br>
</div></li>
<li><div align="left">
<a href="http://www.ibm.com/developerworks/cn/web20/">developerWorks Web 2.0 资源中心</a>，这是有关 Web 2.0 相关信息的一站式中心，包括大量 Web 2.0 技术文章、教程、下载和相关技术资源。您还可以通过 <a href="http://www.ibm.com/developerworks/cn/web20/newto/">Web 2.0 新手入门</a> 栏目，迅速了解 Web 2.0 的相关概念。<br><br>
</div></li>
</ul>
<a name="author"><span class="atitle">关于作者</span></a><div align="left"><div class="ibm-container ibm-portrait-module ibm-alternate-two"><div class="ibm-container-body">
<a name="author1"></a>邱俊涛，毕业于昆明理工大学计算机科学与技术专业，对机械控制、电子、人工智能等方面有浓厚的兴趣，对计算机科学的底层比较熟悉。喜欢 C/Java/Python 等语言。</div></div></div>
<div align="left"> </div>
<div><a title="Wiz，个人知识管理，PKM。" href="http://wiz.cn">通过Wiz发布</a></div>
