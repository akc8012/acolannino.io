---
title: "How I struggled to build a Nextcloud server (and won!)"
date: 2020-06-28T23:36:18-04:00
draft: true
---

### WHY (*am I doing this at all*)?
I really like taking notes. Notes are an extension of my stupid brain, which can't remember a *damn* thing on its own. All these notes were being stored on Google's servers, which [doesn't] [seem like] [the best] [idea].

### The install
Installing everything was shockingly difficult. There can't just be a little `sudo apt install nextcloud` action, no no no no no. You need to install each little bit yourself, by hand, and glue each piece together (`nextcloud` isn't even in the apt repo, of course you have to download / unpack the tarball yourself).

This made some sense as I learned (sorta, vaguely) how Nextcloud works - It's running on a webserver directly on your machine, handling all the networking and whatnot, with a full-on SQL database and lots of PHP magic happening too. So, it's understandable that Nextcloud has to spread it's mischievous tentacles in each crevice of your pure OS install.