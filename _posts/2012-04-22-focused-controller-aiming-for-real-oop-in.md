---
layout: post
title: Focused Controller - Aiming for "real OOP" in Rails controllers
date: '2012-04-22T10:28:43+02:00'
tags:
- rails
- oop
tumblr_url: https://fernando.blat.es/post/21559962345/focused-controller-aiming-for-real-oop-in
---
[Focused Controller - Aiming for "real OOP" in Rails controllers](https://github.com/jonleighton/focused_controller)  

[thechangelog](http://thechangelog.com/post/21493208725/focused-controller-aiming-for-real-oop-in-rails-controll):

> While Rails controllers are Ruby classes and have some OOP support as a result, the lack of true encapsulation and awkward `before_filter`-based sharing of code between actions leave some OOP die hards disappointed. [Jon Leighton](https://twitter.com/jonleighton)’s [Focused Controller](https://github.com/jonleighton/focused_controller) is an early stage project that takes a different approach. Controllers are Ruby modules and actions are classes classes that inherit ultimately from `ApplicationController`:
> 
> module PostsController # Action is a common superclass for all the actions # inside `PostsController`. class Action < ApplicationController include FocusedController::Mixin end class Index < Action def run # Your code here. end # No instance variables are shared with the view. Instead, # public methods are defined. def posts @posts ||= Post.all end # To prevent yourself having to write `controller.posts` # in the view, you can declare the method as a helper # method which means that calling `posts` automatically # delegates to the controller. helper_method :posts end # Actions do not need to declare a `run` method - the default # implementation inherited from `FocusedController::Mixin` is an # empty method. class Show < Action def post @post ||= Post.find params[:id] end helper_method :post end end 
> 
> Since routes need to be modified to point to this new convention of `Controller::Action#run`, a helper is provided for your routes file that supports the usual syntax:
> 
> focused_controller_routes do resources :posts end 
> 
> Jon is looking for feedback so check out the [README](https://github.com/jonleighton/focused_controller#readme) for advanced usage, especially on how to test this new style of controller.
