---
layout: post
title: agile git workflow
date: '2010-12-27T23:17:00+01:00'
tags:
- git
- development
tumblr_url: https://fernando.blat.es/post/2487694471/agile-git-workflow
---
Overview:

1. Branch off of master to work on the feature
2. Work, work, work, commit, commit, commit
3. Pull down any updates to master
4. Rebase and squash (with discretion) the feature branch to master’s&nbsp;HEAD
5. Merge the feature branch back to master
6. Push up to the shared repository

Git commands:

{% highlight python %}
...
git commit -m "Feature finished"
git fetch
git rebase -i -p origin/master
# pick vs. squash commits
git checkout master
git merge --no-ff issue-12
{% endhighlight %}

Full explained in: [http://geewax.org/agile-git-workflow](http://geewax.org/agile-git-workflow)
