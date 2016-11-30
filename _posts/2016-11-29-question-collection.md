---
layout:			post
title:			关于Jekyll excerpt的一些设置
date:   		2016-11-29
categories: jekyll
tags: 			jekyll
permalink: 	/:year/:month/:day/:categories-:year-:month-:day
---
<blockquote>
Ps：大括号 <strong>{ }</strong> 是Jekyll中的转义字符，因此输出大括号时，应使用:
<code>
{% assign openTag = '{%' %}
{{ openTag }} raw %}
	content
{{ openTag }} endraw %}。
</code>
</blockquote>

Jekyll设置列表页的摘录，使用
<code>{% raw %}{{ post.excerpt }}{% endraw %}</code>
，使用方法如下：

{% highlight html linenos %}
{% raw %}
{% for post in site.posts %}
  <li>
    <span class="post-meta">{{ post.date | date: "%Y-%m-%d" }}</span>
    <h2>
      <a class="post-link" href="{{ post.url | prepend: site.baseurl }}"> post.title }}</a>
    </h2>
    {{ post.excerpt }} <!--在这里添加摘录-->
  </li>
{% endfor %}
{% endraw %}
{% endhighlight %}

<code>{% raw %}{{ post.excerpt }}{% endraw %}</code>标签添加在第七行，Jekyll会根据post的内容的第一个段落生成摘录,样式类似于：<!-- more -->

<img src="{{ site.baseurl }}/assets/blogImg/jekyll_excerpt.png" alt="">

这样看起来其实已经不错了，但是如果要是能自定义摘录地长度，是不是更酷一点？

<strong>方法如下：</strong>
<ul>
	<li>
		打开"_config.yml"，在任意处（建议在#site setting下）添加
		<code>excerpt_separator: "&lt;!--more--&gt;"</code>
	</li>
	<li>
		打开post在任意处添加
		<code>&lt;!--more--&gt;</code>
		标签，在此标签之前的内容将会作为摘要在列表中显示。
	</li>
</ul>

这样就实现了摘要的显示自定义，如果你仔细的话会发现没有 more，代码如下：
{% highlight html linenos %}
{% raw %}
{% for post in site.posts %}
  <li>
    <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>
    <h2>
      <a class="post-link" href="{{ post.url | prepend: site.baseurl }}"> post.title }}</a>
    </h2>
    {{ post.excerpt }}
    {% if post.content contains site.excerpt_separator %}
      <a href="{{ post.url | prepend: site.baseurl }}">...Read more</a>
    {% endif %}
  </li>
{% endfor %}
{% endraw %}
{% endhighlight %}