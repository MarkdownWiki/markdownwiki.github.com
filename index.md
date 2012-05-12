---
layout: page
title:
tagline:
---
{% include JB/setup %}

<div class="row-fluid">
	<div class="span8">
		<h1>{{site.posts[0].title}}</h1>
		<hr>
		{{site.posts[0].content}}
	</div>
	<div class="span4">
		<h3>Blog Posts</h3>
		<ul class="nav nav-pills nav-stacked">
  		{% for post in site.posts %}
    		<li><a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  		{% endfor %}
		</ul>
	</div>
</div>




