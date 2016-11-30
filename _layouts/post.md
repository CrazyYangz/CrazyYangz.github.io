<!DOCTYPE html>
<html lang="en">
<head>
	{% include head.html %}
</head>
<body>
	<div id="container">
		{% include left_col.html %}
		<div class="right-col">
			<div class="right-wrap">
				<article class="article article-type-post">
					<div class="article-inner">
						<header class="article-header">
							<h1 class="article-title" style="padding-top: 1px;">{{ page.title }}</h1>
						</header>
						<div class="article-entry">
							{{ content }}
						</div>
						<div class="article-info article-info-index">
							<a class="archive-article-date">
								<i class="iconfont">&#xe62d;</i>
								<span>{{ page.date | date: "%Y-%m-%d" }}</span>
							</a>
							<div class="article-tag tagcloud">
								<i class="iconfont">&#xe62c;</i>
								<ul class="article-tag-list">
									{% for tag in page.tags %}
									<li class="article-tag-list-item">
										<a href="#{{ tag | slugify }}" class="color3"> {{ tag }} </a>
									</li>
									{% endfor %}
								</ul>
							</div>
						</div>
					</div>
				</article>
				<nav id="article-nav">
					{% if page.previous %}
					<a href="{{ site.url}}{{ page.previous.url }}" id="article-nav-newer" class="article-nav-link-wrap">
						<i class="iconfont">&#xe61d;</i>
						<div class="article-nav-title">{{ page.previous.title }}</div>
					</a>
					{% endif %}
					{% if page.next %}
					<a href="{{ site.url}}{{ page.next.url }}" id="article-nav-older" class="article-nav-link-wrap">
						<div class="article-nav-title">{{ page.next.title }}</div>
						<i class="iconfont">&#xe633;</i>
					</a>
					{% endif %}
				</nav>
				<div class="duoshuo">
					<!-- 多说评论框 start -->
					<div class="ds-thread" data-thread-key="{{ page.id }}" data-title="{{ page.title }}" data-url="{{ site.url }}{{ page.url }}"></div>
					<!-- 多说评论框 end -->
					<!-- 多说公共JS代码 start (一个网页只需插入一次) -->
					<script type="text/javascript">
					var duoshuoQuery = {short_name:"yangzhen"};
						(function() {
							var ds = document.createElement('script');
							ds.type = 'text/javascript';ds.async = true;
							ds.src = (document.location.protocol == 'https:' ? 'https:' : 'http:') + '//static.duoshuo.com/embed.js';
							ds.charset = 'UTF-8';
							(document.getElementsByTagName('head')[0]
							 || document.getElementsByTagName('body')[0]).appendChild(ds);
						})();
						</script>
					<!-- 多说公共JS代码 end -->
				</div>
			</div>
			{% include footer.html %}
		</div>
	</div>
</body>
</html>