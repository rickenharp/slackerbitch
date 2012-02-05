---
date: '2002-12-14 16:51:43'
layout: post
slug: switching-from-flat-to-google-friendly-archive-urls
status: publish
comments: true

title: Switching from flat to Google-friendly archive URLs
wordpress_id: '65'
categories:
- Weblogs
---

As I wrote in my last entry, I changed the way my MT archives individual posts to be more Google-friendly. But since I did not want to have the old 000001.html-style files around and did not want to wait until my site gets reindexed, I delved into the mod_rewrite documentation and came up with a way to achieve this redirection.

First, we need the [mapping program](/rewrite_archives.pl.txt), that generates the new URL based on the old URL. Since I am using MySQL as backend, this only works with this setup so far. It queries the database to regenerate the Google-friendly url from the entry id used in the flat name scheme.
Change the $mtcfghome variable to point to the directory where your mt.cfg resides.
Put the mapping program somewhere where Apache can execute it and make sure it has execute permissions (chmod 755).

Now we need to tell Apache to use it:
I am using this inside a virtual host configuration, so if you have some other setup, you have to play around with it a little.
In the <VirtualHost> section, add


> 
`
RewriteEngine on
RewriteMap    archive-map       prg:/path/to/rewrite_archives.pl
RewriteCond  %{REQUEST_URI}  ^/archives/[0-9]+.html
RewriteRule   ^/archives/(.*).html  /archives/${archive-map:$1} [R=permanent,L]
`



Make sure that mod_rewrite is compiled in or activated in httpd.conf (just search for lines containing mod_rewrite and see if they are not commented out).
After a restart, Apache should now redirect like a champion.
DISCLAIMER: mod_rewrite is deep Apache voodoo, which I don't claim to understand fully, so if you break something while fiddling with it, it's all your fault ;-)
