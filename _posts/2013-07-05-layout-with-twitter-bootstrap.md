---
layout: post
title: 利用twitter bootstrap设置页面的布局
description: "twitter boostrap的使用初步"
category: 备忘
tags: [技术]
---
{% include JB/setup %}

一直不太满意jekyll生成的界面，主要的原因是有些文字内容可以显示在页面的右（或左）边栏上，而不必一直排在页面的末尾。

今天下午试了一下twitter
bootstrap包，发现功能太强大了，是一个完整的UI设计包。

我只关心如何将页面切分，来完成想要的内容布局，所以只看了一了页面的部分。[它将页面分成了12列](twitter.github.io/bootstrap/scaffolding.html)，由此只需要指定内容显示位置的行，以及内容所跨的列数，整个内容就可以正确地显示了，并且可以根据屏幕宽窄浮动起来。比如本页面，文章的内容占10列，而右边的分类信息与标签信息只占两列。

这个功能非常类似$\LaTeX$里面制造海报的baposter包或beamer/beamerposter包。

参考资源
* [http://twitter.github.io/bootstrap/scaffolding.html]
