---
layout: post
title: today we are having some trouble with our little
date: '2011-01-25T22:52:32+01:00'
tags:
- development
- actuable
tumblr_url: https://fernando.blat.es/post/2929720050/today-we-are-having-some-trouble-with-our-little
---
 ![](/tumblr_files/tumblr_lflm3k8M9a1qz4y16o1_1280.png)  

Today we are having some trouble with our little pet project [Actuable](http://actuable.es).

It’s a Rails 3.0.3 application with Ruby 1.9.2 and (nginx) Passenger, all installed in a linode instance.

Some tips to remember:

- you only have 4 CPU’s, don’t configure Passenger to have 4 processes running because the server won’t have free CPU cycles for other processes such as the database, the background jobs runner, the redis, the memcached, and all the stuff you have installed
- optimize your database! indexes & valid configuration variables can give you a breath
- don’t forget to configure more than 1 worker in the nginx
- fragment cache + memcached is very easy to configure and helps you to save CPU cycles
