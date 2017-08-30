---
layout: page
title: Screencasting
permalink: /screencasting/
---
<body>
{% for post in site.posts %}
		{% if post.type == "screencast" %}
			<div class="screencast-list-title">
				<h3>{{post.title}}</h3>
				<p>{{post.description}}</p>
				<p>{{post.excerpt}}</p>
			</div>
			<!--
			<iframe width="560" height="315" src="https://ia801505.us.archive.org/22/items/{{post.archiveurl}}" frameborder="0" allowfullscreen></iframe>
			-->
			<iframe width="560" height="315" src="https://www.youtube.com/embed/{{post.youtubeurl}}" frameborder="0" allowfullscreen></iframe>
		{% endif %}
{% endfor %}
</body>
<br>
<br>
<br>
