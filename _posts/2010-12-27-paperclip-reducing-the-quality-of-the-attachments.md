---
layout: post
title: 'paperclip: reducing the quality of the attachments'
date: '2010-12-27T08:59:00+01:00'
tags:
- paperclip
- rubyonrails
- development
tumblr_url: https://fernando.blat.es/post/2480104575/paperclip-reducing-the-quality-of-the-attachments
---
Example of attachment:

{% highlight python %}
  has_attached_file :main_picture, :styles => {
                                      :small => {
                                        :geometry => "203x115#",
                                        :format => 'jpg'
                                      },
                                      :huge => {
                                        :geometry => "927x524#",
                                        :format => 'jpg'
                                      }
                                    },
                                    :convert_options => {
                                      :all => "-quality 90"
                                    },
                                    :url => "/system/:attachment/:id/:style.:extension",
{% endhighlight %}

- `:convert_options` for reducing quality
- `:url` for avoiding problems with image names
