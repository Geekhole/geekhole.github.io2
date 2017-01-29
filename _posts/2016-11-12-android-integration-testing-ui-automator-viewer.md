---
layout: post
published: true
author: Joshua Mason
date: '2015-09-30'
comments: true
title: Android Integration Testing – UI Automator Viewer
category:
  - Android
---
There’s not too much to say on this one, but just because there isn’t much to say doesn’t mean it’s not an amazing piece of software! Free, and included with the Android SDK, the UI Automator Viewer is incredibly useful when writing automated tests, with Espresso or any other testing framework that requires some way of identifying views to interact with. I found information on this little gem whilst searching for best practices when writing tests using Espresso, however the information contained in this article is actually more to do with testing interactions between apps, something which is difficult (if not impossible) to do with Espresso. The link to the article in question is [here](https://developer.android.com/training/testing/ui-testing/uiautomator-testing.html).

The UI Automator Viewer allows you to connect a device or simulator to your  computer and then obtain a snapshot of the XML view hierarchy, including information on the resource id and all other manner of properties a view can have. The one possible downside is that it doesn’t work with custom views, instead showing the custom view as a whole, it will show the individual views within the custom view. i.e. if you have a custom view that extends an `ImageView`, and which contains a `TextView` and `ImageButton` it will show the top level item as an `ImageView`, with child items as a `TextView` and `ImageButton`. It’s not too much of a downside really…

So,  if you haven’t looked at the link I posted above, the way to access this great application once you have the Android SDK is to look within the sdk/tools folder. Under this there should be a file named ‘uiautomatorviewer’. Open this, and away you go!
