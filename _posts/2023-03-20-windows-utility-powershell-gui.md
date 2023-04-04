---
title: "Windows Utility (PowerShell GUI)"
date: "2023-03-20"
categories: 
  - "support"
  - "tips"
  - "tutorial"
  - "windows"
---

**Windows Utility (PowerShell GUI) - By Chris Titus**

This Windows utility seems pretty handy from the testing I have done with it. Go check out Chris' Website, he has some pretty cool stuff going on [https://christitus.com/](https://christitus.com/).

Here is the GitHub: [https://github.com/ChrisTitusTech/winutil](https://github.com/ChrisTitusTech/winutil)

You can run this Utility Software straight from an Admin PowerShell using:  **irm christitus.com/win | iex**

In case you don't know what these PowerShell commands do (I admit, I was a little shaky on them) here is a breakdown:

**IRM**

The irm command means "Invoke-RestMethod".

_"The Invoke-RestMethod cmdlet sends HTTP and HTTPS requests to Representational State Transfer (REST) web services that returns richly structured data."_ [Source](https://www.pdq.com/powershell/)

**IEX**

The iex command stands for "Invoke-Expression".

_"The Invoke-Expression cmdlet evaluates or runs a specified string as a command and returns the results of the expression or command. Without Invoke-Expression , a string submitted at the command line would be returned (echoed) unchanged."_  [Source](https://www.pdq.com/powershell/)

**What does it do?**

**INSTALL**

There are several different options for common installs listed here. The categories of software listed are Browsers, Communications, Development, Document, Games, Pro Tools (Very Useful installs), Microsoft Tools, Multimedia Tools, Utilities. The install area reminds me of ninite.com except with more useful tools for sysadmins.

The next gem on this tab is the "Upgrade Installs" button. This button will search your currently installed software and check for updates. If there are updates it automatically install them. I ran this and it updated a lot of software for me! Pretty neat!

![](/assets/images/image-3-1024x679.png)

**TWEAKS**

There are several really good options with the Tweaks tab on the Utility software, most of which I use different PowerShell Scripts to accomplish. Along with all the options there is also a "recommended selections" option that will select the options the Author has deemed to be the best for the system type. Don't worry about clicking these recommended options, they don't auto-apply, they just check the options. You still have to manually click the "Run Tweaks" button.

![](/assets/images/image-2-1024x677.png)

**CONFIG**

The Config tab just a few options, ranging from Windows Features installer to Windows Fixes and also includes Legacy Control Panel options.

![](/assets/images/image-1-1024x683.png)

**UPDATES**

The Updates tab deals with setting Windows Update options. These update options are limited to "Default OOB (Out of Box)", Security (Recommended), and Disable all updates.

![](/assets/images/image-4-1024x667.png)

Source: [One Tool for Everything](https://www.youtube.com/watch?v=vXyMScSbhk4)

![](images/image-5.png)

Source: [https://christitus.com/one-tool-for-everything/](https://christitus.com/one-tool-for-everything/)
