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
			<iframe src="https://archive.org/embed/{{post.archiveurl}}" width="640" height="480" frameborder="0" webkitallowfullscreen="true" mozallowfullscreen="true" allowfullscreen></iframe>
		{% endif %}
{% endfor %}
</body>

