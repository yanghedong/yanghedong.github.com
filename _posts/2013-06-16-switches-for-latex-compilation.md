---
layout: post
title: LaTeX编译开关
description: "通过开关，控制同一个$\LaTeX$文件输出不同的内容"
category: 备忘
tags: [LaTeX]
---
{% include JB/setup %}
写简历时，可能根据情况需要英文简历或中文简历。如果$\LaTeX$或$\TeX$命令能读到命令行用于控制
语言类型的开关参数，则可以将中英文简历放在同一个```.tex```文件中。遗憾的是，没有这样
的命令。

不过，有一种变通的方法。假定同时包含中英文内容的简历为```cv.tex```，文中通过检测是否定义变
量```\\zh{}```来输出中、英文。则，输出先英文、后中文的中英简历的命令```en-cn.sh```如下：

```sh
#!/bin/sh
xelatex cv.tex
xelatex cv.tex
mv cv.pdf cv-en.pdf
xelatex "\\def\\zh{} \input{cv}"
xelatex "\\def\\zh{} \input{cv}"
mv cv.pdf cv-zh.pdf
xelatex "\newcommand\org[0]{cv} \input{en-cn}"
mv en-cn.pdf hedong-en-cn.pdf
```

合并两个语言版本的简历，用到了一个名为```en-cn.tex```的文件，其内容如下：

```
\documentclass[A4paper]{article}
\usepackage{pdfpages}
\begin{document}
  \includepdf[nup=1x1, delta=0mm 0mm,%
              scale=1,pages={1-2}]{hedong\org-en.pdf}
  \includepdf[nup=1x1, delta=0mm 0mm,%
              scale=1,pages={1-2}]{hedong\org-zh.pdf}
\end{document}
```
