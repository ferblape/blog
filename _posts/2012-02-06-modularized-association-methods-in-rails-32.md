---
layout: post
title: Modularized Association Methods in Rails 3.2
date: '2012-02-06T20:38:26+01:00'
tags:
- ruby on rails
- active model
tumblr_url: https://fernando.blat.es/post/17163861712/modularized-association-methods-in-rails-32
---
[Modularized Association Methods in Rails 3.2](http://blog.hasmanythrough.com/2012/1/20/modularized-association-methods-in-rails-3-2)

> The real reason for this change is being able to compose your own methods with the standard generated methods. Before this change, you’d have to use&nbsp;`alias_method_chain`&nbsp;or some other fancy footwork to layer your own logic on top of the standard association functionality. Either that or you’d have to somehow duplicate the standard behavior in your own method. Ick. Now you can compose methods using inheritance and&nbsp;`super`, the way Alan Kay intended you to.
