---
title: "How I struggled to build a Nextcloud server (and won!)"
date: 2020-06-28T23:36:18-04:00
draft: true
---

### Why (am I going through with all of this)?
I figured, if *I* have to struggle, I may as well invite others onto the struggle-bus as well.

I really like taking notes. Notes are an extension of my stupid brain, which can't remember a *damn* thing on its own. All these notes were being stored on Google's servers, which [doesn't](https://en.wikipedia.org/wiki/PRISM_(surveillance_program)) [seem like](https://www.gnu.org/proprietary/malware-google.en.html) [the best](https://www.washingtonpost.com/technology/2019/06/21/google-chrome-has-become-surveillance-software-its-time-switch/) [idea](https://www.eff.org/deeplinks/2020/03/google-says-it-doesnt-sell-your-data-heres-how-company-shares-monetizes-and).

This isn't so much a guide or tutorial - more just me explaining the massive effort it took to set this damn thing up. I hope somebody someday learns something from my suffering, or is maybe just entertained.

### RAID 1, or whatever that means
Here I was, all ready to go in fulfilling my long-held dream of running my own little server. Then my stupid coworker comes in, and asks "hey, what if your drive fails? what will you do then?" and ruins all of my fun. 

He tells me I should do "RAID", which is apparently all the rage. RAID stands for "Redundant, Awesome... I dunno", and was invented on a whim by [some college kids in the 80's](https://en.wikipedia.org/wiki/RAID#History).

This was by far the most pain-free part of the process (the only one). I recommend doing this for fun if you're bored on a Friday evening. It's cathardic, and the only part of this process that [just worked](https://www.youtube.com/watch?v=nVqcxarP9J4).

### The installation
Installing everything was shockingly difficult. There can't just be a little `sudo apt install nextcloud` action, no no no no no. You need to install each little bit yourself, by hand, and glue each piece together (`nextcloud` isn't even in the apt repo, of course you have to download / unpack something called a *"tarball"* yourself).

This made some sense as I learned (sorta, vaguely) how Nextcloud works - It's running on a webserver directly on your machine, handling all the networking and whatnot, with a full-on SQL database and lots of PHP magic happening too. So, it's understandable that Nextcloud has to spread it's mischievous tentacles in each crevice of your pure OS install.

I followed the [Nextcloud documentation](https://docs.nextcloud.com/server/latest/admin_manual/index.html), which sure does exist. In their defense, all of their software is [free and open](https://en.wikipedia.org/wiki/Free_and_open-source_software), including the docs, so I could have submitted any number of changes, and yet here I am selfishly writing this blog.

### The WiFi versus pixels battle of 2020
So here I am, all ___ and happy with my brand new Raspberry Pi running a fresh ~~Raspbian~~ Raspberry Pi OS. As I'm setting everything up (and, for some reason, using its surprisingly not bad lightweight version of Chromium), the WiFi starts cutting in-and-out. This has been a persistent problem ever since I switched my main devices (personal desktop and laptop) to Linux, so I figured this was the same / similar problem as the [mysterious Intel WiFi+bluetooth death bug plaguing Linux for years, apparently].

I do some more digging, and find what I believe to be the truth (or, as close to any of us mere mortals will ever get to a truth). There appears to be a [widely reported problem with the Pi 4](https://www.raspberrypi.org/forums/viewtopic.php?t=247982) where the signals coming out from the HDMI (which are shaped like squares?) are the same frequency(?) as the WiFi. So, if your display resolution is pumped up high enough, and that HDMI is cranking out lots of square signals, [the WiFi gets totally borked](https://www.raspberrypi.org/forums/viewtopic.php?p=1514642&sid=b811be4b798c7ab50d7626c691b5cc26#p1514642). Neat.

This is clearly absurd, and I hate it. Hardware is bad, and everyone saying "programmers gotta learn hardware too!!!" should get off my lawn. 

### Conclusion
All in all, I sure did have a time. The admin page still won't stop whining about a "PHP memory limit". I don't even know what that means. If PHP is running out of memory, I wish it would just ask the OS for more. Really I don't mind, I've got plenty. For most things I find baffling, I think to myself "hey, they probably had a good reason for doing it this way", but as I read more about the [haphazard history of PHP](https://en.wikipedia.org/wiki/PHP#Early_history), I decided to change my mind. *"I have absolutely no idea how to write a programming language"*, said the writer of the PHP programming language.

Maybe my takeaway from all this is that nobody knows how to do anything. I certainly still don't, but at least I now have a functioning home server with several gigabytes of memes loaded on.
