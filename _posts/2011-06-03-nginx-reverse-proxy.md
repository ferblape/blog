---
layout: post
title: nginx reverse proxy
date: '2011-06-03T09:03:22+02:00'
tags:
- nginx
tumblr_url: https://fernando.blat.es/post/6135693369/nginx-reverse-proxy
---
Reverse proxy to pass to a given IP the incoming requests:

{% highlight javascript %}
server {
  server_name domain.com;
  root /var/www//current/public;

  location / {
    proxy_redirect off;
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_pass http://1.2.3.4;
{% endhighlight %}
}
