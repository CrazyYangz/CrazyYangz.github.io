---
layout: default
title: Yangzhen的博客
---
<h2>{{ page.title }}</h2>

<ul>
	{% for post in site.posts %}
	<li>
		<a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a>
		<p>{{ post.excerpt }}</p>

		<span>{{ post.date | date_to_string }}</span>
	</li>
	{% endfor %}
</ul>