---
date: '2002-12-22 10:13:20'
layout: post
slug: making-movabletype-play-nice-with-umlauts
status: publish
comments: true

title: Making MovableType play nice with umlauts
wordpress_id: '69'
categories:
- Weblogs
---

Since I am using [Anders'](http://www.jacobsen.no/anders/blog/) tips for archiving MovableType with [my german language blog](http://retrogra.de), I noticed a small flaw in the _dirify_ directive. If there are any umlauts in the title, they get simply discarded, leaving behind rather mutilated looking filenames.
Since that can't be good for the Googlejuice, I have added a new function, _convert_umlauts_, that changes them to their ASCII equivalents.
If anybody is interested, here's [the patch](/MT-Util-umlaut.diff)
