---
date: '2002-10-12 17:55:28'
layout: post
slug: css-insanity
status: publish
comments: true

title: CSS Insanity
wordpress_id: '33'
categories:
- Coding
---


This is starting to drive me nuts. According to CSS2, when I use position:absolute:


> 
 The box's position (and possibly size) is specified with the 'left', 'right', 'top', and 'bottom' properties. These properties specify offsets with respect to the box's containing block.



But that's not happening with Mozilla. The box is positioned with respect to the whole document, not the surrounding DIV-tag.  

Aaaaaaaah!

