---
title: "How I struggled to build a Nextcloud server (and won!)"
date: 2020-06-28T23:36:18-04:00
draft: true
---

### WHY (AM I GOING THOUGH WITH ALL THIS)?
I figured, if *I* have to struggle, I may as well invite others onto the strugglebus as well.

I really like taking notes. Notes are an extension of my stupid brain, which can't remember a *damn* thing on its own. All these notes were being stored on Google's servers, which [doesn't] [seem like] [the best] [idea].

This isn't so much a guide or tutorial - more just me explaining the massive effort it took to set this damn thing up. I hope somebody someday learns something from my suffering, or is maybe just entertained.

### THE INSTALL
Installing everything was shockingly difficult. There can't just be a little `sudo apt install nextcloud` action, no no no no no. You need to install each little bit yourself, by hand, and glue each piece together (`nextcloud` isn't even in the apt repo, of course you have to download / unpack something called a *"tarball"* yourself).

This made some sense as I learned (sorta, vaguely) how Nextcloud works - It's running on a webserver directly on your machine, handling all the networking and whatnot, with a full-on SQL database and lots of PHP magic happening too. So, it's understandable that Nextcloud has to spread it's mischievous tentacles in each crevice of your pure OS install.

I followed the [Nextcloud documentation](https://docs.nextcloud.com/server/latest/admin_manual/index.html), which sure does exist. In their defense, all of their software is [free and open], including the docs, so I could have submitted any number of changes, and yet here I am selfishly writing this blog.

### THE WIFI DISPLAY CONUNDRUM
So here I am, all ___ and happy with my brand new Raspberry Pi running a fresh ~~Raspbian~~ Raspberry Pi OS. As I'm setting everything up (and, for some reason, using its surprisingly not bad lightweight version of Chromium), the WiFi starts cutting in-and-out. This has been a persistent problem ever since I switched my main devices (personal desktop and laptop) to Linux, so I figured this was the same / similar problem as the [mysterious Intel wifi+bluetooth death bug plaguing Linux for years, apparently].

I do some more digging, and find what I believe to be the truth (or, as close to any of us mere mortals will ever get to a truth). There appears to be a widely understood problem with the Pi 4 where the signals coming out from the HDMI (which are shaped like squares?) are the same frequency(?) as the WiFi. So, if your display resolution is pumped up high enough, and that HDMI is cranking out lots of square signals, the wifi gets totally borked. Neat.

This is clearly absurd, and I hate it. Hardware is bad, and everyone saying "programmers gotta learn hardware too!!!" should get off my lawn. 

### CONCLUSION
It still won't stop whining about a "php memory limit". I don't even know what that means. If php is running out of memory, just please ask the OS for more. Do I have to do everything around here? God.
