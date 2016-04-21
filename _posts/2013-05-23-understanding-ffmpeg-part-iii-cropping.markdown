---
author: reneVolution
comments: true
date: 2013-05-23 20:34:44+00:00
layout: post
slug: understanding-ffmpeg-part-iii-cropping
title: 'Understanding FFmpeg - Part III: Cropping'
wordpress_id: 321
categories:
- FFmpeg
tags:
- command line
- crop
- cropdetect
- encoding
- FFmpeg
- ffplay
- filter
---

[![About cropping](/images/crop_banner.jpg)]({% post_url 2013-05-23-understanding-ffmpeg-part-iii-cropping %})



If you've ever been in a situation where your recorded video had a blank interval or you just want to get a specific part of your video you'll definitely want to crop your video. In this article i'll show you how to do this with [FFmpeg](http://www.ffmpeg.org).


## Example video


[![crop_example](/images/crop_example-600x337.png)]({{ post.url }})



Ok, before you leave the keyboard and stop reading .. you will not need a ruler to fix this. Let's have look how we can do it the easy way using [FFmpeg](http://www.ffmpeg.org).

Get the cropping values

At first we need to find out the necessary values for the cropping filter. This can be done by FFplay using the cropdetect filter. This can be done using the command line {% highlight text %}ffplay -i YourMovie.mp4 -vf "cropdetect=24:16:0"{% endhighlight %} or using FFmpeg with a command line like {% highlight text %}ffmpeg -i YourMovie.mp4 -vf "cropdetect=24:16:0" dummy.avi{% endhighlight %}.

The cropdetect filter is configured with the arguments **cropdetect=limit:round:reset** with the following meaning:

**limit** = The threshold of the intensity of the black bar. You can play around with that, it worked mostly well for me with the default value 24

**round** = Ensures the output resolution is divisible by the value specified. 16 is best for most video codecs.

**reset** = Determines after how many frames cropdetect will reset the previously detected largest video area and start over to detect the current optimal crop area. This is especially useful when tv logos interrupt the video.

To output in your shell will look like this:

{% highlight bash %}
[Parsed_cropdetect_0 @ 0x7fe4f14127c0] x1:0 x2:639 y1:29 y2:295 w:640 h:256 x:0 y:36 pos:1426828 pts:636 t:26.500000 crop=640:256:0:36
[Parsed_cropdetect_0 @ 0x7fe4f14127c0] x1:0 x2:639 y1:29 y2:295 w:640 h:256 x:0 y:36 pos:1428008 pts:637 t:26.541667 crop=640:256:0:36
{% endhighlight %}

What's that ? Right, the last part on every line with "_**crop=...**_" are our cropping values to remove all black bars around our movie.


## Crop it like it's hot


Now it's time to remove those annoying black bars around this movie using

{% highlight bash %}  
ffmpeg -i YourMovie.mp4 -vf "crop=640:256:0:36" YourCroppedMovie.mp4
{% endhighlight %}


which will result in the expected output like this:

[![cropped](/images/cropped-600x240.png)]({{ post.url }})


To finally explain the parameters used with the crop filter in a more general way, here we go:

The crop filter takes four arguments crop=out_width:out_height:x:y  and can be explained as

**out_width/output_height** represents the cropped output width of the video.

**x/y** is the start coordinate from the top left corner.

In my example the cropped output width is 640px and the output height is 256px in total, starting from (0,36) coordinate.


## Cropping with fixed values


Another approach is to crop your video to a fixed area. This can be done using regular expressions inside the crop filter configuration.

For e.g. to crop your video 32px on left/right and 16px on top/bottom use this configuration crop=iw-64:ih-32:32:16. The parameter **iw-64** is the cropped output width calculated by the input width - 64px as we wanted to crop 32px from each side. The same is done for the output height with **ih-32** which results in the calculated cropped output height - 32px -> 16px each top and bottom. The starting coordinates are **x** = 32 and **y** = 16.

I hope i could show you how useful and powerful cropping is and you enjoyed reading. Try it and have fun...
