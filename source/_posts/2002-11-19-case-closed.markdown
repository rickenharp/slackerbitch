---
date: '2002-11-19 18:07:58'
layout: post
slug: case-closed
status: publish
comments: true

title: Case Closed
wordpress_id: '53'
categories:
- Technology
---

Lately, I had trouble burning audio CDs. What was curious about it was, that I had the same problems at home and at work, and I didn't have them a while ago, on neither computer.
After some sleuthing, I found the solution, and here it is, in case anyone has the same problem: At work, I used to have an Adaptec SCSI card, that got put into out backup server, and as a replacement I put in a DawiControl 2974 card.
And at home, I used to have an Adaptec, too, which got exchanged for a Tekram DC390 card. And both the DawiControl and the Tekram card use the same driver (tmscsim). When I switched to an older driver for the card, the burning worked like a charm.
So, if you have a CD burner (in my case a HP 9200), and a SCSI card using the tmscsim driver, expect cdrdao to abort after 3 Megabytes with an error. Short term solution: Use the (old and unmaintained) AM53C974 driver, or get another SCSI card.
