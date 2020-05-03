---
layout: post
title: Feeling comfortable programming Javascript
date: '2012-03-27T17:18:00+02:00'
tags:
- javascript
- nodejs
- heroku
- jasmine
- npm
tumblr_url: https://fernando.blat.es/post/20009924261/feeling-comfortable-programming-javascript
---
As a Ruby developer, programming right Javascript is a bit uncomfortable:

- you have to adapt to learn a language that uses prototypes instead of classes
- it is a new environment, with new tools, and you need to feel comfortable with them to be productive

These days we have been working in a small [Node.js](http://nodejs.org/) application for a small pet project. Instead of create the whole application using Node.js we decided to use Ruby on Rails for models, controllers and UI and use Node.js to handle hard search, which fits really well with the async nature of Node.js.

The result is [Mapismo worker past](https://github.com/ferblape/mapismo-worker-past), a kind of background worker that search for data in some social networks, such as Instagram or Flickr.

I’m pretty proud of the result and the experience, that’s why I want to share some keys in this post.

### Testing

Once you are used to develop testing your code, it is really difficult to work without that feeling. That’s why one of the first things that you can do when learning javascript is learn, at the same time, how to test the code you write.

Right now, I only know [Jasmine](http://pivotal.github.com/jasmine/), and it has been really useful. And, if you use Node.js, you can use [Jessie](https://github.com/futuresimple/jessie) that runs Jasmine in Node.js.

And if your project is open source you should CIlike [Travis](http://travis-ci.org/). I’m [already doing it](http://travis-ci.org/#!/ferblape/mapismo-worker-past).

### Application meta-information

Create a file `package.json` in the root of your project and write down stuff like the version of Node.js you expect to run, the dependencies of your application, the license of your project, which is the command to run your tests.

### Package search

To search for npm packages (the equivalent to Ruby gems), you should use [search.npmjs.org](http://search.npmjs.org/). I’ve noticed that for an specific topic there are lots of alternatives. For example, try to search for `cron` or `flickr`. Github in this cases is really useful to detect abandoned projects (or projects without tests).

### Heroku

You can [use heroku to deploy your Node.js application](https://devcenter.heroku.com/articles/nodejs). It works, and it’s easy. And maybe your application does not require so many resources and you can run it in the free plan.

### Javascript resources

This is a bit off-topic, but I want to share with you these resources:

- [Understanding JavaScript OOP](http://killdream.github.com/blog/2011/10/understanding-javascript-oop/index.html)
- [JSRef](http://jsref.64p.org/)
- [Node manual](http://nodejs.org/api/index.html)
- [Essential JavaScript Design Patterns](http://addyosmani.com/resources/essentialjsdesignpatterns/book/#introduction)

Remember, you don’t need to be like him:

[<figure class="tmblr-full" data-orig-height="627" data-orig-width="500"><img src="https://66.media.tumblr.com/7a50aa572676d561a68bcb41f4a2dc2d/aab7239c4c95e9cb-d5/s540x810/20f66cbc380179855472f0ec1419e2b3240ba179.jpg" data-orig-height="627" data-orig-width="500"></figure>](http://troll.me/2012/01/31/the-most-interesting-man-in-the-world/i-dont-awlays-write-javascript-but-when-i-do-i-amke-it-procedural/)
