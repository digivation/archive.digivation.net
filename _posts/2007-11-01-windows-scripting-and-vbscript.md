---
title: Windows Scripting and VBScript
author: Matthew Smith
layout: post
permalink: /2007/11/01/windows-scripting-and-vbscript
categories:
  - Technology
tags:
  - coding
  - it
  - management
  - visual basic
  - windows
  - wsh
---
As you may (or may not) know, I do IT work at a small local school. When I am not busy solving teachers&#8217; problems, I am tasked with performing various maintenance tasks on these computers. Almost every system that I deal with runs Windows 2000 (the rest run XP or 2003 Server) and these are running on a wide range of hardware (mostly ancient history by today&#8217;s standards). Most recently, I&#8217;ve been updating a bevy of software. I first installed updates by hand &#8211; a long, boring, tedious, and annoying process. Since necessity (or boredom) is the mother of invention, I quickly decided it would be easier to throw all of the commands into a [batch file][1] instead of clicking through each install.<!--more-->

Then I remembered that batch files have been around since the dawn of time and there are better ways to do things (such as [Linux][2]). Unfortunately I don&#8217;t have the power of [bash][3] at hand&#8230; so I investigated the [Microsoft way][4] of doing things &#8211; most glorious (or not) VBScript (or JScript). Since I found more VBScripts than JScripts, I decided to tinker around with VBS for a while and see what could be done.

I hate VBS. I keep wanting to use Java or C syntax. Arg. So annoying. But it&#8217;s better than the command line. With a little hacking (and copying and pasting), I have managed to create a simple &#8220;stupid&#8221; script that runs the install files. As I develop it more, I&#8217;ll post up what I&#8217;ve got. For now, we have this:

[vb]  
&#8216; create the shell object  
Set objShell = CreateObject(&#8220;WScript.Shell&#8221;)

&#8216; do updates

msgbox &#8220;Preparing to install Updates.. will take a few moments&#8221;

&#8216; Flash Plkayer  
objShell.Run &#8220;.\Adobe\install\_flash\_player.exe /s&#8221;,,True  
objShell.Run &#8220;.\Adobe\flashplayer9\_install\_ie.exe /s&#8221;,,True

&#8216; Shockwave  
objShell.Run &#8220;.\Shockwave\Shockwave\_Installer\_Slim.exe /s&#8221;,,True

&#8216; Quicktime  
if GetOS = &#8220;W2K&#8221; then  
objShell.Run &#8220;.\Quicktime\QuickTimeWin2000.exe&#8221;,,True  
else  
objShell.Run &#8220;.\Quicktime\QuickTimeInstaller.exe /passive&#8221;,,True  
end if

&#8216; Windows Media Player  
if GetOS = &#8220;W2K&#8221; then  
objShell.Run &#8220;.\WMP\MP9Setup.exe /Q&#8221;,,True  
else  
objShell.Run &#8220;.\WMP\wmp11.exe&#8221;,,True  
end if

&#8216; JAVA  
objShell.Run &#8220;.\Java\jre-6u3-windows-i586-p-s.exe /s&#8221;,,True

&#8216; Adobe Reader  
objShell.Run &#8220;.\Adobe\AdbeRdr810\_en\_US.exe /sAll&#8221;,,True

&#8216; Time Zone Update

objShell.Run &#8220;.\TZUpdate\DaylightSavingFix.exe /qinstall&#8221;,,True

msgbox &#8220;Installation Complete&#8221;

&#8216; Get OS Function

Function GetOS()  
&#8216;Will work with most versions of WSH.  
&#8216;CMD window will not display.  
Const OpenAsASCII = 0  
Const FailIfNotExist = 0  
Const ForReading = 1

Dim WshShell : Set WshShell = CreateObject(&#8220;WScript.Shell&#8221;)  
Dim FSO : Set FSO = CreateObject(&#8220;Scripting.FileSystemObject&#8221;)  
Dim sTemp, sTempFile, fFile, sResults  
sTemp = WshShell.ExpandEnvironmentStrings(&#8220;%TEMP%&#8221;)  
sTempFile = sTemp &#038; &#8220;\runresult.tmp&#8221;

WshShell.Run &#8220;%comspec% /c ver >&#8221; &#038; sTempFile, 0, True

Set fFile = FSO.OpenTextFile(sTempFile, ForReading, FailIfNotExist, OpenAsASCII)

sResults = fFile.ReadAll  
fFile.Close  
FSO.DeleteFile(sTempFile)

Select Case True  
&#8216;Add more info to the 98 and 95 to get the specific version. i.e. 98SE 95 a,b,or c  
Case InStr(sResults, &#8220;Windows 95&#8243;) > 1 : GetOS = &#8220;W95&#8243;  
Case InStr(sResults, &#8220;Windows 98&#8243;) > 1 : GetOS = &#8220;W98&#8243;  
Case InStr(sResults, &#8220;Windows Millennium&#8221;) > 1 : GetOS = &#8220;WME&#8221;  
Case InStr(sResults, &#8220;Windows NT&#8221;) > 1 : GetOS = &#8220;NT4&#8243;  
Case InStr(sResults, &#8220;Windows 2000&#8243;) > 1 : GetOS = &#8220;W2K&#8221;  
Case InStr(sResults, &#8220;Windows XP&#8221;) > 1 : GetOS = &#8220;WXP&#8221;  
Case Else : GetOS = &#8220;Unknown&#8221;  
End Select  
End Function  
[/vb]

The GetOS function came from [here][5]. I am still developing this and I have written a function to detect the service pack level:

[vb]  
Function GetSP()  
&#8216;For NT Systems  
Dim SP_VER  
Set Shell = WScript.CreateObject(&#8220;WScript.Shell&#8221;)

Select Case Shell.RegRead (&#8220;HKEY\_LOCAL\_MACHINE\SYSTEM\CurrentControlSet\Control\Windows\CSDVersion&#8221;)  
Case 256  
GetSP = &#8220;SP1&#8243;  
Case 512  
GetSP = &#8220;SP2&#8243;  
Case 768  
GetSP = &#8220;SP3&#8243;  
Case 1024  
GetSP = &#8220;SP4&#8243;  
Case 1280  
GetSP = &#8220;SP5&#8243;  
Case 1536  
GetSP = &#8220;SP6&#8243;  
End Select

Set Shell = Nothing

End Function  
[/vb]

That function uses information found [here][6]. I will probably refine this script to detect currently installed software (and version, if possible), then only run the updates that are needed. I also need to find a reliable way to run Windows Updates&#8230; so stay tuned!

 [1]: http://en.wikipedia.org/wiki/Batch_file
 [2]: http://www.linuxcommand.org/writing_shell_scripts.php
 [3]: http://en.wikipedia.org/wiki/Bash
 [4]: http://en.wikipedia.org/wiki/Windows_Script_Host
 [5]: http://www.visualbasicscript.com/m_25374/tm.htm
 [6]: http://www.windowsnetworking.com/kbase/WindowsTips/WindowsNT/RegistryTips/Miscellaneous/Determineservicepacklevel.html