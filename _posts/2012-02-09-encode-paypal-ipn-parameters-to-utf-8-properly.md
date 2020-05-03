---
layout: post
title: Encode Paypal IPN parameters to UTF-8 properly
date: '2012-02-09T15:32:05+01:00'
tags:
- ruby
- ruby on rails
- paypal
- ipn
- encoding
- utf-8
tumblr_url: https://fernando.blat.es/post/17318291802/encode-paypal-ipn-parameters-to-utf-8-properly
---
[Paypal](http://www.paypal.com) sucks the most of the time, whenever it has the opportunity to demonstrate it. One of that chances are payment notifications, also known as IPN, and the encoding of the parameters.

First of all, Paypal ignores the parameters charset that you send with all the purchase parameters, so, if you don’t change your settings in Paypal webpage, it is going to send you the parameters in `windows-1252` encoding.

Rails assumes that the world is fair and modern and works in `UTF-8`, so when your application receives a request Rails sets the encoding of the parameters to `UTF-8` without converting them.

For example, if Paypal sends you the string _“Almería”_, in your parameters you will see&nbsp;_“Almer\xEDa”_, and if you ask for the encoding:

{% highlight python %}
{% endhighlight %}

To fix it, the first thing is to reproduce this state:

{% highlight python %}
a.encoding
{% endhighlight %}

And then, try to get back to `UTF-8`. Sadly this doesn’t work:

{% highlight python %}
{% endhighlight %}

If you want a detailed explanation, you can read [this post](http://jalada.co.uk/2011/12/07/solving-latin1-and-utf8-errors-for-good-in-ruby.html), which has help me a lot and has inspired me to get the solution:

{% highlight python %}
class Hash
  def encode_to_utf8
    copy_of_params = {}
    self.each do |k,v|
      copy_of_params[k] = fix_cp1252_utf8(v)
    end
    copy_of_params
  end

  private
  
  def fix_cp1252_utf8(text)
    text.force_encoding('windows-1252').encode('cp1252',
                :fallback => {
                  "\u0081" => "\x81".force_encoding("cp1252"),
                  "\u008D" => "\x8D".force_encoding("cp1252"),
                  "\u008F" => "\x8F".force_encoding("cp1252"),
                  "\u0090" => "\x90".force_encoding("cp1252"),
                  "\u009D" => "\x9D".force_encoding("cp1252")
                }).encode("utf-8")
  end
  
{% endhighlight %}

So, when you receive the parameters from paypal notification, just call encode\_to\_utf8 to get the proper encoding back to your data.

_(I know you love to use inject, but I don’t link so much to have to return the temporal hash inside the block :)_
