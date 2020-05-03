---
layout: post
title: A definition for monit in Chef
date: '2011-07-25T18:29:00+02:00'
tags:
- monit
- redis
- chef
tumblr_url: https://fernando.blat.es/post/8045930392/a-definition-for-monit-in-chef
---
If you use `monit` and `Chef` maybe you are interested in this small definition:

{% highlight python %}
  template "/etc/monit/#{params[:name]}.monitrc" do
    cookbook "monit"
    source "service.monitrc.erb"
    variables(:p => params)
    notifies :restart, resources(:service => "monit")
  end
{% endhighlight %}

This definition adds some sugar to your recipes when using monit, i.e:

{% highlight python %}
  pid_file "/var/run/redis.pid"
  start_program "/etc/init.d/redis-server start"
  stop_program "/etc/init.d/redis-server stop"
  alert "#{node[:monit][:alert_recipients]} only on { timeout }"
  checks <<-CHECKS
  if failed host localhost port 6379 then restart
  if 5 restarts within 5 cycles then timeout
{% endhighlight %}
end
