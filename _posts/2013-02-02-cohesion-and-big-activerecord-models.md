---
layout: post
title: Cohesion and Big ActiveRecord Models
date: '2013-02-02T10:39:00+01:00'
tags: []
tumblr_url: https://fernando.blat.es/post/42090507814/cohesion-and-big-activerecord-models
---
[Cohesion and Big ActiveRecord Models](https://gist.github.com/4660239)  

> One of the problems of big ActiveRecord models is their low cohesion. In Rails we group behaviour around the entities of the domain we’re modelling. If we use only ActiveRecord models for that, we’ll probably end up with classes full of actions, in most cases, completely unrelated to each other (except for the fact that they act on the same domain entity).
