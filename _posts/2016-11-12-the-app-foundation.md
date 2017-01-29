---
layout: post
published: true
author: Joshua Mason
date: '2016-08-10'
comments: true
title: The App Foundation
category:
  - Android
---
The foundation of any app is very important. If you’ve been developing for a while you will have your own style and way of doing things in each app that you use. This is useful and helps to keep things in an order that you find easy to work with. If you’ve not been developing for that long, the task of getting into this kind of routine can be somewhat daunting. From personal experience, it wasn’t until I started programming in a professional capacity – I had been programming as a hobby for ten years previously – that I finally came to work out my own routine. I’ll admit that I did have a lot of help as well – working in an environment with other professional programmers and seeing their own styles is the best way of working your own styles out!

So to help others along (and to speed up development of my own apps) I have published a project that has the basics that every project that I write has. Below are some hints and tips for using it, but hopefully if you look at the code it’s mostly self explanatory! You can find the repository here.

There are a few main points I want to go over. The first is that I always have a base `Activity` and a base Fragment. By this I mean that I have two abstract classes that extend `Activity` and `Fragment` respectively. By doing this we can put in all the methods that we know we will want to access from all of our activities / fragments. The most important ones in the activity are `setRootFragment()` and `pushFragment()`. These two methods give us the ability to easily add new fragments without repeating code. They are probably my favourite methods out of all of them!

The second important methods are `getLayoutId()` and `onCreateWrappedView`. The first method specifies the layout id that the fragment or activity should inflate. The second is used to do any UI setup for the activity or fragment. For example, if you inflate a layout that has a text view and you wish to assign the text view to a class wide field you would do something similar to:

```java
public void onCreateWrappedView() {
globalTextView = (TextView) findViewById(R.id.textView);
}
```

In the fragment it is slightly different as we have to pass in the root view to be able to find the view in question – I think that’s fairly self explanatory, however!

There are some logging functions within the utils.Util class, which stop you having to put in an app tag every time. The class is also useful for putting other methods that are used app wide.

The final thing to note is the Api class. I’ve added a barebones api infrastructure using `Retrofit2`, which I use with a suite of managers (when I require it).
