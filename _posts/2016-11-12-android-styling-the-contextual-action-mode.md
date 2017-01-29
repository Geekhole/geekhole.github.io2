---
layout: post
published: true
author: Joshua Mason
date: '2015-12-02'
comments: true
title: Android – Styling the Contextual Action Mode
category:
  - Android
---
I recently found myself needing to use the [Contextual Action Mode](http://developer.android.com/guide/topics/ui/menus.html#CAB) functionality of Android to make things look a little more “Androidy” (I was cloning an iOS app, at a customers behest.). All went well, except for one really annoying little UI problem. The left action button was slightly off in relation to to the hamburger menu button. To fix this I needed some way of changing the padding if this item, but alas, no easy way exists of doing this. Well, I say that, but after a little bit of work it turns out it’s not that hard after all.

The general idea of what I am about to describe can probably be used in other places to style android build in components where you aren’t given direct control.

So, without further ado, I will explain how to change the padding on the left action button.

First using the [UIAutomator tool in the Android SDK](https://geekhole.github.io/android/2015/09/30/android-integration-testing-ui-automator-viewer/) we can find the resource ID of all the items on the context menu. So, once you’ve implemented the Contextual Action Mode, get it up on the screen and use the tool, as described in the above link to obtain the ID. In my case the ID is R.id.action_mode_close_button.

The next step is to get an actual reference to this view. This is easy; if you are within an activity you can simply use

```java
findViewById(R.id.action_mode_close_button);
```

or, if you are within a fragment

```java
getActivity().findViewById(R.id.action_mode_close_button);
```

From there, you can enact anything on the view that you normally would. As I said, I wished to change the padding so all in all my single line of code looked similar to this:

```java
getActivity().findViewById(R.id.action_mode_close_button).setPadding(50, 0, 50, 0);
```

So there you have it, now you can find and manipulate any view within Android that you can find!
