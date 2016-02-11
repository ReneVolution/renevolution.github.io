---
author: reneVolution
comments: true
date: 2013-05-02 20:15:04+00:00
layout: post
slug: understanding-ffmpeg-part-ii-scaling-video
title: 'Understanding FFmpeg - Part II: Scaling video'
wordpress_id: 285
categories:
- FFmpeg
tags:
- FFmpeg
- filter
- How To
- png
- resize
- scale
- streaming
- video
---

[![FFmpeg-Logo.svg](http://www.renevolution.com/wp-content/uploads/2013/03/FFmpeg-Logo.svg_.png)](http://www.renevolution.com/wp-content/uploads/2013/03/FFmpeg-Logo.svg_.png)

Most of the time you're encoding video with [FFmpeg](http://www.ffmpeg.org) you'll want to scale your video to fit your needs for a specific player configuration or just because you can :-). Seriously, when you're creating content for e.g. Adaptive Streaming you'll want to lower the video resolution as you create lower bitrates for tablets or mobiles.

To keep the following scaling examples comparable i decided to use the image of second 30 from [Tears of Steel](http://www.renevolution.com/introducing-tears-of-steel/) video. This is done through the parameter -ss 30  in the command line. I also convert the frames into png files using -vframes 1  option and defining png encoding with just using the output file extension png.


## The Scaling filter


To use the scaling filter you need to make use of the -vf  (videofilter) option in your command line. This signals [FFmpeg](http://www.ffmpeg.org) to prepare the video frames being filtered. Filters in FFmpeg are chainable, but this is a topic we'll dive deeper into in an upcoming article.

The general usage for the scaling filter is:

"scale=w=desired-output-width:h=desired-output-height"

which is equivalent to

"scale=desired-output-width:desired-output-height"

Simple Scaling

As first example i will show you how to scale a given video to a fixed defined resolution of 640x267px using the command line:

    
    ffmpeg -ss 30 -i tears_of_steel_1080p.mov -vf "scale=640:267" -vframes 1 tos_640x267_scale.png


This will result in the following picture:

[
![tos_640x267_scale](http://www.renevolution.com/wp-content/uploads/2013/05/tos_640x267_scale.png)](http://www.renevolution.com/wp-content/uploads/2013/05/tos_640x267_scale.png)



It might be suspicious to you that i chose 640x267px as resolution for this but this is resulting resolution to keep the aspect ratio of the video image. Let's see what happens if we scale the video to  a fixed resolution of 640x360px:

    
    ffmpeg -ss 30 -i tears_of_steel_1080p.mov -vf "scale=640:360" -vframes 1 tos_640x360_scale.png


[![tos_640x360_scale](http://www.renevolution.com/wp-content/uploads/2013/05/tos_640x360_scale.png)](http://www.renevolution.com/wp-content/uploads/2013/05/tos_640x360_scale.png)



Ok, this looks really bad and even if the actors may like seeing them that slim, it actually looks more like a remake of the "[Coneheads](http://www.imdb.com/title/tt0106598/)"-Movie in 1993 :-).

Back on topic, there will be scenarios where you don't know about the correct resolution for your output video and you may just want to define the maximum width or height. For those scenarios ffmpeg introduced an automatic way to keep the aspect ratio by just defining width or height and set the opposite to -1.

    
    ffmpeg -ss 30 -i tears_of_steel_1080p.mov -vf "scale=640:-1" -vframes 1 tos_640x-1_scale.png


and

    
    ffmpeg -ss 30 -i tears_of_steel_1080p.mov -vf "scale=-1:267" -vframes 1 tos_-1x267_scale.png


will result with the same resolution (+/- 1px) as the first picture.


## Advanced Scaling




### Stop upscaling


If you want to batch process your set of videos you might consider to use regular expressions. Those are extremely powerful and i can only advise you to use them if you don't know what kind of input resolutions to expect.

The following example will prevent you from upscaling your videos to a higher width as the input video provides and a maximum width of 640px:

    
    ffmpeg -ss 30 -i tears_of_steel_1080p.mov -vf "scale='min(iw,640)':-1" -vframes 1 tos_no_upscaling.png


In this example i use the _iw_ variable which holds the analyzed input width of the video and the _min()_ function which compares the input width with 640 and applies the lower one to the filter. So, for an input resolution of 1280x720px the output resolution will be 640x360px and for an input resolution of 320x180px the output resolution will stay 320x180px.


###  Half size


With regular expression you can also scale your image to e.g a half size video with the following command line:

    
    ffmpeg -ss 30 -i tears_of_steel_1080p.mov -vf "scale='iw/2':-1" -vframes 1 tos_half_size.png


You can easily modify this example to e.g. create quarter sized video and of course you can also apply those regular expressions to the height. Just try it out.


