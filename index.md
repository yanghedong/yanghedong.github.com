---
layout: page
title: 备忘与思考
---
{% include JB/setup %}


{% for post in site.posts %}
<div class="post">
  <h3 class="title"><a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a><span class="date">{{ post.date | date_to_string }}</span></h3>
  <p>{{ post.description }}</p>
  <div class="more"><a href="{{ BASE_PATH }}{{ post.url }}" alt="read more...">阅读全文</a></div>
</div>
{% endfor %}


<div class="span4">
 <div id="sidebar">
  <div id="recentcomments" class="dsq-widget">
   <h2 class="dsq-widget-title">Recent Comments</h2>
   <script type="text/javascript" src="http://forgetnot.disqus.com/recent_comments_widget.js?num_items=5&hide_avatars=0&avatar_size=32&excerpt_length=200"></script>
  </div>
 </div>
</div>
