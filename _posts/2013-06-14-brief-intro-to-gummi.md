---
layout: post
title: Gummi简介
description: "Gummi的功能简介以及使用技巧"
category: 备忘
tags: [Gummi, LaTeX, WYSIWYG]
---
{% include JB/setup %}

$\LaTeX$主张所思即所得(WYTIWYG)，所以主流的编辑器都是标准的文本编辑器（有些可能会带有针对$\LaTeX$语法或主题的插件）。
编辑之后的源代码文件（即扩展名为.tex的文件），往往利用latex, pdflatex或xelatex进行编译，得到pdf或dvi等格式的输出文件，
来观看最终的效果。

[Gummi](http://dev.midnightcoding.org/projects/gummi)作为$\LaTeX$的编译器比较另类。它的主界面分来左右两栏，左栏是$\LaTeX$文件编辑框，右栏是即时生成的pdf效果，从某种
意义上说，它有了所见即所得(WYSIWYG)的功效。除此之外，它还支持SyncTeX用于在生成的pdf与源代码之间互相定位显示，比如在右
栏的pdf显示上ctrl+点击可以定位点击位置对应的源代码，在左栏源代码某行作改动则右侧自动将屏幕滚动到修改处并显示改动的效果。

Gummi还有其它功能，比如代码片段功能，输入item+tab，就可以自动生成itemize环境。

### 文档定位

需要注意的是，在TexLive 2011版本之后，需要告诉gummi要编辑的$\LaTeX$源文件的绝对路径，否则无法根据编辑位置自动定位pdf文件位置。
原因我的理解如下：

* synctex 利用源文件的绝对路径名来比较两个文件是否相同。源文件的绝对路径是xelatex在编译时生成的，生成的策略如下：
  1. 如果tex文件是绝对路径，就直接使用。
  1. 如果tex文件是相对路径，就"当前路径"加上"$\textrm{kpeswich test.tex}$"的返回值，比如结果就是"$\textrm{/home/user/./test.tex}$"。

```shell
  xelatex -synctex=1 test.tex
  xelatex -synctex=1 /home/user/test2.tex
```

* 如果传递给synctex相对路径，或者上述第2种情况下不带"/./"格式的绝对路径，都会出错误如"SyncTeX Warning: No tag for ./test.tex"。

```sh
  synctex view -i 3:1:/home/user/./test.tex -o test.pdf
  synctex view -i 3:1:/home/user/test2.tex -o test2.pdf
```

### 中文文档模板

```latex
\documentclass[adobefonts,UTF8,cs4size,a4paper,fancyhdr,fntef,hyperref]{ctexart}%,winfonts,
\usepackage{url}
\usepackage[numbers,sort&compress]{natbib}%,super
\usepackage{graphicx}
\graphicspath{{./pics/}}
\usepackage{amsmath,amsthm,amssymb}
\usepackage{color}
\usepackage[colorlinks]{hyperref}
\usepackage{alltt}
\usepackage{makeidx}
\makeindex
\usepackage{todonotes}
\usepackage{ulem} % use normalem to protect \emph
\newcommand\hl[1]{\bgroup\markoverwith
  {\textcolor{#1}{\rule[-.5ex]{2pt}{2.5ex}}}\ULon}

\newtheorem{thm}{THEOREM}
\newtheorem{lma}{LEMMA}
\newtheorem{clr}{COROLLARY}
\newtheorem{asm}{Assumption}

\newcommand{\argmax}{\operatornamewithlimits{argmax}}
\newcommand{\argmin}{\operatornamewithlimits{argmin}}
\newcommand{\ud}{\mathrm{d}}%this is used to input dx of \int
\newcommand\onlinecite[1]{文献[\citenum{#1}]}
\newcommand\keywords[1]{\flushleft\textbf{关键词}:#1}

\title{\textbf{Welcome to Gummi 0.6.4}}
\author{Hedong Yang}
\date{\today}

\begin{document}
\maketitle
\tableofcontents
\section{Start}

%\section*{参考文献}
\bibliographystyle{GBT7714-2005N}
\bibliography{gummi}
\end{document}
```
