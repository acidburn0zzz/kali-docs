---
title: NetHunter Rootless
description:
icon:
date: 2019-12-20
type: post
weight: 100
author: ["re4son",]
tags: ["",]
keywords: ["",]
og_description:
---

## NetHunter Rootless Edition

##### *Maximum flexibility with no commitment*  

Install Kali NetHunter on any stock, unrooted Android device without voiding the warranty.  

[![](images/010-NH-Rootless-Installation_Start_s.jpg)](images/010-NH-Rootless-Installation_Start.jpg)

[![](images/020-NH-Rootless-KeX_s.jpg)](images/020-NH-Rootless-KeX_s.jpg)

&nbsp;  

Prerequisite:  
--------------  

Android Device  
(Stock unmodified device, no root or custom recovery required)  

&nbsp;  

Installation:  
--------------  

* Install the NetHunter-Store app from https://store.nethunter.com  
* From the NetHunter Store, install __Termux__, __NetHunter-KeX client__, and __Hacker's keyboard__  
  _Note:_  
       _The button "install" may not change to "installed" in the store client after installation - just ignore it._  
      _Starting termux for the first time may seem stuck while displaying "installing" on some devices - just hit enter._ 
  
* Open Termux and type:  
  `termux-setup-storage`  
  `pkg install wget`   
  `wget -O install-nethunter-termux https://offs.ec/2MceZWr`  
  `chmod +x install-nethunter-termux`  
  `./install-nethunter-termux`  

  

&nbsp;

Usage:  
-------  

Open Termux and type one of the following:  

| Command                | To                                                      |
| ---------------------- | ------------------------------------------------------- |
| `nethunter`            | start Kali NetHunter command line interface             |
| `nethunter kex passwd` | Configure the KeX password (only needed before 1st use) |
| `nethunter kex &`      | start Kali NetHunter Desktop Experience                 |
| `nethunter kex stop`   | stop Kali NetHunter Desktop Experience                  |

Note: The command `nethunter` can be abbreviated to `nh`.  
_Tip: If you run kex in the background (`&`) without having set a password, bring it back to the foreground first when prompted to enter the password, i.e. via `fg <job id>` - you can later send it to the background again via `Ctrl + z` and `bg <job id>`_  

To use KeX, start the KeX client, enter your password and click connect  
_Tip: For a better viewing experience, enter a custom resolution under "Advanced Settings" in the KeX Client_   

 &nbsp; 

## NetHunter Editions:

Please refer to [this table](../#1-0-nethunter-editions) for a comparison of the different NetHunter editions.  

&nbsp;  

## Tips:  

1. Run `apt update && apt full-upgrade` first thing after installation. If you have plenty of storage space available you might want to run `apt install kali-linux-full` as well.
2. Firefox won't work on unrooted devices. Just replace it with Chromium via:  
   `apt remove firefox-esr`  
   `apt install chromium`  
   Next:  
   ~ Find the "Chromium Web Browser" item in the application menu  
   ~ right click and select "Edit Application"  
   ~ Change the "Command"  to `/usr/bin/chromium --no-sandbox %U`  
3. All of the penetration testing tools should work but some might have restrictions, e.g. metasploit works but doesn't have database support. If you discover any tools that don't work, please post it in our [forums](https://forums.kali.org/forumdisplay.php?14-NetHunter-Forums). 
4. Some utilities like "top" won't run on unrooted phones.
5. Perform regular backups of your rootfs by stopping all nethunter sessions and typing the following in a termux session:  
   `tar -cJf kali-arm64.tar.xz kali-arm64 && mv kali-arm64.tar.xz storage/downloads`  
   That will put the backup in your Android download folder.  
   _Note: on older devices, change "arm64" to "armhf"_  
6. Please join us in our [forums](https://forums.kali.org/forumdisplay.php?14-NetHunter-Forums) to exchange tips and ideas and be part of a community that strives to make NetHunter even better.