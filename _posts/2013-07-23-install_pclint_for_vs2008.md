---
layout: post
title: "Install PCLint9 for VS2008"
description: ""
category: tools
tags: [pclint]
---
{% include JB/setup %}
#如何安装PCLint9

##安装和配置生成lnt
- PCLint9的安装与之前的版本大同小异。需要注意的创建lnt脚本的过程中，配置项的选择需要增加VS2008环境。建议在include的时候添加windows sdk的include目录。
  

## 集成到vs2008

2 points！
- 在创建tool中的ext tool选项卡的时候，输入命令行参数时，输入重定向字符‘>‘,居然提示不支持。好在PCLint本身有一个-os的选项。用法要参照man.pdf中的提示，需要将重定向文件选项及文件名放在工程文件名前面。

- 在创建选项卡命令行的过程中，vs2008的环境变量（所谓的外部依赖工具运行参数），在msdn中有详细描述。与VC6有很大的不同，照抄网上之前的vc6配置会找不到相应的变量。提示使用命令行参数输入框后面的提示按钮！
  
## a sample

add menu contents: 

Title:						pclint export project.lnt
Command:					d:\lint\lint-nt.exe
Arguments:				-os($(ProjectFileName).lnt) +linebuf $(ProjectFileName) 
Initial directory:$(ProjectDir)


Title:						pclint check prj
Command:					d:\lint\lint-nt.exe
Arguments:				+ffn -i"D:\lint" std.lnt env-vc9.lnt $(ProjectFileName).lnt 
Initial directory:$(ProjectDir)