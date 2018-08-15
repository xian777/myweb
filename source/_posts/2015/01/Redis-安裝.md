---
title: Redis 安裝
tags:
  - Redis
date: 2015-01-19 17:56:00
---

<div>在Linux環境上安裝Redis，最簡單的方式是用套件管理(apt or yum)，但通常不是最新版本
如果要使用最新版本，需要到官網下載原始碼編譯</div>$ wget http://download.redis.io/releases/redis-2.8.19.tar.gz
$ tar xzf redis-2.8.19.tar.gz
$ cd redis-2.8.19
$ make

<div>編譯如果碰到這個情況 </div>make[1]: Entering directory '/tmp/redis-2.8.19/src'
&nbsp; &nbsp; CC adlist.o
In file included from adlist.c:34:0:
zmalloc.h:50:31: fatal error: jemalloc/jemalloc.h: No such file or directory
&nbsp;#include &lt;jemalloc/jemalloc.h&gt;
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;^
compilation terminated.
<div>
</div><div>可以到deps下面先行編譯</div>$ cd deps
$ make hiredis jemalloc linenoise lua

<div>或是直接執行以下的命令</div>$ make MALLOC=libc

Windows下的安裝，可以參考MSOpenTech在github上面的文件
[https://github.com/MSOpenTech/redis](https://github.com/MSOpenTech/redis)

可以直接下載編譯好的版本
[https://github.com/MSOpenTech/redis/releases](https://github.com/MSOpenTech/redis/releases)

更簡單的方式是透過nuget下載，連設定都有，套件名稱為redis-64
[https://www.nuget.org/packages/Redis-64/](https://www.nuget.org/packages/Redis-64/)

設定Service
redis-server --service-install redis.windows.conf --loglevel verbose

解除Service
redis-server --service-uninstall