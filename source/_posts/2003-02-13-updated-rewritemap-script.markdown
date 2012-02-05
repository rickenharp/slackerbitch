---
date: '2003-02-13 17:27:17'
layout: post
slug: updated-rewritemap-script
status: publish
comments: true

title: Updated RewriteMap script
wordpress_id: '78'
categories:
- Weblogs
---

I just finished a rewrite of the [mapping program](http://slackerbit.ch/archives/2002/12/14/switching_from_flat_to_googlefriendly_archive_urls.html) that I used to switch to more google-friendly URLs. Now it no longer needs MySQL installed. Instead, it uses the MT Perl API itself to get the new filename.

As an added bonus, the new URL format is no longer hardcoded, but is taken from the file template that you set in the blog configuration.

**UPDATE:** And this time, I also [link to it](http://slackerbit.ch/rewrite_archives2.pl.txt)...
