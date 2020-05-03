---
layout: post
title: 'Instagram Engineering: Storing hundreds of millions of simple key-value pairs
  in Redis'
date: '2011-11-01T19:42:29+01:00'
tags:
- redis
- instagram
tumblr_url: https://fernando.blat.es/post/12203531654/instagram-engineering-storing-hundreds-of
---
[Instagram Engineering: Storing hundreds of millions of simple key-value pairs in Redis](http://instagram-engineering.tumblr.com/post/12202313862/storing-hundreds-of-millions-of-simple-key-value-pairs)  

[instagram-engineering](http://instagram-engineering.tumblr.com/post/12202313862/storing-hundreds-of-millions-of-simple-key-value-pairs):

> The size difference was pretty striking; with our 1,000,000 key prototype (encoded into 1,000 hashes of 1,000 sub-keys each), Redis only needs 16MB to store the information. Expanding to 300 million keys, the total is just under 5GB—which in fact, even fits in the much cheaper m1.large instance type on Amazon, about 1/3 of the cost of the larger instance we would have needed otherwise. Best of all, lookups in hashes are still O(1), making them very quick.
