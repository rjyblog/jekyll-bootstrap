---
layout:     post
title:      Linux清理Cached内存
subtitle:   
description: ""
date:       2018-07-13
author:     Jason
header-img:
catalog: true
category: Linux
tags: [Android, Linux, 内存管理]
---
{% include JB/setup %}

Kernels 2.6.16 and newer provide a mechanism to have the kernel drop the page cache and/or inode and dentry caches on command, which can help free up a lot of memory. Now you can throw away that script that allocated a ton of memory just to get rid of the cache...

To use /proc/sys/vm/drop_caches, just echo a number to it.

To free pagecache:
{% highlight shell %}
echo 1 > /proc/sys/vm/drop_caches
{% endhighlight %}
To free dentries and inodes:
{% highlight shell %}
echo 2 > /proc/sys/vm/drop_caches
{% endhighlight %}
To free pagecache, dentries and inodes:
{% highlight shell %}
echo 3 > /proc/sys/vm/drop_caches
{% endhighlight %}
This is a non-destructive operation and will only free things that are completely unused. Dirty objects will continue to be in use until written out to disk and are not freeable. If you run "sync" first to flush them out to disk, these drop operations will tend to free more memory.

参考网站：
* [Drop_Caches](https://linux-mm.org/Drop_Caches)
