---
layout: post
title: Nginx + upload module + Rails + Carrierwave
date: '2011-10-06T20:31:03+02:00'
tags:
- nginx
- upload
- ruby on rails
- carrierwave
- toldo
tumblr_url: https://fernando.blat.es/post/11106552363/nginx-upload-module-rails-carrierwave
---
I have just set up nginx file uploading for [Toldo](http://thetoldo.com), so now, our Passenger processes are not blocked anymore meanwhile the users upload their, each time bigger, photos.

It has been really easy following this post: [Uploading multiple files with nginx upload module and upload progress bar](http://blog.joshsoftware.com/2010/10/20/uploading-multiple-files-with-nginx-upload-module-and-upload-progress-bar/), so I’m not going to write the same again.

The big difference is that we use the fantastic [Carrierwave](http://carrierwave.rubyforge.org), but the idea is the same:

{% highlight python %}
  class Image < ActiveRecord::Base
    ...
    # being image the attribute where the mounter is attached
    # the file uploaded is in known path, given by the parameter :path, 
    # so we can simulate a file uploaded in that path
    def path=(value)
      self.image = ActionDispatch::Http::UploadedFile.new({
        :filename => value[:name],
        :type => value[:content_type],
        :head => nil,
        :tempfile => File.open(value[:path])
      })
    end
    ...
{% endhighlight %}

Really easy and powerful.
