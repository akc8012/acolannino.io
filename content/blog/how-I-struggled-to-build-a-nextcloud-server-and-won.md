---
title: "How I struggled to build a Nextcloud server (and won!)"
date: 2020-06-28T23:36:18-04:00
draft: true
---

### Why am I doing this to myself?
I figured, if *I* have to struggle, I may as well invite others onto the struggle-bus as well.

I really like taking notes. Notes are an extension of my stupid brain, which can't remember a *damn* thing on its own. All these notes were being stored on Google's servers, which [doesn't](https://en.wikipedia.org/wiki/PRISM_(surveillance_program)) [seem like](https://www.gnu.org/proprietary/malware-google.en.html) [the best](https://www.washingtonpost.com/technology/2019/06/21/google-chrome-has-become-surveillance-software-its-time-switch/) [idea](https://www.eff.org/deeplinks/2020/03/google-says-it-doesnt-sell-your-data-heres-how-company-shares-monetizes-and).

This isn't so much a guide or tutorial - more just me explaining the massive effort it took to set this damn thing up. I hope somebody someday learns something from my suffering, or is maybe just entertained.

### The hardware
I had been interested in doing *something, anything at all*, with a [Raspberry Pi](https://www.raspberrypi.org/) for a while, so this was my excuse. Beyond that, I just followed [this great article from a Pi magazine](https://magpi.raspberrypi.org/articles/build-a-raspberry-pi-nas) for my hardware choices. If you're wondering what hardware I used, look there. I copied it exactly. Plus, c'mon, look how cute everything looks stacked up like that! A literal "stack"! Ha!

One part the guide doesn't explain very well was the "USB powered hub" - both why you need one, and what that actually is. Is it a hub powered by USB? A USB powered by a "hub"? What is a "hub"? Maybe it seems obvious to you, and maybe I was just sleep deprived at the time, but I had trouble wrapping my smooth brain around this concept. Turns out, the USB hub is simply needed to provide power to the two hard drives, rather than the power going to the Pi *and* the drives. I have no idea if this really is necessary, but it makes me feel 10% more confident my drives won't crap out at any moment, and that helps me go to sleep.

### RAID 1, or whatever that means
Here I was, all ready to go in fulfilling my long-held dream of running my own little server. Then my stupid coworker comes in, and asks "hey, what if your drive fails? what will you do then?" and ruins all of my fun. 

He tells me I should do "RAID", which is apparently all the rage. RAID stands for "Redundant, Awesome... I dunno", and was invented on a whim by [some random nerds in the 80's](https://en.wikipedia.org/wiki/RAID#History). To attempt to give an actual explanation: Using a RAID 1 setup gives me disk redundancy by constantly mirroring each drive. If one drive craps out, the other drive still has all the same data, so you just replace the other drive and go about your day as normal. The downside of RAID 1 is you're getting half the storage capacity as you paid for, but I figured 1 terabyte was large enough to store plenty of memes.

This was by far the most pain-free part of the process. It was the only pain-free part of the process, actually, the rest was pure suffering. I recommend doing this for fun if you're bored on a Friday evening. It's cathartic, and the only part of this process that [just worked](https://www.youtube.com/watch?v=nVqcxarP9J4).

All I had to do was run some cute little commands from [this tutorial], and I was golden. I don't fully understand the intricacies of everything I was doing, and the command-line interfaces for some of these programs were absolutely wild (press w to write my drive ___? Really?), it was all smooth sailing.

I bet it's something that could even 

### The installation
Installing everything was shockingly difficult. There can't just be a little `sudo apt install nextcloud` action, no no no no no. You need to install each little bit yourself, by hand, and glue each piece together (`nextcloud` isn't even in the apt repo, of course you have to download / unpack something called a "tarball" yourself).

#### Attempt 1: Snap!
[Snap](https://snapcraft.io/) is Canonical's (maker of Ubuntu) locked-down little sandbox for Linux apps. The word "container" is thrown around when describing it, and I have no idea if that's true, but I sure as heck wouldn't recommend the [official Nextcloud snap](https://snapcraft.io/nextcloud).

The major selling point of snap is that it bundles all the dependencies of an application, so it can *just work* on any distro. This sounds great! Sign me up! I'm lazy and hate installing my own dependencies! Who the heck wants to do that? Shell scripts, that's who. Problem is, this doesn't really work on every distro. In fact, it doesn't work on the latest Raspberry Pi OS. Do I know why? No. The Nextcloud snap [failed silently](https://en.wikipedia.org/wiki/Fail-silent_system) before it could startup, and it's too shy to tell me why. Cool.

#### Attempt 2: Some shell scripts I found
At this stage, I was still committed to being a lazy jerk. There's no way in heck I would manually install [30-something php modules](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#prerequisites-for-manual-installation) by hand, I simply refused. So, I found a [flashy looking site that claimed to have the scripts for me](https://ownyourbits.com/nextcloudpi/). It didn't work. The script took multiple runs to actually complete itself, and after the 5th or so attempt, it seemed happy. I went to the web GUI, told it to "initialize", and it kinda hung out there for a while. I went to take a walk and come back and it... [screenshot]

#### Attempt 3: The hard way
This made some sense as I learned (sorta, vaguely) how Nextcloud works - It's running on a webserver directly on your machine, handling all the networking and whatnot, with a full-on SQL database and lots of PHP magic happening too. So, it's understandable that Nextcloud has to spread it's mischievous tentacles in each crevice of your pure OS install.

I followed the [Nextcloud documentation](https://docs.nextcloud.com/server/latest/admin_manual/index.html), which sure does exist. In their defense, all of their software is [free and open](https://en.wikipedia.org/wiki/Free_and_open-source_software), including the docs, so I could have submitted any number of changes, and yet here I am selfishly writing this blog.

### The WiFi versus pixels battle of 2020
So here I am, all ___ and happy with my brand new Raspberry Pi running a fresh ~~Raspbian~~ Raspberry Pi OS. As I'm setting everything up (and, for some reason, using its surprisingly not bad lightweight version of Chromium), the WiFi starts cutting in-and-out. This has been a persistent problem ever since I switched my main devices (personal desktop and laptop) to Linux, so I figured this was the same / similar problem as the [mysterious Intel WiFi+bluetooth death bug plaguing Linux for years, apparently].

I do some more digging, and find what I believe to be the truth (or, as close to any of us mere mortals will ever get to a truth). There appears to be a [widely reported problem with the Pi 4](https://www.raspberrypi.org/forums/viewtopic.php?t=247982) where the signals coming out from the HDMI (which are shaped like squares?) are the same frequency(?) as the WiFi. So, if your display resolution is pumped up high enough, and that HDMI is cranking out lots of square signals, [the WiFi gets totally borked](https://www.raspberrypi.org/forums/viewtopic.php?p=1514642&sid=b811be4b798c7ab50d7626c691b5cc26#p1514642). Neat.

This is clearly absurd, and I hate it. Hardware is bad, and everyone saying "programmers gotta learn hardware too!!!" should get off my lawn. At first I started following the internet's advice of simply "lower your screen resolution so your wifi goes fast", but this became tiring on the eyes (especially since you [can't run a blue light filter like redshift on the Pi]).

Even though I was reluctant to it at first, eventually I started controlling my Pi via an SSH terminal from my other machines. Boy oh boy, was this a joyful discovery. No longer was I stuck to whatever stupid resolution the wifi demanded, but I could also use my favorite blue light filter to prevent my retinas from burning up. Sure, I had no GUI, but learning to do everything through the terminal came easily enough, and once I got there, I felt like some kind of computer wizard.

### Conclusion
All in all, I sure did have a time. The admin page still won't stop whining about a "PHP memory limit". I don't even know what that means. If PHP is running out of memory, I wish it would just ask the OS for more. Really I don't mind, I've got plenty. For most things I find baffling, I think to myself "hey, they probably had a good reason for doing it this way", but as I read more about the [haphazard history of PHP](https://en.wikipedia.org/wiki/PHP#Early_history), I decided to change my mind. *"I have absolutely no idea how to write a programming language"*, said the writer of the PHP programming language.

Maybe my takeaway from all this is that nobody knows how to do anything. I certainly still don't, but at least I now have a functioning home server with several gigabytes of memes loaded on.

Also, if you're new to Linux / bash, I'm not sure I'd recommend this kind of endeavour. I had been using Linux on my main machines for the better part of a year, and have gotten sorta okay at using the terminal. Linux makes me smile, and plopping into an SSH terminal and clacking away at the keyboard brings me joy, but it might not do the same for you. I dunno. 
