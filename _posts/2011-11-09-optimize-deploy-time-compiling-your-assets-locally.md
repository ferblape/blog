---
layout: post
title: Optimize deploy time compiling your assets locally
date: '2011-11-09T20:16:45+01:00'
tags:
- capistrano
- toldo
- asset pipeline
tumblr_url: https://fernando.blat.es/post/12563486374/optimize-deploy-time-compiling-your-assets-locally
---
Compress the assets on each deploy can be a pain for the server running your application, specially if it is a small VPS. For example, in [Toldo](http://thetoldo.com), to deploy to our staging server a 512Mb VPS in [linode.com](http://linode.com), it took about 130 secs to compress all the assets, which is a lot of time (specially because one of your CPU’s will be really busy and could affect to the performance of your application).

That’s why we have decided to compress the assets locally and then upload them using Capistrano.

First of all, you should check that you ignore the folder `public/assets` in your code repository and that you have removed the line `load 'deploy/assets'` from `Capfile` file.

We have defined these two tasks to compress the assets and to deploy them. The code is really simple, and not very sophisticated, maybe there are ways to do the same better:

{% highlight python %}
namespace :toldo do
  desc "Compress assets in a local file"
  task :compress_assets do
    run_locally("rm -rf public/assets/*")
    run_locally("bundle exec rake assets:precompile")
    run_locally("touch assets.tgz && rm assets.tgz")
    run_locally("tar zcvf assets.tgz public/assets/")
    run_locally("mv assets.tgz public/assets/")
  end

  desc "Upload assets"
  task :upload_assets do
    upload("public/assets/assets.tgz", release_path + '/assets.tgz')
    run "cd #{release_path}; tar zxvf assets.tgz; rm assets.tgz"
  end
{% endhighlight %}

We have to call these tasks in the callbacks of our deploy file:

{% highlight python %}
  before "deploy:update_code", "toldo:compress_assets"
  ...
{% endhighlight %}

With this small change, our server will be less stressed on each deploy.

![](http://fc08.deviantart.net/fs71/f/2011/111/d/c/nyan_cat_stamp_by_yukimiyasawa-d3eixi6.gif)
