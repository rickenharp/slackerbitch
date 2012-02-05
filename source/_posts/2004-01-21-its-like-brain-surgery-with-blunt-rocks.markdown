---
date: '2004-01-21 18:14:21'
layout: post
slug: its-like-brain-surgery-with-blunt-rocks
status: publish
comments: true

title: It's like brain surgery with blunt rocks
wordpress_id: '114'
categories:
- Rants
---

It's amazing that there are still coders out there who have never heard of _diff_ and _patch_. I'm helping out at a website, and I was asked to install a few "hacks" into the bulletin board software.
After unpacking the archive containing the hacks I almost burst into tears. These "hacks" look like this:



> 

>     
>     
>     **********************************
>     OPEN ROOT/index.php
>     **********************************
>      
>     Find:
>      
>     if ($bbuserinfo['userid']!=0) {
>      
>     Add after it:
>      
>     $storepoints=$bbuserinfo['storep'];
>      
>     Find:
>      
>     } else {
>       $welcometext = "";
>      
>     Add after it:
>      
>     $storepoints="0";
>     
> 
> 




Sweet mother of god, what the **HELL** were you thinking? The whole document is 32kb long, all in the same vein. Why, oh why, didn't you just make a diff of the sources?
Oh right, probably because you're one of those obnoxious Windows PHP "programmers" (and I use that term very loosely).
To top it off, the archive contained 12 different hacks, all in the same braindead format.
And we _have_ to use this proprietary bulletin board system *cough*vbulletin*cough*, because "we already paid for it, and because of all those cool hacks".

This makes me wonder, why is there no easily extendable bulletin board software available? And with "easy", I mean, through plug-ins, not through messing with the core program.
I guess that's one more thing on my _things-to-code-when-you-have-the-time_ list...
