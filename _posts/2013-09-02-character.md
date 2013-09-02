---
layout: post
title: "字符集的问题"
description: ""
category: 
tags: [字符]
---
{% include JB/setup %}

字符的问题由来已久。windows上命名的文件夹经过samba共享传到linux上，中文为啥是乱码？URL中的中文字符为啥是%后面什么什么？
如果这些关于字符的问题你没有困惑，那么该POST可以不用再往后看了。如果你对字符的问题有一些疑惑？那么来这里寻找答案吧。

本文的内容源引自[一篇CSDN帖子](http://blog.csdn.net/fmddlmyy/article/details/372148)


![截图示意]({{ site.img_url }}/20130902/type.jpg)

![截图示意]({{ site.img_url }}/20130902/UNICODE-ASCII.jpg)

![截图示意]({{ site.img_url }}/20130902/utf8-bom.jpg)

![截图示意]({{ site.img_url }}/20130902/utf8-nobom.jpg)

![截图示意]({{ site.img_url }}/20130902/utf16-bom.jpg)

![截图示意]({{ site.img_url }}/20130902/utf16-bom-bigendian.jpg)

![截图示意]({{ site.img_url }}/20130902/utf16-nobom.jpg)

![截图示意]({{ site.img_url }}/20130902/utf16-nobom-bigendian.jpg)
