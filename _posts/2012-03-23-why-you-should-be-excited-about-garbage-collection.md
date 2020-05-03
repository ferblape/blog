---
layout: post
title: Why You Should Be Excited About Garbage Collection in Ruby 2.0 - Pat Shaughnessy
date: '2012-03-23T20:05:00+01:00'
tags:
- ruby
- ruby internals
- garbage collector
- algorithmics
tumblr_url: https://fernando.blat.es/post/19791200564/why-you-should-be-excited-about-garbage-collection
---
[Why You Should Be Excited About Garbage Collection in Ruby 2.0 - Pat Shaughnessy](http://patshaughnessy.net/2012/3/23/why-you-should-be-excited-about-garbage-collection-in-ruby-2-0)  

> You may have heard last week how&nbsp;[Innokenty Mihailov’s great Enumerable::Lazy feature](http://blog.railsware.com/2012/03/13/ruby-2-0-enumerablelazy/)&nbsp;was accepted into the Ruby 2.0 code base. But you may not have heard about an even more significant change that was merged into Ruby 2.0 in January: a new algorithm for garbage collection called “Bitmap Marking.” The developer behind this sophisticated and innovative change,[Narihiro Nakamura](http://www.narihiro.info/index.en.html), has been working on this since 2008 at least and also implemented the “Lazy Sweep” garbage collection algorithm already included in Ruby 1.9.3. The new Bitmap Marking GC algorithm promises to dramatically reduce overall memory consumption by all Ruby processes running on a web server!
