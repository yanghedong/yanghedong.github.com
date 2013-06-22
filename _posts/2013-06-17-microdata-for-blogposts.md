---
layout: post
title: 日志与微数据
description: "微数据的基本知识，以及日志页面的微数据的生成"
category: 备忘
tags: [Blog, Microdata]
---
{% include JB/setup %}
向google提交页面之后，得到提醒说他们喜欢页面嵌入微数据。对微数据知之甚少，这jykll生成的页面似乎也对微数据支持不好。
根据文后收集的资料，对日志页面增加了微数据，不知这样增加是否正确。现将代码显示在此，供参考。

对\_includes/themes/twitter/page.html的改动

```
  	1 	+<div itemscope itemtype="http://www.schema.org/Blog">
  	2 	+  <div style="display:none">
  	3 	+    <span itemprop="author" itemscope itemtype="http://www.schema.org/Person">
  	4 	+      <span itemprop="name">Hedong Yang</span>
  	5 	+    </span>
  	6 	+    <span itemprop="description">A personal blog publishes some
  	7 	+      technical notes which may be useful for others.</span>
  	8 	+    <span itemprop="url">http://yanghedong.github.com</span>
  	9 	+  </div>
1 	10 	 <div class="page-header">
2 	  	-  <h1>{ { page.title }} { % if page.tagline %} <small>{ { page.tagline }}</small>{ % endif %}</h1>
  	11 	+  <h1 itemprop="headline">{ { page.title }} { % if page.tagline %} <small>{ { page.tagline }}</small>{ % endif %}</h1>
3 	12 	 </div>
4 	13 	 
5 	14 	 <div class="row-fluid">
6 	  	-  <div class="span12">
  	15 	+  <div class="span12" itemprop="text">
7 	16 	     { { content }}
8 	17 	   </div>
9 	18 	 </div>
  	19 	+</div>
```

对\_includes/themes/twitter/post.html的改动

```
  	1 	+<div  itemscope itemtype="http://www.schema.org/BlogPosting">
1 	2 	 <div class="page-header">
2 	  	-  <h1>{ { page.title }} { % if page.tagline %}<small>{ {page.tagline}}</small>{ % endif %}</h1>
  	3 	+  <h1 itemprop="headline">{ { page.title }} { % if page.tagline %}<small>{ {page.tagline}}</small>{ % endif %}</h1>
3 	4 	 </div>
4 	  	-
5 	5 	 <div class="row-fluid post-full">
6 	6 	   <div class="span12">
7 	  	-    <div class="date">
8 	  	-      <span>{ { page.date | date_to_long_string }}</span>
  	7 	+    <div class="date" >
  	8 	+    <span itemprop="author" itemscope
  	9 	+      itemtype="http://schema.org/Person"><span itemprop="name">{ { site.author.name }}</span>
  	10 	+      </span>, <span style="display:none" itemprop="description">{ { page.description }}</span>
  	11 	+      <span itemprop="dateCreated">{ { page.date | date_to_long_string }}</span>
9 	12 	     </div>
10 	  	-    <div class="content">
  	13 	+    <div class="content" itemprop="text">
11 	14 	       { { content }}
12 	15 	     </div>
13 	16 	 
48 	51 	     { % include JB/comments %}
49 	52 	   </div>
50 	53 	 </div>
  	54 	+</div> 
```

1. [http://www.schema.org/]
1. [http://www.w3.org/html/wg/drafts/microdata/master/]
1. [http://support.google.com/webmasters/bin/answer.py?hl=en&answer=176035]

