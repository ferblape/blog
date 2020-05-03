---
layout: post
title: How we started to measure page rendering time in Toldo
date: '2013-04-20T12:27:20+02:00'
tags:
- toldo
- stats
- ducksboard
- rails
tumblr_url: https://fernando.blat.es/post/48428274161/how-we-started-to-measure-page-rendering-time-in
---
In the last week we have been measuring the mean response time in the server of the public pages of [Toldo](http://tol.do) shops, it is, how long takes Rails to render those public pages.

What we did is, by far, the simplest solution: each day we process the previous day logs using a simple bash script, which filters the requests from the shops and extracts the column with the response time.

{% highlight python %}
{% endhighlight %}

Also, a simple Ruby script helps calculating the mean:

{% highlight python %}
# mean.rb
#!/usr/bin/env ruby

total = 0
sum = 0.0

STDIN.read.split("\n").each do |a|
  total += 1
  sum += a.to_f
end

{% endhighlight %}

Finally, we have been using the awesome dashboard service [Ducksboard](http://ducksboard.com) to generate some nice graphs. And this is the result (the time is in miliseconds):

<figure class="tmblr-full" data-orig-height="194" data-orig-width="350"><img alt="image" src="https://66.media.tumblr.com/d12ae84c56a7baa87939256b9bad8f62/fb5db9d76c329254-4f/s540x810/133524a7e187626e3375559685de2c38fe013e8c.png" data-orig-height="194" data-orig-width="350"></figure>

In fact, we took profit of this measuring to introduce a nice improvement in the rendering time and check the impact (as you can see in the decrease of the rendering time of about the 40%).

The improvement was introducing fragment caching implemented with the gem [cache\_digests](http://rubygems.org/gems/cache_digests). We are still amazed by the fact that we hadn’t have to write any single line to expire the fragments. Take a look to [this railscast](http://railscasts.com/episodes/387-cache-digests) if you want to learn how it works.

We are still considering new improvements, such as a better dealing of browser cache and finding a way to serve faster the fonts from [Typekit](https://typekit.com/fonts).

But back to the post main topic, keep in mind that:

- you don’t need any big implementation to start to measure stuff in your application
- but measuring is necessary to learn the impact of your changes
- [Ducksboard](http://ducksboard.com) is great, they have a nice [API](http://ducksboard.com/our-apis/) and they are [Developer friendly](http://ducksboard.com/developers/)
- [cache\_digests](http://rubygems.org/gems/cache_digests) FTW!
