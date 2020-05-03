---
layout: post
title: wkhtmltopdf stopping when running tests
date: '2012-09-02T09:19:05+02:00'
tags:
- homebrew
- wkhtmltopdf
- ruby
- rspec
- pdfkit
- in
tumblr_url: https://fernando.blat.es/post/30713044468/wkhtmltopdf-stopping-when-running-tests
---
Using Mountain Lion and [wkhtmltopdf](http://code.google.com/p/wkhtmltopdf/) installed via homebrew, when I run my tests they stop when inside the test it generates a PDF, and I couldn’t finish the execution of all the suite. I use also [pdfkit gem](http://rubygems.org/gems/pdfkit).

After searching a lot no one seems to have this problem. I fixed it by removing the package from homebrew and installing it manually, [downloading the binary](http://code.google.com/p/wkhtmltopdf/downloads/list) from the project webpage.
