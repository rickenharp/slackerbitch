---
date: '2003-02-01 17:59:23'
layout: post
slug: blogging-via-mail-securely
status: publish
comments: true

title: Blogging via mail, securely
wordpress_id: '75'
categories:
- Weblogs
---

Since I couldn't find a decent (for me) desktop blogging client for Movable Type for Linux, I have decided to make it possible to blog from my favourite application: [mutt](http://www.mutt.org/)
To add some security to the script, it only posts entries that have a good [GnuPG](http://www.gnupg.org) signature, and even then only if the fingerprint of the key used to sign is allowed to post. And signing emails with gpg is a snap with mutt.
By adding custom headers to the mail, you can even set the category of the entry and ping TrackBack URLs.
The script takes the value of the X-MT-Category header, and if that matches the name of an existing category, this is set as the primary category for that entry. <del>Unfortunately, this category doesn't show up on the main index after the script rebuilds the entry, even though it _does_ show up in the admin section and after a manual rebuild. Maybe someone with a better understanding of the MT Perl API can shed some light on this...</del>[Kevin Shay](http://www.staggernation.com) found the reason for this, it had to do with MT doing some caching. Disabling this caching for the rebuild removes this problem
And pinging TrackBack URLs happens via the X-MT-Ping header. This header can appear multiple times, and each URL gets pinged.
It's still the first version of the script, so it's still a little rough. I have been running it under qmail and vpopmail, and to get the script to rebuild the entry, I had to make blog directory writable to the vpopmail group. It works, but if someone has a more elegant approach to this, I am all ears.
This script uses a few CPAN modules:





  * GnuPG


  * MIME::Parser


  * Mail::Header


  * MIME::QuotedPrint



And here's the code: [mail2blog.pl](http://slackerbit.ch/mail2blog.pl). Use at your own risk, if it eats your server, sets your house on fire or lets your hair fall out, I will say "I told you so" :-)
