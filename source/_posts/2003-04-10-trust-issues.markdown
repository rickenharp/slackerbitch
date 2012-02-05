---
date: '2003-04-10 11:13:37'
layout: post
slug: trust-issues
status: publish
comments: true

title: Trust Issues
wordpress_id: '93'
categories:
- Technology
---

Today, I decided to reinstall our intranet file server. For several reasons:




  * It's still running RedHat 7.2


  * I fiddled around with LDAP for UNIX and SMB auth. Didn't quite work


  * After a power outage yesterday, I cannot NFS-mount one directory on the server. All others are okay, just this one directory refuses to work. It did work previous to the outage.



So, I tell my cow-orker, and he asks "What are you gonna put on the box?"
Well, that's an easy answer: "RedHat 7.3"
Him: "Why don't you use 8 or even 9?"

To be honest, it's a gut feeling. Starting with 8, RedHat has become too colorful and eyecandyish to be on a server, for my taste. I use 8 as my desktop machine, because I love the antialiased fonts in Mozilla, but when it comes to critical servers, I prefer to stay a little behind the tech curve. When Redhat 7 came out, I still put 6.2 on a lot of machines, because by that time, a lot of the kinks had been ironed out of 6.2, and, honestly, 7.0 was not the best release...

So my answer was "Because I don't trust Redhat newer than 7.3 on critical servers". And because I am a stubborn old fart!
