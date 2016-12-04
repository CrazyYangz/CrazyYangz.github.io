<!DOCTYPE html>
<html lang="en">
<head>
	{% include head.html %}
</head>
<body>
	<div id="container">
		{% include left_col.html %}
		<div class="right-col mid-col">
			<div class="right-wrap">
				{{ content }}
			</div>
			{% include footer.html %}
		</div>
	</div>

	<script>
		var yiliaConfig = {
			mathjax: false,
			animate: true,
			isHome: false,
			isPost: false,
			isArchive: false,
			isTag: true,
			isCategory: false,
			open_in_new: true,
			root: "/",
			innerArchive: true
		}
	</script>
	<script src="/assets/js/main.js"></script>
	{% include tools_col.html %}
</body>
</html>