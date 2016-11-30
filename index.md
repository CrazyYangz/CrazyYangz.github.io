---
layout: default
title: Young的博客
---
{% comment %}
=======================
The following part extracts all the tags from your posts and sort tags, so that you do not need to manually collect your tags to a place.
=======================
{% endcomment %}
{% assign rawtags = "" %}
{% for post in site.posts %}
	{% assign ttags = post.tags | join:'|' | append:'|' %}
	{% assign rawtags = rawtags | append:ttags %}
{% endfor %}
{% assign rawtags = rawtags | split:'|' | sort %}

{% comment %}
=======================
The following part removes dulpicated tags and invalid tags like blank tag.
=======================
{% endcomment %}
{% assign tags = "" %}
{% for tag in rawtags %}
	{% if tag != "" %}
		{% if tags == "" %}
			{% assign tags = tag | split:'|' %}
		{% endif %}
		{% unless tags contains tag %}
			{% assign tags = tags | join:'|' | append:'|' | append:tag | split:'|' %}
		{% endunless %}
	{% endif %}
{% endfor %}


{% for post in site.posts %}
<article class="article article-type-post">
	<div class="article-inner">
		<header class="article-header">
			<h1>
				<a href="{{ site.baseurl }}{{ post.url }}" class="article-title">{{ post.title }}</a>
			</h1>
		</header>
		<div class="article-entry">
			{{ post.excerpt }}
			<!-- 判断是否完全显示，若没有则添加more -->
			{% if post.content contains site.excerpt_separator %}
			<p class="article-more-link">
				<a href="{{ site.baseurl }}{{ post.url }}" class="article-more-a">more >></a>
			</p>
			{% endif %}
		</div>
		<div class="article-info article-info-index">
			<a href="" class="archive-article-date">
				<i class="iconfont">&#xe62d;</i>
				<span>{{ post.date | date: "%Y-%m-%d" }}</span>
			</a>
			<div class="article-tag tagcloud">
				<i class="iconfont">&#xe62c;</i>
				<ul class="article-tag-list">
					{% for tag in post.tags %}
					<li class="article-tag-list-item">
						<a href="#{{ tag | slugify }}" class="color3"> {{ tag }} </a>
					</li>
					{% endfor %}
				</ul>
			</div>
		</div>
	</div>
</article>
{% endfor %}