---
layout: post
title: Our Jenkins script
date: '2011-04-25T11:21:06+02:00'
tags: []
tumblr_url: https://fernando.blat.es/post/4922902125/our-jenkins-script
---
Our Jenkins configuration to run our specs, including the acceptance ones with Selenium (based on [this great post](http://blog.wakatara.com/2010/12/12/installing-a-hudson-ci-server-on-amazon-ec2-with-cucumber-and-capybara-and-github-integration/)

{% highlight python %}
#!/bin/bash 
export DISPLAY=:99 
sudo /etc/init.d/xvfb start 
bundle install --without staging production
/usr/bin/env RAILS_ENV=test bundle exec rake db:drop db:create db:migrate  
bundle exec rake
RESULT=$? 
{% endhighlight %}
exit $RESULT
