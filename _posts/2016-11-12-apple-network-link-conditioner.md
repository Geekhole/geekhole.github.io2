---
layout: post
published: true
author: Joshua Mason
date: '2015-09-17'
comments: true
title: Apple Network Link Conditioner
category:
  - Development
subtitle: ''
modified: ''
tags: ''
---
As a mobile application programmer one thing that I often find myself needing to do is test apps on bad network connections. If you’ve ever created an app that uses the internet to download anything at all, you will probably understand the annoyances of trying to work out what exactly will happen if you end up with an incredibly bad connection. And of course, since the apps are run on mobile devices, you could end up with a bad internet connection at any point whilst out an about.

On iOS devices there is luckily built in functionality to simulate bad network connections, which can be found in the developer options under settings. However there is nothing quite so helpful on Android. This is where the Apple Network Link Conditioner comes in. It is important to note at this point that unfortunately if you are developing from a windows machine this is probably not going to help you, as this piece of software is only available on Apple Macs, due to it being an extension of the XCode tools used to develop iOS and OS X apps.

That being said, if you own a Mac then the Network Link Condition is an excellent tool for use in development. It is contained within the Hardware IO Tools for XCode which can be downloaded from [here](https://developer.apple.com/downloads/). You’ll need an Apple Developer account to access these tools, but you should be able to sign up for free.

Once you have downloaded the package, open it up and you will see an icon named `NetworkLinkConditioner.prefPane`. Opening this will install a new application into your settings allowing you to control your network connection.

The next step to be able to work with this on your android device (assuming you are not using the simulator, in which case you’re all set to go), is to turn on WiFi sharing. In order to do this you will need to have your Mac connected to an Ethernet source. You can turn on WiFi sharing in Settings > Sharing and selecting Internet Sharing. After you have your internet shared, connect your android device to your new WiFi source and you’re ready to start testing with different internet connection types!
