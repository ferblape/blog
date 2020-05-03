---
layout: post
title: Sandi Metz - SOLID Object-Oriented Design
date: '2011-09-26T13:29:52+02:00'
tags:
- tdd
- bdd
- solid
- design
- oop
tumblr_url: https://fernando.blat.es/post/10684143771/sandi-metz-solid-object-oriented-design
---
_(notes taken from this great talk)_

[Sandi Metz talks about SOLID Object-Oriented Design](http://confreaks.net/videos/240-goruco2009-solid-object-oriented-design)

Your application will change, and what will happen when it changes depends on it’s design, because you are going to be introducing unexpected dependencies, and only a good design can help you to keep your code good enough.

![](http://martinfowler.com/bliki/images/designStaminaGraph.gif)

[http://martinfowler.com/bliki/DesignStaminaHypothesis.html](http://martinfowler.com/bliki/DesignStaminaHypothesis.html)

If you plan your application to fail, skip design, but if your application succeeds it will cost you money.

SOLID:

- **S** ingle Responsibility
- **O** pen / Closed
- **L** iskov Substitution&nbsp;(not very common in AR objects)
- **I** nterface Segregation&nbsp;(does not apply to dynamic languages)
- **D** epenency Inversion&nbsp;

Design is all about dependencies: if you refer to something, you depend to it; and when the things you depende on change, you must change.

Red - Green - Refactor:

- Is it DRY?
- Does it have one responsibility?
- Does everything in it change at the same rate?
- Does it depend on things that change less often that it does?
