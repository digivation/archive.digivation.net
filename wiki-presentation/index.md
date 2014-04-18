---
title: Collaborative Writing with Wikis
author: Matthew Smith
layout: page
---
### Introduction

Over the past few years of my engineering education, there have been several occasions where I had to collaborate on a document with a team. The normal course of action simply involved using Microsoft Word to write portions of the document and emailing the around the group until a final document was produced.

The undergraduate engineering experience culminates in a year long team design project, appropriately known as &#8220;senior design,&#8221; a course feared by all engineering students who have not yet completed it. During the senior design process, the team creates both a preliminary design review document (the PDR) and a critical design review document (the CDR), each of which weighs in around thirty pages of technical documentation. Additional documentation is also generated throughout the process, such as data, notes, and proposals.

When my team approached the PDR, we used the standard Word+Email approach and quickly learned of its shortcomings. As we began the second phase of senior design, I began to look for an alternative method of writing our documentation so that we would not experience the same frustrations when writing the CDR. The solution that I devised involved using a specifically formatted wiki to collaboratively write the CDR. If I had come up with this solution earlier in the process (such as at the very beginning of the course), we could have extended our wiki to provide a central repository for collaborating on all of our documentation, including storage space for the various data generated through the design process. Needless to say, this would have significantly streamlined our design process by cutting down on the amount of paperwork that we were required to keep track of and providing us with a centralized and always available repository of information on our project.

Over the next few pages, I will outline the specific steps to recreating the wiki that my team used. These instructions apply to DokuWiki, which I chose due to its&#8217; power and simplicity (it only requires a web server running PHP). While the instructions given here are specific, **the general ideas can be applied to any wiki software**. I recently gave a presentation on the general idea, which you can find below. I will also add a video of the presentation soon.

You can visit my [CDR site][1], or check out the following resources.


  Resources 
    
      Download DokuWiki
    
    
      DokuWiki Syntax Reference
    
    
      Presentation on Collaborative Writing with Wikis [PDF]
    
    
      Presentation Handout [PDF]
    
  
  
  
    Contents
  
  
  
    
      Page 1: Introduction
    
    
      Page 2: Installing DokuWiki
    
    
      Page 3: Configuring the Wiki for Collaborative Writing
    
    
      Page 4: Preparing the Wiki Layout
    
    
      Page 5: Conclusion
    
  
  
  
    Coming soon
  
  
  
    
      Video presentation
    
    
      Technical details on wiki creation (under construction)
    
  




### Installing DokuWiki

The installation process for DokuWiki is relatively simple. Before proceeding, you will need the following:

*   **Web server**  
    If you do not yet have a web server, there are several possible options. If you simply wish to test the procedures without actually setting up a real web site, you can install [XAMPP][2], a personal web server package that has everything you need to test the wiki on your own PC. While the test site will not be available from the internet, you can play around with all the configuration settings and familiarize yourself with the software.For this website, I use [Sitelutions][3] for the domain name and [WebHostingBuzz][4] for my web host. If you are a Mercer student, speak with Dr. Grady about being able to use Mercer&#8217;s own web servers to host your project site.
*   **PHP**  
    Your webserver must be running [PHP 4.3.10][5] or better. If you installed XAMPP, this comes pre-installed and there is nothing else to worry about. Most other web hosts will have this installed as well.
*   **A Web Browser (Firefox, Internet Explorer, etc)  
    **Any recent browser will work fine. Firefox has built-in spell checking support, which is very handy
*   **FTP Client  
    **If you are uploading the DokuWiki files to your web host, you need some sort of FTP program to accomplish this. [FileZilla][6] is an excellent choice. If you are using XAMPP on your PC, you can simply copy the files with your file manager.

**Installation of DokuWiki**

1.  Download the latest DokuWiki package from [here][7].
2.  Extract the file to your computer (it is a GZIP file that can be opened with a program such as [7-Zip][8]). You should now have a folder called dokuwiki-xxxx-xx-xxx.
3.  Copy the files to the appropriate directory on your server (if you are using XAMPP, copy the dokuwiki directory to \htdocs\ and rename the dokuwiki-xxxx-xx-xxx to something like wiki. If you do this, you should be able to access your local DokuWiki installation from ).
4.  Open the install.php file in your web browser (if you are using XAMPP, you should be able to access the install page from , assuming you followed the above step to the letter). Follow the directions to configure your installation. I recommend enabling the ACL option and selecting &#8220;Public Wiki&#8221; for initial ACL policy setting. This will allow you to control who can edit your wiki. For more information on the options, visit [this page][9].
5.  You should now have a fully functioning wiki. Proceed to the next page to customize the installation for collaborative writing. If you need more information, see the [DokuWiki install instructions][10].



### Configuring the Wiki for Collaborative Writing

Before the wiki is ready to serve as a collaborative medium, a few minutes of prep time are needed.

**Adding the Status Icons**

One of the useful &#8220;modifications&#8221; to DokuWiki that helped my team keep track of our progress on the document was the inclusion of icons to visually indicate the level of completion of each section. If you look at the [index][11] for my senior design wiki, you will see a series of green check marks beside each item (along with a handy table at the top of the page providing a quick reference to the meanings of each icon). By using these icons, we could simply glance over the front page of the wiki and figure out what needed work.

To make the icons simple to use, I simply configured some new &#8220;smilies,&#8221; which allow you to type a text shortcut (like :1:, :2:, :3:, :done:, etc) into the editor instead of a lengthy url to the graphic file. To do this, we must place the icons in **/lib/images/smileys/** and then configure the file **/conf/smileys.conf**. The icons that I used came from [famfamfam][12]&#8216;s fantastic set called &#8220;[mini icons][13].&#8221; Of course you can use any icon/text short-cut combination that you wish, but this is what I used:

> :1:	flag_red.gif
:2:	flag_orange.gif
:3:	flag_green.gif
:done:	icon_accept.gif
:alert:	icon_alert.gif

Just append lines like these to the end of your smileys.conf file, upload the files you want to the smileys directory, and you can start using your new text shortcuts for your new status icons!

**Adding Additional Upload File Types**

DokuWiki allows you to upload files to your wiki, but only accepts a pre-defined set of file types. If you wish to upload additional files beyond the default settings, you will need to edit the file **/conf/mime.conf**. I added the following lines to my mime.conf file to enable MS Project files, videos, and a few other file types that we needed to store in the wiki.

> mpp	application/msproject
sch	application/eagleschematic
brd	application/eagleboard
avi	video/x-msvideo
wmv	audio/x-ms-wmv

If you need help with mime types, this [Google search][14] should get you pointed in the right direction.  


### Preparing the Wiki Layout

Before the writing begins, it is a good idea to create a structured organization on the wiki that will serve to guide the writing process. As you may notice from my [site][15], we were focused solely on writing a single document. Thus, the root of the wiki serves as a &#8220;table of contents&#8221; for the entire document. By subdividing the document into reasonable sections, many editors can work on the document simultaneously (**only one person can be editing any given page at a time**), so it is a good idea to plan out your document divisions before the writing begins.

It is entirely possible to organize the wiki in a way that would allow for multiple documents to be created on the same wiki. Instead of placing your table of contents in the wiki root, you would create links to sub-pages containing the various tables of contents for any documents to be worked on.

Once you decide on your layout, implement it using the [wiki syntax][16].



### Conclusion

 [1]: http://digivation.net/senior_design/
 [2]: http://www.apachefriends.org/en/xampp.html
 [3]: http://www.sitelutions.com/
 [4]: http://www.webhostingbuzz.com
 [5]: http://www.php.net/
 [6]: http://filezilla-project.org/
 [7]: http://www.splitbrain.org/projects/dokuwiki
 [8]: http://www.7-zip.org/
 [9]: http://wiki.splitbrain.org/wiki:installer
 [10]: http://wiki.splitbrain.org/wiki:install
 [11]: /senior-design
 [12]: http://www.famfamfam.com/
 [13]: http://www.famfamfam.com/lab/icons/mini/
 [14]: http://www.google.com/search?q=mime+types
 [15]: /senior_design
 [16]: http://wiki.splitbrain.org/wiki:syntax
