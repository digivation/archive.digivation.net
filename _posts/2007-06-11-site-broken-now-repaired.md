---
title: Site Broken, Now Repaired
author: Matthew Smith
layout: post
permalink: /2007/06/11/site-broken-now-repaired
categories:
  - Site Updates
tags:
  - Wordpress
---
Notice: When upgrading to WordPress 2.2, disable all plugins before beginning the upgrade.

This vital piece of information was ignored, and resulted in an unaccessible back-end for around a week (mainly due to my own laziness). However, all is well now.

If you happen to be getting a blank page when loading &#8220;upgrade.php&#8221; (PHP out of memory errors in the log), or seeing random blank pages after trying to save posts, moderate comments, etc, you should go through and disable your plugins to find out which one is responsible. In my case, it was the Google Sitemaps plugin (not by Google). If you have upgraded and cannot access the admin interface, use phpMySql or something similar to remove the content of the &#8220;activate\_plugins&#8221; key in the wp\_options table. Then upgrade and re-enable your plugins!

Update: After some tinkering around and deleting / re-uploading of files, the Sitemaps plugin has started working properly again. This is good; sitemaps help your search engine rankings.