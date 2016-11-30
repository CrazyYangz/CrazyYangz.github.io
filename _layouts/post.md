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
			</div>
			{% include footer.html %}
		</div>
	</div>
</body>
</html>