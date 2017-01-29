---
layout: post
published: true
author: Joshua Mason
date: '2015-10-28'
comments: true
title: Android MediaPlayer – A brief introduction
category:
  - Android
---
Recently my boss approached me to say that one of our clients wanted a custom made audio player app creating. This is something I have never touched on before, and my original thoughts on the matter were along the lines of “Oh sugar…”. But it turns out that Android has an incredibly easy to use MediaPlayer class. So the basics of what you need to know to get started:

To create an instance of the `MediaPlayer` class, ready to play a track you can use

```java
MediaPlayer player = MediaPlayer.create(context, R.raw.sound_file_1);
```

This is assuming that you’re trying to load a file placed in your apps raw resources folder. The context just needs to be any valid context object. From this, to play the file all you need to do is call `start()`. A few of the most basic commands you might want to use include:

```java
player.start();
int currentPosition = player.getCurrentPosition();
player.seekTo(currentPosition + 1000);
player.seekTo(currentPosition - 1000);
player.pause();
player.stop();
```

`getCurrentPosition()` obtains the current position on the current track in milliseconds. `seekTo()` takes an argument in milliseconds of where to jump to in the track. Hence, `seekTo(currentPosition + 1000)` will jump 1 second forward (fast forward) in the track, and the opposite will jump back (rewind) 1 second.
`player.stop()` will stop the current track. If you call `start()` after `stop()` has been called you will get an error.

In a later post I will be showing a little more detail on how to use this class, and some ways to make managing media with it easier.
