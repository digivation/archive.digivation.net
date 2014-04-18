---
title: 'Texts from your BlackBerry have &#8220;@&#8221; between the words?'
author: Matthew Smith
excerpt: |
  <img class="right size-medium wp-image-517" title="BlackBerry 8700" src="http://archive.digivation.net/wp-content/uploads/2008/07/url-193x300.jpg" alt="" width="193" height="300" />So, yes, I just recently joined the bandwagon and enabled sms messages on my cell phone. No, I'm not "slow" or "behind the times." My phone was, until recently, attached to my parents' family plan - and they blocked all messages instead of paying the extra $30/month. Since I now have my own steady income, I have spun my number off to my own plan and enabled text messages in the process. Hurray for independence (and the costs of such freedom).
layout: post
permalink: /2008/07/15/sms-blackberry-at
categories:
  - Technology
tags:
  - data
  - error
  - phone
  - sms
  - text
---
<img class="right size-medium wp-image-517" title="BlackBerry 8700" src="http://archive.digivation.net/wp-content/uploads/2008/07/url-193x300.jpg" alt="" width="193" height="300" />So, yes, I just recently joined the bandwagon and enabled sms messages on my cell phone. No, I&#8217;m not &#8220;slow&#8221; or &#8220;behind the times.&#8221; My phone was, until recently, attached to my parents&#8217; family plan &#8211; and they blocked all messages instead of paying the extra $30/month. Since I now have my own steady income, I have spun my number off to my own plan and enabled text messages in the process. Hurray for independence (and the costs of such freedom).

Shortly after beginning my own &#8220;sms revolution,&#8221; a few people began complaining that messages they received contained an &#8220;@&#8221; between each word of the message. Of course I immediately think &#8220;well obviously that&#8217;s an encoding problem.&#8221; And sure enough&#8230; here&#8217;s how you solve it:

Navigate to *Options -> SMS Text* and change *Data Coding* to *7 bit*. I&#8217;m assuming it was previously set to *UCS2*. A quick word of warning: if you need to send messages containing some foreign characters, you must leave your encoding set to UCS2 and tell your friends to get a better phone. Another bonus is that now your messages can actually contain 160 characters instead of the 62 character limit of the extended letter set.

The more you know&#8230;