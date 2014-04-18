---
title: 'Integration of Facebook / WordPress Login Systems &#8211; Good or Bad?'
author: Matthew Smith
layout: post
permalink: /2007/08/14/integration-of-facebook-wordpress-login-systems-good-or-bad
categories:
  - Wordpress
tags:
  - authentication
  - extension
  - facebook
  - login
  - Wordpress
---
<img src="http://digivation.net/wp-content/uploads/2007/08/key.thumbnail.jpg" alt="Key" class="right" />What if you could log into [WordPress][1] using [Facebook][2] authentication? I&#8217;ve recently been inspired to do more WordPress hacking thanks to the great discussions occurring at [WordPress Bits][3], and this is one of the random thoughts that crossed my mind the other day.

I know that this is possible in some shape or form between the [Facebook API][4] and the WordPress plugin system, I&#8217;m just not sure how to implement it.

I envision a system similar to [OpenID][5] that would allow Facebook users to click a &#8220;login&#8221; button, be directed to Facebook servers where they confirm that they wish to login to the site, and then are redirected back to the WordPress blog. They can now post comments or perform any other task that they are authorized for, all while associated with their Facebook identity. You could even take this a few steps further and have actions (leaving a comment, writing a post, etc) posted to the mini-feed&#8230; and pull in their current profile picture to place beside posts/comments/where ever (there are tons of things you could do with the information from Facebook).

I&#8217;m sure it&#8217;s morally inappropriate to do something like this, seeing as the Facebook system is a &#8220;walled garden&#8221; while OpenID is an open extensible platform. However, the power of Facebook&#8217;s &#8220;social graph&#8221; is not to be underestimated. And I&#8217;m not suggesting replacing OpenID or the WordPress login system &#8211; this would simply be another alternative. **Perhaps a better idea is the creation of a flexible login system** (think [PAM for Linux][6]), making it simple for developers to add new login methods to WordPress. More choice is better, right?

Thoughts, ideas, suggestions? I&#8217;ve looked at the [OpenID plugin for WordPress][7], but I&#8217;m not sure if that would be a beneficial place to start or not and I&#8217;m definitely not yet informed enough to write a plugin to do such (I need to learn more about PHP, the Facebook API, MySQL, and WordPress). Should this be attempted at all? The only reason that this idea struck me as appealing is the shear number of friends, family and acquaintances that I have on Facebook. And I&#8217;m pretty sure this isn&#8217;t something I can tackle by myself (at least not in any reasonable amount of time).

 [1]: http://wordpress.org
 [2]: http://facebook.com
 [3]: http://wpbits.wordpress.com
 [4]: http://developers.facebook.com/
 [5]: http://openid.net/
 [6]: http://en.wikipedia.org/wiki/Pluggable_Authentication_Modules
 [7]: http://verselogic.net/projects/wordpress/wordpress-openid-plugin/