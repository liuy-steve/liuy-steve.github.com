---
layout: post
title: "linux 常用工具的使用"
description: ""
category: 
tags: [工具]
---
{% include JB/setup %}

linux 工具
=====================
大家常用的Linux下的命令行工具有哪些呢？最近有同事培训了简单的linux命令行工具
的使用，对基本的几个工具进行了介绍。科室千万别小看这些基本工具。

**分析网卡流量**

在linux下使用sar命令，可以显示网络信息。

sar提供六种不同的语法选项来显示网络信息。-n选项使用6个不同的开关：DEV | EDEV | NFS | NFSD | SOCK | ALL 。DEV显示网络接口信息，EDEV显示关于网络错误的统计数据，NFS统计活动的NFS客户端的信息，NFSD统计NFS服务器的信息，SOCK显示套接字信息，ALL显示所有5个开关。它们可以单独或者一起使用。


>[root@cnetos5 ~]# sar
>
[root@cnetos5 ~]# sar -u
>
Linux 2.6.18-53.el5 (cnetos5)   10/20/2013
>
12:00:01 AM       CPU     %user     %nice   %system   %iowait    %steal     %idle
>
12:10:01 AM       all      0.02      0.00      0.14      0.01      0.00     99.84
>
12:20:01 AM       all      0.02      0.00      0.12      0.01      0.00     99.86
>
12:30:01 AM       all      0.01      0.00      0.12      0.01      0.00     99.86
>
Average:          all      0.03      0.00      0.13      0.01      0.00     99.84

    CPU    all 表示统计信息为所有 CPU 的平均值。

    %user	显示在用户级别(application)运行使用 CPU 总时间的百分比。

    %nice	显示在用户级别，用于nice操作，所占用 CPU 总时间的百分比。

    %system	在核心级别(kernel)运行所使用 CPU 总时间的百分比。

    %iowait	显示用于等待I/O操作占用 CPU 总时间的百分比。

    %steal	管理程序(hypervisor)为另一个虚拟进程提供服务而等待虚拟 CPU 的百分比。

    %idle	显示 CPU 空闲时间占用 CPU 总时间的百分比。
    
SAR -N

    [root@sybase ~]# sar -n DEV
    Linux 2.6.32-220.el6.x86_64 (sybase)    10/22/13        _x86_64_        (2 CPU)
    
    
    15:00:01        IFACE   rxpck/s   txpck/s    rxkB/s    txkB/s   rxcmp/s   txcmp/s  rxmcst/s
    15:10:01           lo      0.39      0.39      0.10      0.10      0.00      0.00      0.00
    15:10:01         eth0     74.25     29.15     88.49      1.89      0.00      0.00      0.00
    15:10:01         eth1      0.00      0.00      0.00      0.00      0.00      0.00      0.00
    15:20:01           lo      0.39      0.39      0.10      0.10      0.00      0.00      0.00
    15:20:01         eth0     17.02      7.04     20.88      0.46      0.00      0.00      0.00
    15:20:01         eth1      0.00      0.00      0.00      0.00      0.00      0.00      0.00
    Average:           lo      0.39      0.39      0.10      0.10      0.00      0.00      0.00
    Average:         eth0    156.77     72.57    219.63      5.63      0.00      0.00      0.00
    Average:         eth1      0.00      0.00      0.00      0.00      0.00      0.00      0.00
    
    输出项说明：
    IFACE    网络设备名
    rxpck/s	每秒接收的包总数
    txpck/s	每秒传输的包总数
    rxbyt/s	每秒接收的字节（byte）总数
    txbyt/s	每秒传输的字节（byte）总数
    rxcmp/s	每秒接收压缩包的总数
    txcmp/s	每秒传输压缩包的总数
    rxmcst/s	每秒接收的多播（multicast）包的总数
    
**分析CPU占用**

    Linux中常用的监控CPU整体性能的工具有：
    mpstat： 
        mpstat 不但能查看所有CPU的平均信息,还能查看指定CPU的信息。
    vmstat：
    	只能查看所有CPU的平均信息；查看cpu队列信息；
    iostat: 
    	只能查看所有CPU的平均信息。
    sar： 
    	与mpstat 一样，不但能查看CPU的平均信息，还能查看指定CPU的信息。
    top：
    	显示的信息同ps接近，但是top可以了解到CPU消耗，可以根据用户指定的时间来更新显示。
        

    [root@sybase ~]# mpstat 1
    Linux 2.6.32-220.el6.x86_64 (sybase)    10/22/13        _x86_64_        (2 CPU)
    
    15:32:11     CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
    15:32:12     all    0.99    0.00    1.49    0.00    0.00    0.00    0.00    0.00   97.52
    15:32:13     all    1.00    0.00    1.50    0.00    0.00    0.00    0.00    0.00   97.50
    15:32:14     all    1.00    0.00    1.50    2.50    0.00    0.00    0.00    0.00   95.00
    15:32:15     all    1.00    0.00    1.00    0.50    0.00    0.00    0.00    0.00   97.51
    15:32:16     all    1.00    0.00    1.99    0.00    0.00    0.00    0.00    0.00   97.01
    15:32:17     all    1.49    0.00    1.49    0.00    0.00    0.00    0.00    0.00   97.03
    15:32:18     all    0.50    0.00    1.49    0.00    0.00    0.00    0.00    0.00   98.01

**分析内存占用**

    [root@sybase ~]# vmstat 1 
    procs -----------memory---------- ---swap-- -----io---- --system-- -----cpu-----
     r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
     0  0      0 1288620 171140 280440    0    0     1    21   18   13  1  2 97  0  0
     0  0      0 1288620 171140 280448    0    0     0    40 3499 13022  1  2 95  2  0
     0  0      0 1288620 171140 280448    0    0     0     4 3298 12879  1  2 97  0  0
     0  0      0 1288620 171140 280448    0    0     0     0 3190 12786  0  2 98  0  0
     
**分析IO**

    [root@sybase ~]# iostat -x 1
    Linux 2.6.32-220.el6.x86_64 (sybase)    10/22/13        _x86_64_        (2 CPU)
    
    avg-cpu:  %user   %nice %system %iowait  %steal   %idle
               1.12    0.00    1.68    0.42    0.00   96.78
    
    Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
    sda               0.05     8.75    0.08    1.67     2.56    82.49    48.61     0.03   16.82   4.89   0.86
    dm-0              0.00     0.00    0.11    8.52     2.23    68.58     8.21     2.14  247.78   0.97   0.84
    dm-1              0.00     0.00    0.00    0.00     0.00     0.00     8.00     0.00    6.38   3.19   0.00
    dm-2              0.00     0.00    0.02    1.74     0.31    13.91     8.09     0.23  129.84   0.09   0.02
    
    每项数据的含义如下，
    rrqm/s:	每秒进行 merge 的读操作数目。即 rmerge/s
    wrqm/s:	每秒进行 merge 的写操作数目。即 wmerge/s
    r/s:	每秒完成的读 I/O 设备次数。即 rio/s
    w/s:       每秒完成的写 I/O 设备次数。即 wio/s
    rsec/s:     每秒读扇区数。即 rsect/s
    wsec/s:     每秒写扇区数。即 wsect/s
    rkB/s:     每秒读K字节数。是 rsect/s 的一半，因为每扇区大小为512字节。
    wkB/s:     每秒写K字节数。是 wsect/s 的一半。
    avgrq-sz:   平均每次设备I/O操作的数据大小 (扇区)。即 (rsect+wsect)/(rio+wio)
    avgqu-sz:   平均I/O队列长度。即 aveq/1000 (因为aveq的单位为毫秒)。
    await:     平均每次设备I/O操作的等待时间 (毫秒)。即 (ruse+wuse)/(rio+wio)
    svctm:     平均每次设备I/O操作的服务时间 (毫秒)。即 use/(rio+wio)
    %util:     一秒中有百分之多少的时间用于 I/O 操作，或者说一秒中有多少时间
