---
layout: post
title: Don't forget to tune your database
date: '2011-01-28T12:26:00+01:00'
tags:
- actuable
- development
- mysql
tumblr_url: https://fernando.blat.es/post/2974844912/dont-forget-to-tune-your-database
---
Do you know [mysqltunner.pl](http://mysqltuner.pl/mysqltuner.pl)?&nbsp;It’s a perl script that gives you some clues for improving the performance of your mysql, analyzing the configuration variables and some queries from the history.

{% highlight python %}

li142-29:~# perl mysqltuner.pl

 >> MySQLTuner 1.0.1 - Major Hayden
 >> Bug reports, feature requests, and downloads at http://mysqltuner.com/
 >> Run with '--help' for additional options and output filtering
Please enter your MySQL administrative login: root
Please enter your MySQL administrative password:

-------- General Statistics --------------------------------------------------
[--] Skipped version check for MySQLTuner script
[OK] Currently running supported MySQL version 5.1.47-rel11.2-log
[OK] Operating on 64-bit architecture

-------- Storage Engine Statistics -------------------------------------------
[--] Status: -Archive -BDB -Federated +InnoDB -ISAM -NDBCluster
[--] Data in InnoDB tables: 42M (Tables: 32)
[!!] Total fragmented tables: 32

-------- Performance Metrics -------------------------------------------------
[--] Up for: 2m 35s (1K q [9.419 qps], 45 conn, TX: 1M, RX: 185K)
[--] Reads / Writes: 75% / 25%
[--] Total buffers: 256.0M global + 2.6M per thread (151 max threads)
[!!] Maximum possible memory usage: 652.4M (87% of installed RAM)
[OK] Slow queries: 0% (0/1K)
[OK] Highest usage of available connections: 2% (4/151)
[OK] Key buffer size / total MyISAM indexes: 48.0M/90.0K
[OK] Query cache efficiency: 24.2% (216 cached / 892 selects)
[OK] Query cache prunes per day: 0
[OK] Sorts requiring temporary tables: 0% (0 temp sorts / 90 sorts)
[OK] Temporary tables created on disk: 21% (95 on disk / 444 total)
[OK] Thread cache hit rate: 91% (4 created / 45 connections)
[OK] Table cache hit rate: 25% (58 open / 230 opened)
[OK] Open file limit used: 4% (47/1K)
[OK] Table locks acquired immediately: 100% (674 immediate / 674 locks)
[OK] InnoDB data size / buffer pool: 42.7M/128.0M

-------- Recommendations -----------------------------------------------------
General recommendations:
    Run OPTIMIZE TABLE to defragment tables for better performance
    MySQL started within last 24 hours - recommendations may be inaccurate
{% endhighlight %}

If you get a massive

you are in the right way!&nbsp;

We have reduced the load average from 6 to 0.33, which is a very good value. Also, the number of slow queries has been reduced to 0!

Let’s celebrate it with a [poolparty](http://d3ds4oy7g1wrqq.cloudfront.net/blat/myfiles/PoolParty.gif).&nbsp;

.
