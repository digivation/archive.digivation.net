---
title: Why Telephones Use Negative Forty-Eight Volts DC
author: Matthew Smith
layout: post
permalink: /2006/08/11/why-telephones-use-negative-forty-eight-volts-dc
tags:
  - electronics
  - theory
  - work
ljID:
  - 86
categories:
  - Journal
  - Musings
  - Technology
---
If you’ve been following the random stories throughout the site, you might just remember a mention of my summer co-op job at Emerson Network Power (if not, you can refer to [this post][1]). The summer has gone well; I’ve made some cash, learned some new tricks, and added a nice new section to my resume. However, there was one little problem that arose&#8230;

<!--more-->

All telephony equipment operates on negative forty-eight volt DC power systems. I was introduced to this “fact of life” at the beginning of the summer, and I found it very odd. Not the fact that its forty-eight volts or that its DC, but that its negative (the positive terminals of the batteries are “ground”). Why the heck was that voltage negative? Anyway, summer continued, I got busy, and I forgot about this little question. Fast forward to the end of summer…

I was sitting in on a division meeting listening to the engineers discuss various aspects of the projects they were working on, when suddenly my supervisor turned to me and asked “So what have you learned this summer?” Caught off guard, I immediately turn red and began to stammer something about “AutoCAD and plant operations and Pro Engineer…” when he cuts me off and says, “No, what did you *learn*?” So then I mumbled something about how telephones and telecommunications networks work, and in doing so, mentioned the oddity of that negative voltage. Immediately he went “Ah ha!” And just like that I had a new research assignment.

After a few days of poring over large communications theory books, searching the Internet, and scratching my head, I knew why the power system was forty-eight volts DC, but no idea why it was negative. After about week of searching, I finally broke down and asked; here is what I learned.

Telephony equipment uses forty-eight volts DC for very simple reasons: DC does not introduce noise on the line and is easily produced from regular lead-acid (vehicle) batteries – which just happen to come in twelve-volt increments (due to the chemical properties of the battery). Forty-eight volts is high enough to be efficient while still being considered a “safe low voltage” and being a multiple of twelve (four batteries make up one “string”).

The negative polarity is much more elusive, but can be summed up in one word: corrosion. Thanks to a bit of research performed by Sir Humphry Davy for the British Navy, we have a technology known as “[cathodic protection][2].” First developed to keep the copper hulls of British naval ships from corroding, this technology has been applied to protecting everything from oilrigs to gas pipelines to telephony cabinets. By keeping the cabinet frame at a more positive voltage than ground, corrosion is reduced and the life of the equipment is increased. Who would have guessed?

 [1]: http://digivation.net/2006/06/08/job-title-engineering-bitch/
 [2]: http://en.wikipedia.org/wiki/Cathodic_protection