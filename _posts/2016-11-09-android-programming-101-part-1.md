---
layout: post
published: true
author: Joshua Mason
comments: true
title: 'Android Programming 101 - Part #1'
date: '2015-09-14'
category:
  - Android
---
One of the most important tools in a programmer’s arsenal, one without which development is practically impossible, is the Integrated Development Environment, or IDE. There are two good IDEs that you can use for Android programming: *Eclipse* or *Android Studio*.

In this guide I will be showing you how to use Eclipse as a development environment for Android.

### Download and install Eclipse

The first step is to obtain a copy of Eclipse from [the Eclipse website](http://www.eclipse.org/downloads/). I would suggest downloading the Eclipse IDE for Java Developers which should be the first download on the page.

The download will consist of a zip file with all the program files contained within it. All you need to do to ‘install’ it is unzip the contents of the folder and place it wherever you want to keep it. If you are using windows and decide to put it in the Program Files folder you may need to run eclipse as an administrator by right clicking on the eclipse.exe file and selecting **Run as Administrator**.

You may also get the following message when you try to run Eclipse for the first time:

*Picture missing*

This just means that you don’t have the Java Runtime Environment (JRE) and associated Java Development Kit (JDK) tools installed. It’s a simple fix, honestly! [Click here](http://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html) and download and install the latest version of the JRE.

After this, try running eclipse again and you should get to the workspace selection screen.

### Install the Android plugin

A workspace is a place you can store multiple projects. For example, you might have two related projects one for getting data from a server (Client) and one that sends this data to the client (Server). This is just one example of when you might want to have multiple projects stored together.

Once you’ve selected a workspace you should be presented with the start page of Eclipse. At this point we still aren’t ready to start developing on Android. We first need to install the Android plugin for Eclipse.

Go to the **Help** > **Install New Software**.

From the resulting screen select Add and fill in the Name and Location fields as

Name: Android plugin

Location: https://dl-ssl.google.com/android/eclipse

*Picture missing*

Follow the wizard through, making sure that you select the *Developer Tools* option before proceeding. This may take a little while, so feel free to go grab a coffee in the mean time!

Once complete, restart Eclipse and you should find some new icons in the icon bar. The first button, the one that looks something like the Android logo in a little box with a down arrow, is the SDK Manager.

*Picture missing*

### Setup the SDK manager

We’ll need to download some things using the SDK manager before we start developing, so click on the button and give it a moment to load up.

*Picture missing*

Which options you will want to select on this screen very much depend on which versions of Android you want to develop for. As you can see from the above screenshot there are a lot of different options for the different versions of Android. If you have an Android device and don’t intend on using an emulator you can ignore all the items referencing System Images. What you will need, however, are the SDK Platforms for each version of Android you want to develop for, and possibly the Google APIs.

Select all the items relevant to you and install them. This can take a very long time depending on the speed of your internet and the speed of you machine, but once complete you are finally ready to start some programming!
