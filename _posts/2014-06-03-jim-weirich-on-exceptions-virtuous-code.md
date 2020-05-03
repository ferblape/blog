---
layout: post
title: Jim Weirich on exceptions | Virtuous Code
date: '2014-06-03T13:53:00+02:00'
tags:
- ruby
tumblr_url: https://fernando.blat.es/post/87688577990/jim-weirich-on-exceptions-virtuous-code
---
[Jim Weirich on exceptions | Virtuous Code](http://devblog.avdi.org/2014/05/21/jim-weirich-on-exceptions/?utm_source=rubyweekly&utm_medium=email)  

> (An aside, because I use exceptions to indicate failures, I almost always use the “fail” keyword rather than the “raise” keyword in Ruby. Fail and raise are synonyms so there is no difference except that “fail” more clearly communicates that the method has failed. The only time I use “raise” is when I am catching an exception and re-raising it, because here I’m _not_ failing, but explicitly and purposefully raising an exception. This is a stylistic issue I follow, but I doubt many other people do).
