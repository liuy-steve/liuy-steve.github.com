---
layout: post
title: "learing git"
description: ""
category: tools
tags: [git]
---
{% include JB/setup %}
#学习git 目录 暂时记录的东西

## git 的暂存区

- git status -s 的命令行解释
  尤其是命令行的输出结果的第一列M和第二列M的区别
  将git status -s 看成 version - M - stage - M - ws 的关系，便于记忆。
- git diff的不同参数 
  在git权威宝典这本书里面的第5.1节和5.2节有这详细的说明。跟着例子做一遍，很容易就记得了
  
## git 暂存区的用法

- git 暂存区（statge），我以为是git的workspace和version之间的中间件。

## git 通过命令行进行git版本控制方法的演算

- git通过建立 tag，commit，tree，blob 通过想容器一样的封装，将本身的“标签”和内容长度加上内容字符进行SHA1哈希算法确立标签。这个标签就是全局（统计学上）的唯一
标识。通过在标识之间建立链表一样的结构，（parrent）等的关系来检索git中任意提交过或者还原的版本。类似C语言中指针的应用，指针指向的是hash指标识的object。
很巧妙。 全局的指针有 HAED “branch” ，对指针的操作可以取^,还可以取^+No.用来向前追溯，那么向后追溯呢?

## 一直到第10章以前都是比较痛苦的学习过程
- 10章以前通过一个简单的例子解释了git版本控制的原理。看了两遍才看出个大概的意思。直到第10章的时候，看到了这句话：“Git通过田间方式反删除文件没有副作用，这是应为在Git的版本库中，相同的内容的文件保存在一个blob对象中，即使是内容不同的blob对象通过对象库大伯啊也会进行存储优化”。看到这个句子有种茅塞顿开的感觉，git真牛逼。太巧妙了。
