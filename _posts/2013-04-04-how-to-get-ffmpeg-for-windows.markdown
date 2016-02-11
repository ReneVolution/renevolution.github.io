---
author: reneVolution
comments: true
date: 2013-04-04 20:55:27+00:00
layout: post
slug: how-to-get-ffmpeg-for-windows
title: How to get the latest FFmpeg binaries for Windows
wordpress_id: 244
categories:
- FFmpeg
tags:
- codecs
- command line
- FFmpeg
- Windows
- x264
---

[![FFmpeg-Logo.svg](http://www.renevolution.com/wp-content/uploads/2013/03/FFmpeg-Logo.svg_.png)](http://www.renevolution.com/wp-content/uploads/2013/03/FFmpeg-Logo.svg_.png)


Last time i guided you on [how to install FFmpeg on Mac OS X](http://www.renevolution.com/how-to-install-ffmpeg-on-mac-os-x/). In today's article i will show you a way to get the latest [FFmpeg](http://www.ffmpeg.org) binaries for your Microsoft Windows operating system. Intentionally, when i started this blog i wanted to provide you with FFmpeg builds myself but after a while of thinking about it i decided to not reinvent the wheel on this topic and focus on guiding you how to use it. Anyway, for hands on my tutorials you will need to have a working version of FFmpeg. Badly, compiling FFmpeg for Windows is far from easy and i'm really happy there are already people who took the challenge and share their work with us.


## Get the FFmpeg binaries


So, the great resource i am talking about is [ffmpeg.zeranoe.com](http://ffmpeg.zeranoe.com/builds/). The binaries are available for 32bit and 64bit operating systems containing ffplay.exe, which is basically a command line controlled video player, ffprobe.exe as an analyzer tool with a lot of greate features and of course ffmpeg.exe as the command line encoding tool. If you are just looking for the binaries to use it in your command line, you should download the static build for your operating system. If you're developer you may decide to use the shared libraries or development versions.


## Installation Instructions





	
  1. As the binaries provided by zeranoe are archived using the freely available [7-zip](http://7-zip.org/), you need to download and install it.

	
  2. Download the latest build of FFmpeg from [ffmpeg.zeranoe.com](http://ffmpeg.zeranoe.com/builds/).

	
  3. Unpack your downloaded version. You will find the binaries in the folder /bin.


That's essentially it but i recommend to either put the path to your binaries into your System PATH variables or move the the binaries to somewhere which is already in your PATH. Of course you could also move the binaries to e.g. C:\Tools\bin  and launch FFmpeg with C:\Tools\bin\ffmpeg.exe , that's up to you.

For all you guys who are waiting for the next part of "Understanding FFmpeg", i promise the next article will continue with that series. See you then.
