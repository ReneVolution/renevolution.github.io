---
author: reneVolution
comments: true
date: 2013-03-16 05:52:26+00:00
layout: post
slug: how-to-install-ffmpeg-on-mac-os-x
title: How to install FFmpeg on Mac OS X
wordpress_id: 52
categories:
- FFmpeg
tags:
- FFmpeg
- Homebrew
- How To
- Mac OS X
- XCode
---

[![Install FFmpeg on OS X](/images/brew_install_ffmpeg.png)]({% post_url 2013-03-16-how-to-install-ffmpeg-on-mac-os-x %})

This post is going to be to show you how to install [FFmpeg](http://www.ffmpeg.org) on Mac OS X as easy as possible. For that, i will use a software called ["Homebrew"](http://mxcl.github.com/homebrew/). It is a linux like package manager with a lot of useful tools easy to install from it. It is quite similar to MacPorts, but in this special case you will get a more recent [FFmpeg](http://www.ffmpeg.org) using [Homebrew](http://mxcl.github.com/homebrew/) than [MacPorts](http://www.macports.org/). Once you are familiar with [Homebrew](http://mxcl.github.com/homebrew/), i am sure you will use it a lot more afterwards if you are not using already.

**Install/Update Xcode**

To be able to use [Homebrew](http://mxcl.github.com/homebrew/) you need the Xcode Command Line Tools. Follow these steps to install it:

1. Open "[Mac App Store](https://itunes.apple.com/de/app/xcode/id497799835?mt=12)" and install Xcode. If you have XCode already installed, update to the latest version available if necesary.

2. After Xcode has been successfully installed, open the Xcode Preferences-Pane.

3. Select the "Downloads"-Tab and click on "Install" next to the "Command Line Tools" entry.


[![XCode Downloads-Pane](http://www.renecalles.de/wp-content/uploads/2013/03/XCode-Downloads-Pane-300x111.png)](http://www.renecalles.de/wp-content/uploads/2013/03/XCode-Downloads-Pane.png)




The time i am writing this Tutorial i have already installed the Xcode Command Line Tools, even if not in the latest version, which i will correct later on my system. But, this is also good for you as you can see what to install if i tell you that on your system will be an "Install"-Button where is an "Update"-Button on the provided screenshot.


**Install Homebrew **

Installing [Homebrew](http://mxcl.github.com/homebrew/) is quite simple. Everything you need to do is to open up a Terminal window, paste and execute the following command and follow the instructions during the installation process.

  `ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

After successful installation you should execute:

brew doctor

This checks if your [Homebrew](http://mxcl.github.com/homebrew/) installation was successful and installation of Formulas (Packages) will work. If you have any trouble please drop me a note in the comments section.

**Install FFmpeg**

Now we are nearly done as all prerequisites are now installed and we can start installing FFmpeg. As there are many options when installing FFmpeg, a command you should know about is brew options <Formula> . This will show you all available options for the formula you are going to install which will be in this case "ffmpeg". So in our case, brew options ffmpeg will print the following information to your screen:


    reneVolution$ brew options ffmpeg

    --with-fdk-aac
    	Enable the Fraunhofer FDK AAC library
    --with-ffplay
    	Enable FFplay media player
    --with-freetype
    	Build with freetype support
    --with-frei0r
    	Build with frei0r support
    --with-libass
    	Enable ASS/SSA subtitle format
    --with-libvo-aacenc
    	Enable VisualOn AAC encoder
    --with-libvorbis
    	Build with libvorbis support
    --with-libvpx
    	Build with libvpx support
    --with-opencore-amr
    	Build with opencore-amr support
    --with-openjpeg
    	Enable JPEG 2000 image format
    --with-opus
    	Build with opus support
    --with-rtmpdump
    	Enable RTMP protocol
    --with-schroedinger
    	Enable Dirac video format
    --with-speex
    	Build with speex support
    --with-theora
    	Build with theora support
    --with-tools
    	Enable additional FFmpeg tools
    --without-faac
    	Build without faac support
    --without-lame
    	Disable MP3 encoder
    --without-x264
    	Disable H.264 encoder
    --without-xvid
    	Disable Xvid MPEG-4 video encoder


To finally install FFmpeg on your system you should follow these steps:

1. Check if your [Homebrew](http://mxcl.github.com/homebrew/) installation is up to date and working with brew doctor

2. Check all available options for ffmpeg with brew options ffmpeg

3. Install ffmpeg with all desired options with brew install ffmpeg [all your options]

Example:

To install FFmpeg with all available options without disabling anything execute:


    brew install ffmpeg --with-fdk-aac --with-ffplay --with-freetype --with-frei0r --with-libass --with-libvo-aacenc --with-libvorbis --with-libvpx --with-opencore-amr --with-openjpeg --with-opus --with-rtmpdump --with-schroedinger --with-speex --with-theora --with-tools


If you are running into any troubles during installation please leave a message in the comments section.

Afterwards FFmpeg should be installed and you can start enjoy to use it.

If you prefer to work with FFmpeg on your Windows machine, read my article [How to get the latest FFmpeg binaries for Windows](http://www.renevolution.com/how-to-get-ffmpeg-for-windows/).
