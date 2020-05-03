---
layout: post
title: 'giant robots smashing into other giant robots: Tidy views and beyond with
  Decorators'
date: '2011-12-02T23:45:11+01:00'
tags: []
tumblr_url: https://fernando.blat.es/post/13650070966/giant-robots-smashing-into-other-giant-robots
---
[giant robots smashing into other giant robots: Tidy views and beyond with Decorators](http://robots.thoughtbot.com/post/13641910701/tidy-views-and-beyond-with-decorators)  

[thoughtbot](http://robots.thoughtbot.com/post/13641910701/tidy-views-and-beyond-with-decorators):

> ## The problem
> 
> Here’s a view serving `monkeys#show`. What’s wrong with it?
> 
> <h1><%= @monkey.name -%>'s Monkey page</h1>
> <% if @monkey.eating? %> <div class="eating"> <h2><%= @monkey.name -%> is eating. Nom nom.</h2> </div>
> <% elsif @monkey.sleeping? %> <div class="sleeping"> <h2><%= @monkey.name %>...
