--- 
categories: 
  - JavaScript
comments: true
layout: post
published: true
status: publish
tags: 
  - css
  - firefox
  - google
  - ie
  - java
  - JavaScript
  - 浏览器
title: firefox中用js提交表单
type: post
---
<div class="postcontent">          <span class="Apple-style-span">            <span class="Apple-style-span">1.document.forms.from.submit(); <!--more--><br>document.form.sumbit(); <br>document.form.submit.click(); <br>this.form.submit(); <br>以上几种形式的js表单提交在firefox浏览器下是不起作用的 <br>2.必须遵循w3c标准： <br>1).获得form时应使用getElementById()方法 <br>2).用.submit()方法提交表单 <br>3).button的name/id绝对不能命名为”submit” <br>4).form中所有的组件（按钮，文本框等）的name/id也不能命名为”submit” </span>          </span>                  <span class="Apple-style-span">            <span class="Apple-style-span">              <span class="Apple-converted-space">                <span class="Apple-style-span">                  <span class="Apple-style-span"># 当提交按钮的name 或者 id为submit时候，用js 提交表单，表单名.submit()时候会报一个错误，提示对象不支持此属性或办法。 <br>解决方法是修改提交按钮的 name 或者 id 不要与 submit或者action同名即可。 <br>那么，请问为什么 当提交按钮的 name 或者 id为submit或者 action的时候 js提交表单会报错呢？这难道是 一个bug？ <br>高手们请指教。。。。</span>                </span>              </span>            </span>          </span>                  <span class="Apple-style-span">            <span class="Apple-style-span">              <span class="Apple-converted-space">                <span class="Apple-style-span">                  <span class="Apple-style-span">！<span class="Apple-style-span">                      <span class="Apple-style-span">                        <span class="Apple-style-span">                          <span class="Apple-style-span">因为”表单名.submit()提交”这种写法本身就是不符合W3C标准的规定的，在IE下没有报错因为IE支持这种写法，但是如果在FF下就会报错，要写成”document.getElementById(‘form id’).submit()”的？</span>                        </span>                      </span>                    </span>                  </span>                </span>              </span>            </span>          </span>                  <span class="Apple-style-span">            <span class="Apple-style-span">              <span class="Apple-converted-space">                <span class="Apple-style-span">                  <span class="Apple-style-span">                    <span class="Apple-style-span">                      <span class="Apple-style-span">                        <span class="Apple-style-span">                          <span class="Apple-style-span"># <span class="Apple-style-span">                              <span class="Apple-style-span">我在项目中发现<input type=”submit”/>与<img src=”123.gif” onclick=”submit();”> <br>得出的效果截然不同， 谁能告诉我这两着有合不同 <br>我又如何能用图片来替代原有的提交按钮</span>                            </span>                          </span>                        </span>                      </span>                    </span>                  </span>                </span>              </span>            </span>          </span>                  <span class="Apple-style-span">            <span class="Apple-style-span">              <span class="Apple-converted-space">                <span class="Apple-style-span">                  <span class="Apple-style-span">                    <span class="Apple-style-span">                      <span class="Apple-style-span">                        <span class="Apple-style-span">                          <span class="Apple-style-span">                            <span class="Apple-style-span">                              <span class="Apple-style-span">！<span class="Apple-style-span">                                  <span class="Apple-style-span"><input type=”submit” />是说这是一个按钮,它的是一个提交按钮.当点击它时,它会自动将它所在的表单进行提交. </span>                                </span>                              </span>                            </span>                          </span>                        </span>                      </span>                    </span>                  </span>                </span>              </span>            </span>          </span>        <h2 class="related_post_title">相关阅读</h2>
<ul class="related_post">
<li>2010年06月16日 -- <a href="http://ruyihe.com/blog/2010/06/javascript%E4%B8%AD%E6%9C%80%E5%B8%B8%E7%94%A8%E7%9A%8455%E4%B8%AA%E7%BB%8F%E5%85%B8%E6%8A%80%E5%B7%A7/" title="Javascript中最常用的55个经典技巧">Javascript中最常用的55个经典技巧</a>
</li>
<li>2010年06月14日 -- <a href="http://ruyihe.com/blog/2010/06/js%E6%B5%9C%E5%AC%A9%E6%AC%A2on_attr_change%E9%94%9B%E5%B2%80%E6%B4%83%E9%8D%9A%EE%84%80%E5%8E%93%E7%BB%B1%E7%8A%B2%E7%9D%98%E9%8E%AC%D1%85%E6%AE%91%E9%8D%99%E6%A8%BA%E5%AF%B2%E9%94%9B%E5%B1%BC%E4%BA%92%E6%B8%9A%E5%9E%AE%E7%9D%98%E9%8E%AC%D1%83%E5%BD%89%E9%8D%96%E6%A0%AB%E6%AE%91/" title="js事件On_Attr_Change，监听元素属性的变化，以便属性变化的时候作出处理【推荐】">js事件On_Attr_Change，监听元素属性的变化，以便属性变化的时候作出处理【推荐】</a>
</li>
<li>2010年05月19日 -- <a href="http://ruyihe.com/blog/2010/05/70%E4%B8%AA%E6%96%B0%E9%B2%9C%E5%AE%9E%E7%94%A8%E7%9A%84javascript%E5%92%8Cajax%E6%8A%80%E6%9C%AF/" title="70个新鲜实用的JavaScript和Ajax技术">70个新鲜实用的JavaScript和Ajax技术</a>
</li>
<li>2010年05月19日 -- <a href="http://ruyihe.com/blog/2010/05/10%E7%BB%89%E5%B3%A7avascript%E9%90%97%E8%A7%84%E6%99%A5%E7%80%B9%E7%82%B0%E7%B7%A5/" title="10种JavaScript特效实例">10种JavaScript特效实例</a>
</li>
<li>2010年05月18日 -- <a href="http://ruyihe.com/blog/2010/05/10%E6%B6%93%EE%81%88%E6%BD%AA%E7%94%AF%E5%91%8A%EE%97%97%E9%90%A8%E5%88%9Fjax%E9%8D%99%E5%A6%80avascript%E7%80%B9%E7%82%B0%E7%B7%A5%E7%92%A7%E5%8B%AC%E7%B0%AE%E7%BC%83%E6%88%A0%E7%8F%AF/" title="10个非常棒的Ajax及Javascript实例资源网站">10个非常棒的Ajax及Javascript实例资源网站</a>
</li>
<li>2010年05月18日 -- <a href="http://ruyihe.com/blog/2010/05/%E6%80%8E%E6%A0%B7%E5%9C%A8%E8%A1%A8%E5%8D%95%E6%8F%90%E4%BA%A4%E5%89%8D%E7%94%A8js%E4%BF%AE%E6%94%B9%E8%A1%A8%E5%8D%95%E6%95%B0%E6%8D%AE%E5%92%8C%E6%8F%90%E4%BA%A4%E5%9C%B0%E5%9D%80action-%E5%90%AB/" title="怎样在表单提交前用JS修改表单数据和提交地址action 含实例">怎样在表单提交前用JS修改表单数据和提交地址action 含实例</a>
</li>
<li>2010年05月13日 -- <a href="http://ruyihe.com/blog/2010/05/70%E4%B8%AA%E6%96%B0%E9%B2%9C%E5%AE%9E%E7%94%A8%E7%9A%84javascript%E5%92%8Cajax%E6%8A%80%E6%9C%AF%E3%80%90%E6%8E%A8%E8%8D%90%E3%80%91/" title="70个新鲜实用的JavaScript和Ajax技术【推荐】">70个新鲜实用的JavaScript和Ajax技术【推荐】</a>
</li>
<li>2010年05月13日 -- <a href="http://ruyihe.com/blog/2010/05/js%E5%87%BD%E6%95%B0%E7%BB%9F%E4%B8%80%E4%BF%AE%E6%94%B9css%E6%A0%B7%E5%BC%8F%E8%A1%A8%E4%B8%AD%E7%9A%84%E5%B1%9E%E6%80%A7%E5%80%BC%EF%BC%8C%E5%85%BC%E5%AE%B9ff%E5%92%8Cie%EF%BC%8C%E5%BC%BA%E5%8C%96/" title="js函数统一修改css样式表中的属性值，兼容FF和IE，强化版含实例">js函数统一修改css样式表中的属性值，兼容FF和IE，强化版含实例</a>
</li>
<li>2010年05月13日 -- <a href="http://ruyihe.com/blog/2010/05/%E9%90%A2%E2%95%A6avascript%E9%8E%B7%E6%A0%A7%E5%A7%A9div%E7%81%9E%E5%82%A6%E7%B4%9D%E7%BB%AB%E8%AE%B3%E6%8A%80google%E9%90%A8%E5%8B%AD%E7%B6%89%E6%A4%A4%E9%9D%9B%E7%AB%B7%E7%81%9E%E2%82%AC%E9%94%9B%E5%B1%BE%E6%95%AE%E9%8E%B8%E4%B9%ABirefox%E9%94%9B%E5%B1%BE%E7%89%B1%E5%AF%AE%E5%BF%93%E5%BD%B2/" title="用javascript拖动div层，类似google的网页布局，支持firefox，样式可自定义">用javascript拖动div层，类似google的网页布局，支持firefox，样式可自定义</a>
</li>
</ul>
</div>
<div><a title="Wiz，个人知识管理，PKM。" href="http://wiz.cn">通过Wiz发布</a></div>
