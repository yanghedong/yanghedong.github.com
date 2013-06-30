---
layout: post
title: 在LaTeX中设置背景颜色
description: 如何设置某种环境的中文背景颜色
category: 备忘
tags: [Latex]
---
{% include JB/setup %}

在$\LaTeX$中设置背景颜色的方法有多种，比如用```\colorbox{color}{text}```命令可以设置句子的背景颜色，
利用soul包的```\hl{}```命令可以设置段落的背景颜色，利用ulem包可以设置跨段落的背景颜色
（如下）等。

```latex
\usepackage{ulem} % use normalem to protect \emph
\newcommand\hl[1]{\bgroup\markoverwith
  {\textcolor{#1}{\rule[-.5ex]{2pt}{2.5ex}}}\ULon}
```

如果需要设置包含环境的段落的背景颜色，则需要利用到xparse包。

```latex
\usepackage{xparse}
\makeatletter\NewDocumentEnvironment{coloredbox}{m}{ %
\begin{lrbox}{\@tempboxa}\begin{minipage}{\columnwidth}
}{ %
  \end{minipage}\end{lrbox}%
   \colorbox{#1}{\usebox{\@tempboxa}}%
}\makeatother
\newenvironment{biaozhun}{\begin{coloredbox}{green}}{\end{coloredbox}}
```

如果不想把颜色作为参数，可以直接利用下面的命令（此时它不须xparse包）。

```
\definecolor{MyGray}{rgb}{0.96,0.97,0.98}
\makeatletter\newenvironment{graybox}{ %
   \begin{lrbox}{\@tempboxa}\begin{minipage}{\columnwidth}}{\end{minipage}\end{lrbox}%
   \colorbox{MyGray}{\usebox{\@tempboxa}}
}\makeatother
```

