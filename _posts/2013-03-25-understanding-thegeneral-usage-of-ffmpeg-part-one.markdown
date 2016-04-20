---
author: reneVolution
comments: true
date: 2013-03-25 19:31:17+00:00
layout: post
slug: understanding-thegeneral-usage-of-ffmpeg-part-one
title: 'Understanding FFmpeg - Part I: General usage'
wordpress_id: 136
categories:
- FFmpeg
tags:
- codecs
- command line
- encoding
- FFmpeg
- x264
---

[![Big Buck Bunny - a classic demo video](/images/rinkysplash.jpg)]({% post_url 2013-03-25-understanding-thegeneral-usage-of-ffmpeg-part-one %})


At the time people start audio/video conversion with [FFmpeg](http://www.ffmpeg.org), most people have to google a lot to find out how to use it in an appropriate way. Most of the time users search for specific use cases which is ok if you only need to use it for a single use case. This blog will also point you to specific use cases e.g. about watermarking, encoding into different file formats and codecs etc. However, this blog post will show you FFmpeg works in an general, more abstract way which will help you using it in different scenarios. As this will become a bit complex and i focus on readability, i will start very simple and base on that during the further explanation.


## The very simplest usage

{% highlight text %}
ffmpeg -i [INPUTFILE] [OUTPUTFILE]
{% endhighlight %}


e.g. {% ihighlight text %}ffmpeg -i MyMovie.mp4 MyMovie.avi{% endihighlight %} will convert your MP4 video to AVI. Of course this is not very useful as you haven't specified anything for your output like resolution, codec, bitrate etc., but i will use this command as a starting point for further explanations.


## Specifiying the Codecs


Audio and video codecs define the compression algorithms to encode the audio or video with. FFmpeg can deal with a lot of codecs which you can check for availability with ffmpeg -codecs . It will show you all installed codecs and define also if they are avaialable for decoding, encoding or both. Here is where to define the codec in your command line:

{% highlight text %}
... [INPUTFILE] -c:v [VIDEOCODEC] [CODEC-OPTIONS] -c:a [AUDIOCODEC] [CODEC-OPTIONS] [OUTPUTFILE]
{% endhighlight %}

So, for example to create a H.264 Video with AAC Audio the full command line would look like this:

{% highlight text %}
ffmpeg -i MyFile.avi -c:v libx264 -preset slow -c:a libfdk_aac MyFile.mp4
{% endhighlight %}

Let's go through the new arguments in our command line:

**{% raw %}-c:(v\|a){% endraw %}** is a selector for different types of codecs. **v** is the selector for video and **a** for audio

**[VIDEOCODEC]:**  is the video codec to use. In my example libx264 which will encode to H.264 video.

**[AUDIOCODEC]:** defines respectively the audio codec for encoding. In the example i used libfdk_aac to encode to AAC audio.

**[CODEC-OPTIONS]:** Every codec comes with a bunch of options. You should ever define right next to the specific codec. For video i am just using a preset provided by the X264 developers and for audio i didn't choose any, so FFmpeg will use the default options.

This was just a brief overview and we just touched the surface of what FFmpeg is capable of. Actually i don't know how many parts this upcoming series will have. I'm thinking about around five and then i will go over to some specific and/or fun things you can do with FFmpeg. The next Topic will show you how to crop, scale & letter-/pillarbox your movies.

See you there...
