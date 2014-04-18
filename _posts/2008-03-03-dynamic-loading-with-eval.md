---
title: Dynamic Loading with eval()
author: Matthew Smith
layout: post
permalink: /2008/03/03/dynamic-loading-with-eval
categories:
  - Technology
tags:
  - dynamic
  - eval()
  - includes
  - installer
  - jscript
  - load
  - programming
---
<img src="http://archive.digivation.net/wp-content/uploads/2008/01/code.png" class="left" alt="Code" />I may not be able to explain how cool this is, but I&#8217;m going to try.

Right now I&#8217;m working on a replacement for the [nasty VBScript][1] I posted a while back that updates the software installed on the computers at work. Sure, the script did it&#8217;s job but it wasn&#8217;t pretty to look at and updating it or adding new software is a pain in the arse.

To make my new and improved version, I wanted to redesign my installer/updater code in a nice, modular, [object-oriented][2], easy to update manner. I devised a modular solution where I would write one main script that would perform all the heavy lifting, with the specifics of each application provided by simple scripts that could be added, removed, and updated with ease.

The main script scans a directory looking for all files that end in &#8220;.app.js,&#8221; loads them up, and executes the commands found within. Each .app.js file provides a single class, with the same name as the first part of the file name (so **foo**.app.js would provide a class called **foo**). This class in turn provides a set of properties that the main script can use to perform actions (such as checking versions, upgrading software, removing software&#8230; you get the idea).

Now the tricky part? You have no idea what the class names are prior to run time. So you can&#8217;t create new objects using &#8220;var bar = new foo().&#8221;

I&#8217;d learned about the JScript &#8220;[eval()][3]&#8221; statement a while back, which I used extensively for simulating C&#8217;s &#8220;[#include][4]&#8221; statement. The cool thing about it is that eval() performs JScript execution on a text stream&#8230; so to perform dynamic loading with eval(), I simply used concatenation to produce a string like such:

[js]  
var callString = &#8220;new &#8221; + methods.call[index] + &#8220;()&#8221;;  
[/js]

and then evaluated the string:

[js]  
var newObject = eval(callString);  
[/js]

And it works like a charm! Now I can run a loop over my array of class names, create new objects, and perform all my other nifty little tasks. It looks simple, but I had to contemplate this for a second before the light bulb flashed on&#8230; I&#8217;m sure someone out there has already done this, been just as excited as me, and posted about it on their own blog. However, this is the solution I came up with off the top of my head without the assistance of any Google searches, so I&#8217;m going to be happy and post about it here before I ever check Google!

 [1]: http://archive.digivation.net/2007/11/01/windows-scripting-and-vbscript
 [2]: http://en.wikipedia.org/wiki/Object-oriented_programming
 [3]: http://www.w3schools.com/jsref/jsref_eval.asp
 [4]: http://developer.apple.com/documentation/developertools/gcc-4.0.1/cpp/Include-Syntax.html