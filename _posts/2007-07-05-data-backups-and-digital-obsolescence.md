---
title: Data, Backups, and Digital Obsolescence
author: Matthew Smith
layout: post
permalink: /2007/07/05/data-backups-and-digital-obsolescence
categories:
  - Technology
tags:
  - data
  - Technology
---
A brilliant thinker ahead of his time, [Vannevar Bush][1] envisioned a device he called the [memex][2] which would supplant one&#8217;s memory, allowing you to store and retrieve texts, ideas, photographs, and other items of interest. These bits of data could be linked together in meaningful ways, providing a way to explore the relationships between various &#8220;memories.&#8221; Sound familiar (I recommend reading read [this][3])?

Now that we use something far better than Mr. Bush&#8217;s Memex, have you taken a moment to reflect on the amount of data that you create? From documents to pictures to music to videos, we create and use a vast amount of data on a daily basis. Most of us don&#8217;t even think about this until we run out of space or have a catastrophic hard drive crash resulting in a gut-wrenching realization (&#8220;I just lost all my music&#8230;&#8221;). I started contemplating these things anew after reading my college&#8217;s [recent post][4], as well as David&#8217;s [reflections][5] [on the topic][6]. Looking at these two articles reminded me of an old post (May &#8217;06) by [Mark][7] that also touched [on the topic of data preservation][8].

What exactly is one to do? I&#8217;ve done some brief research on the topic, but have yet to find a solution that satisfies me. I use a desktop computer that houses the majority of my data (some 600 GB of stuff), in addition to a laptop (used only for doing stuff away from home). I also use a 2 GB thumb drive that travels with me, as well as a portable 160 GB hard drive (for lugging around larger data). All of these devices need to be backed up &#8211; and the older I get, the more important this becomes! Not only do I produce more data, but the importance and sensitivity of the data increases (e.g. I&#8217;ve started using Quicken). On top of all this, there&#8217;s this website &#8211; as I learned once before, it&#8217;s not impermeable, and the data can be lost &#8211; that would be almost two years of writing, up in smoke. Sure, maybe it&#8217;s not all the most valuable content in the world, but I fancy that I&#8217;d reminisce sometime in the future.

The backup and storage problem has a number of solutions, all sub-optimal and far to expensive for me. From co-located servers to storeage sites like [StrongSpace][9], a myriad of options exist. A Network Attached Storage (NAS) device sounds like a decent solution to me, but at this current moment, I can&#8217;t afford one. How am I supposed to back up my precious files? The only solution that I currently use is having copies of the really important things on different devices, though none of them are dedicated backup mechanisms, nor are they particularly secure. I may investigate the possibility of creating a Linux file server out of leftover parts. The possibility of using [Subversion][10] to create re-visioned backups with incremental storage and the ability to &#8220;roll back&#8221; to an older version if something happens to a current version. By storing the subversion repository on a redundant [RAID][11] (level 5), you could reduce the risk to your data by a tremendous amount.

Anyone have a few <strike>500 GB</strike> 1 TB hard drives they&#8217;d like to donate?

The second problem is digital obsolescence and the danger of proprietary file formats. As you&#8217;ve most likely noticed, the digital world moves extremely fast with a constant evolution of new formats, devices, and technology. As David alluded to in his [post][5], when the software you use becomes obsolete or no longer functions, how do you get to that valuable data? What happens if you want to change operating systems? This is one of the biggest reasons why proprietary formats and DRM are so bad for your files &#8211; they tie you to a vendor and limit your options. When that vendor abandons a software line or goes out of business, [what becomes of your stuff][12]?

I would like to convert more of my documents to an open format, and I am actively trying to use as many open-source tools as possible. By employing open standards over proprietary junk, I am keeping my options open &#8211; I can change software, move to a new OS, and find the tools (or create them) to open an old document at some future date, despite the whims of some software vendor

Hopefully with thoughtful planning and management, I can archive my digital creations for many years to come. I&#8217;m sure that the simple thoughts presented here are not the best way (and maybe not even on the right track), but hopefully they will spark an interest in protecting your documents and media.

If you have any ideas or suggestions, be sure to leave a comment!

 [1]: http://en.wikipedia.org/wiki/Vannevar_Bush
 [2]: http://en.wikipedia.org/wiki/Memex
 [3]: http://sciam.com/print_version.cfm?articleID=CC50D7BF-E7F2-99DF-34DA5FF0B0A22B50
 [4]: http://digivation.net/2007/07/02/cds-vs-music-files/
 [5]: http://www.davidcomeaux.com/2007/04/02/a-musical-snack-an-esoteric-tale-and-an-observation/
 [6]: http://digivation.net/2007/07/02/cds-vs-music-files/#comment-6627
 [7]: http://diveintomark.org/
 [8]: http://diveintomark.org/archives/2006/05/08/backup
 [9]: http://www.strongspace.com/
 [10]: http://en.wikipedia.org/wiki/Subversion_%28software%29
 [11]: http://en.wikipedia.org/wiki/RAID
 [12]: http://news.bbc.co.uk/1/hi/technology/6265976.stm