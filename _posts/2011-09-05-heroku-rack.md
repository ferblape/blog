---
layout: post
title: Heroku + Rack = ♥
date: '2011-09-05T17:03:00+02:00'
tags:
- toldo
- heroku
- ruby
tumblr_url: https://fernando.blat.es/post/9834595688/heroku-rack
---
[Toldo](http://thetoldo.com) temporal front page, showing the content in different languages depending on the browser settings, in a few lines, powered by [Rack](http://rack.rubyforge.org) and [Heroku](http://heroku.com):

{% highlight python %}
# http://thetoldo.com

use Rack::Static, :urls => ["/images/"]

run Proc.new { |env|
  language = env['HTTP_ACCEPT_LANGUAGE'].scan(/^[a-z]{2}/).first
  index_file = (language == 'es') ? "index.es.html" : "index.en.html"
  [200, {'Content-Type'=>'text/html'}, File.open(index_file, 'r')]
{% endhighlight %}

[https://gist.github.com/1195166](https://gist.github.com/1195166)
