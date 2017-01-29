---
layout: post
published: true
author: Joshua Mason
date: '2016-01-15'
comments: true
title: Google Play Game Services – Error 10002 (RESULT_SIGN_IN_FAILED)
category:
  - Android
---
One of the newest apps I recently worked on required the use of Google Play Game Services. There’s a lot of material from Google out there on how to set this all up and get it working, and in all honesty the code is all very simple. Just one problem.

After hours of trying, I could not get game services to work correctly and sign in. I had everything set up as described in the documentation, but it just wouldn’t work. After hours of googling, I finally ran across a one line throwaway comment that finally pointed me in the right direction.

[Here is the documentation](https://developers.google.com/games/services/console/enabling#step_2_add_your_game_to_the_dev_console) I used to setup everything in the Play Console. The one thing I unfortunately didn’t realise was that if you created the API Console Project using google’s old style console, even if you’re using the project on the new site, it will not work.

So, that said, the easiest fix was simply to remove the project from the game console and create a completely new one. You can do this by using the option entitled “I don’t use any Google APIs in my game yet”, which comes up after you click to add a new game.

Hopefully this will save someone a little bit of time!
