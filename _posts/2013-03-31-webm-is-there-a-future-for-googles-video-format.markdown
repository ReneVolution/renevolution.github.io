---
author: reneVolution
comments: true
date: 2013-03-31 10:19:42+00:00
layout: post
slug: webm-is-there-a-future-for-googles-video-format
title: 'Webm: Is there a future for Google''s video format?'
wordpress_id: 158
categories:
- General
- webm
tags:
- MPEG DASH
- streaming
- VP8
- VP9
- webm
---

[![Webm logo](/images/WebM_logo_mids.png)]({% post_url 2013-03-31-webm-is-there-a-future-for-googles-video-format %})


If you are working in the video business you would of course have heard about Webm and the VP8 codec as a competitor to H.264. In fact there was no chance to beat H.264. Not yet. In todays article i'll share my thoughts about Webm and the VP8 and VP9 codecs


## What is Webm?


[Webm](http://en.wikipedia.org/wiki/WebM) is a video container format, designed for video streaming in HTML5 . It consists (actually) support for VP8 video and Vorbis audio streams and is based on a profile of Matroska, also known as "MKV". Google is sponsoring the development and grants every user a roaylty-free usage. The next generation video codec will be VP9 and is intended to be the competitor of the HEVC (H.265) codec.


## The VP8 codec


Google owned the [VP8](http://en.wikipedia.org/wiki/VP8) codec from On2 Technologies, which were mostly known for their video codecs in Flash-video for approx. 126 million US-Dollar. Not enough, Google decided to release the specification for this format under the [Creative Commons Attribution 3.0 license](http://www.creativecommons.org/). Badly the codec couldn't compete H.264 for many reasons. The biggest one was a slightly better video compression quality in H.264 videos. Also there was no big acception in the industry for VP8 as H.264 was long proven and without any benefit in e.g. quality, why should they implement a new format?


## Legal issues


As VP8 is using patent techniques from 11 patent holders the [MPEG LA](http://www.mpegla.com/) intended to form a patent pool of companies for it. Last month Google and MPEG LA agreed on a royalty free usage for all users. Not enough, this also includes the next generation video codec VP9. With this commitment we now have, unless Google wants us to pay for it, a completely royalty free video codec, free to use for everyone. This is in fact great news as no one knows how H.264 / H.265 license fees will be charged in the future, even if H.264 usage is actually free.


## The Future: VP9


At the time writing this article the development of the [VP9 video codec](http://en.wikipedia.org/wiki/VP9) is in progress. One of the goals is to achieve 50% better quality with the same bitrate compared to VP8. Another goal is of course to provide a better encoding efficiency than H.265 which has the same approach on achieving a better quality around 50% compared to H.264. There are already VP9 videos circulating on the web and there is also already an integration for VP9 decoding in the [development versions of Google's Chrome](http://www.chromium.org/getting-involved/dev-channel). Actually it is no fun to create VP9 video using the experimental branch of libvpx as, with every reference encoder, the encoding takes days until it finishes. Anyway i will try to provide a sample in the near future also showing you how to install and set up Google Chrome.


## About MPEG DASH


There are actually 3 main adaptive streaming technologies on the market. Everyone specialized for a specific set of devices. To summarize there is [Apple's HTTP Live Streaming (HLS)](https://developer.apple.com/resources/http-streaming/) for Apple/iOS devices, [Microsoft's Smooth Streaming](http://www.iis.net/downloads/microsoft/smooth-streaming) for all Windows devices and [Adobe's HTTP Dynamic Streaming (HDS)](http://www.adobe.com/de/products/hds-dynamic-streaming.html) for all Flash enabled devices. So, why should we need another streaming format? Well, at least there are at minimum two options: 1) To create a universal streaming format for all devices or 2) To share royalties in another patent pool. As i'm trusting in the goodness of the people i'll pick option 1. And here we are, introducing MPEG DASH which stands for Dynamic Adaptive Streaming over HTTP. It combines all streaming technology approaches of HLS, HDS and Smooth Streaming and added some new ones which i will also discuss on another article as it would go beyond of the scope of this article. The official intention of MPEG DASH is to provide a universal streaming technology for all clients. Of course this can only work if it will be integrated in all clients.

What has this to do with Webm you ask? Actually nothing as Webm isn't even mentioned in the actual spec, but there is already development going on to create MPEG DASH streams with Webm content. The library called [DASH-JS](http://www-itec.uni-klu.ac.at/dash/?page_id=746) and the [University of Klagenfurt](http://www-itec.uni-klu.ac.at/dash/) also provide instructions and tools to create Webm MPEG DASH streams and play the using Google Chrome. Maybe we'll see Webm in the next iteration of the MPEG DASH specification which leads me to my conclusion.


## Conclusion


As my friend Rocky Balboa would say: "It's not over til' it's over". That said, there might be a small chance for Google's Webm format in the future under some circumstances, at least for the major video market. If they achieve their goal for the VP9 video codec in being more efficient than H.265 i really see a possibility that it will find it's way to your home.  But, don't get me wrong, it is just a tiny small chance in my opinion and i know many people, maybe also you, are screaming out "Webm is dead!". We will see in the next couple of months or years where this is going to.

In this spirit, thanks for reading and i would really appreciate if you would share your thoughts with me.
