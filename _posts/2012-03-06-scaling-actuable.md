---
layout: post
title: Scaling Actuable
date: '2012-03-06T02:38:34+01:00'
tags:
- actuable
- chef
- ruby on rails
- nodejs
- mysql
- redis
tumblr_url: https://fernando.blat.es/post/18822724015/scaling-actuable
---
[**Actuable**](http://actuable.es) is one of the most successful Spanish projects of the last two years: from september 2010 up to now more than 2,140,000 people have decided to participate in the site and help to change the social reality.

For me, the developer behind the scenes, it has been a really interesting challenge in some aspects: it was my first project in **Ruby 1.9.2** and **Ruby on Rails 3** , my first project using **Redis** , it was the first project that the **acceptance tests** where ran in the browser and had more importance than the functional ones (and this has been one of the best decisions that I took in the project). But, the most important challenge has been **scalability** :

- from 0 to +500,000 requests per day
- from 0 to +2,140,000 users

When we started I installed all the stack in a single VPS, with 512MB of RAM and 4 CPU cores. This server worked pretty well until we go the **Spanish revolution effect** (we doubled the users in just 24 hours). In that moment we upgraded up to 8GB of RAM, but stayed in that single server, up to the past month, when that server was suffering some problems of CPU usage and load:

<figure class="tmblr-full" data-orig-height="206" data-orig-width="500"><img src="https://66.media.tumblr.com/8963c5b8cc7787d4b87b937233614507/8b831e1f1c07cdc6-72/s540x810/55ff740f60197f30a2b9cee155e83a5814fddea3.png" data-orig-height="206" data-orig-width="500"></figure>

So we decided to split the different services in groups of servers, having into account the limitation of 4 CPU’s per server, which was the real bottleneck of the old server:

- old server: web + database + background jobs server + our big Redis
- 2 new x application servers running Unicorn
- 1 new Node.js websocket application + Redis for pub/sub

This way there wasn’t necessary any kind of data migration.

We prepared [some Chef recipes](http://github.com/ferblape/actuable-cookbooks) to install and manage the different roles and then we started with the setup of the services.

I’d like to emphasize two points where we had some trouble:

### Bind services to private IPs

When services run in a single server, bind them to `localhost` is a safe way to run them, and re-configuring them to run in the private network interface can be a pain in the ass, specially in MySQL, where you have to setup password access for the new application servers (do not allow all the IPs from the local network!) and deploy the application which will produce a small downtime.

Also, setting up the firewall properly can cause some server to don’t be accessible.

### Install Unicorn and setup Nginx

I have never used [Unicorn](http://unicorn.bogomips.org) and I only have good words about its setup and its performance: setting up a [`init.` script](https://github.com/ferblape/actuable-cookbooks/tree/master/cookbooks/unicorn) was a good idea and every deploy reload the processes successfully, without keeping any in zombie state. Also monitoring using `monit` has been really easy.

For a 4 CPUs dedicated machine I chose 6 processes configuration, which has been running pretty well up to now: the load average of the servers is about 0.2, which is awesome.

### Summary

Thanks to this work on the platform, Actuable is able to scale horizontally (as Rails developers use to do), and a new application server can be setup and be running in less than 15 minutes.

Invest some time today, to save time tomorrow :)
