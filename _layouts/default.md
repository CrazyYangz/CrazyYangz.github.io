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
				{{ content }}
			</div>
			{% include footer.html %}
		</div>
	</div>

</body>
</html>