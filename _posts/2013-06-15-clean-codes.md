---
layout: post
title: 整洁代码
description: "代码的整洁或优雅程度，反应出一个程序员的职业教养，不可不注意。"
category: 开发
tags: [programming, Java]
---
{% include JB/setup %}

写代码，一般要注意两种约束，

* 代码风格(coding style)，主要是针对语法要求，规定如何编辑代码。
* 代码优雅(clean code)，主要是针对优雅的实现，目标是使代码易理解。

这两者有一些共同之处，比如变量命名的约定。但不同也很明显，比如前者约定代码块开始的"{"是在行首还是行尾，
代码缩进几个空格等，后者则建议函数内尽量不要多个return等等。

Google有C++/Python等语言的coding
style，但是没有Java的。而Android系统及应用都有基于Java，所以它们的coding
style可以视为Google的java coding style。这个[coding style](https://www.evernote.com/shard/s16/sh/b920e93c-2b4f-4e5e-a6ed-c820528f47ea/315dfaf6a40a1d8aec3ea0e063159f74?noteKey=315dfaf6a40a1d8aec3ea0e063159f74&noteGuid=b920e93c-2b4f-4e5e-a6ed-c820528f47ea)声明它们遵循[java基本约定](http://www.oracle.com/technetwork/java/codeconvtoc-136057.html)，
同时增加其它一些规则。与之非常类似的，是[Google web toolkit项目对代码的要求](https://developers.google.com/web-toolkit/makinggwtbetter#codestyle)，也是基本约定外一些规则。这些规则，更多是针对clean code的。

简单来说，clean code对应着一些编码建议或者规则(rule)，目标是代码的易读易维护。clean
code反应出开发者的教养或风度。网上有很多关于如何
开发clean code的小建议，甚至有了一本专著[Clean Code: A Handbook of Agile Software Craftsmanship](http://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882)，其中译本名为《代码整洁之道》。
对项目代码进行
clean code检查的工具，也已经出现较多种。最有名的，当数[Sonarqube](http://www.sonarsource.org/)，以后有机会可以试一下。

与clean code非常相近的一个提法，是编码的good habits/good practices。google上也可以搜到很多相关的内容，不赘述。

