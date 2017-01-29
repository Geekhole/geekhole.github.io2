---
layout: post
published: true
author: Joshua Mason
date: '2016-01-30'
comments: true
title: 'Raspberry Pi: Retropie Console'
category:
  - Personal
---
![RetroPie.png]({{site.baseurl}}/images/RetroPie.png)

So as you may or may not know, the Raspberry Pi 2 came out early last year in February 2015. It’s taken a long while, but finally me and my partner (mainly my partner) got around to setting up [Retropie](http://blog.petrockblock.com/retropie/) on one.

The RetroPie project describes itself as “a collection of works that all have the overall goal to turn the Raspberry Pi into a dedicated retro-gaming console”, and it does this very well with support for early games consoles such as Dreamcast, PlayStation, and Nintendo64.

But enough of that; I’m sure you’re wondering how to go about getting it all set up!

Things you will need:

1. [A Raspberry Pi 2 (Model B)](http://uk.rs-online.com/web/p/processor-microcontroller-development-kits/832-6274/)
1. An [SD card](http://www.amazon.co.uk/Kingston-Class10-microSDHC-Include-Adapter/dp/B0162YQG2I/ref=sr_1_3?s=electronics-accessories&ie=UTF8&qid=1454158920&sr=1-3&keywords=Micro+SD+Card) to put the RetroPie OS and game ROMs on
1. A power supply for the Pi (of course!)
1. A keyboard for setting up the Pi to begin with
1. A screen with a HDMI port and cable
1. A [games controller](http://www.amazon.co.uk/gp/product/B003VD56KC?psc=1&redirect=true&ref_=oh_aui_detailpage_o01_s00) to use with the Pi
1. The [Retropie software image](http://blog.petrockblock.com/retropie/retropie-downloads/retropie-sd-card-image-for-raspberry-pi-2-2/)

It’s important to note that if you’re using the controller linked to above, you’ll need to make sure you also have a USB wireless receiver for the xbox controller as well, as this is not included with the controller itself.

As you can see, I’ve linked to some of the products above that we personally have used, so we know that they work.

We start off by burning the image of the RetroPie software to the SD card so that we can then boot from it. We’re using Apple Macs here, so the software involved is called “[ApplePie Baker](http://www.tweaking4all.com/hardware/raspberry-pi/macosx-apple-pi-baker/)” which takes the hassle out of burning the image correctly. If you’re using windows you can use something like the [Win32DiskImager](http://sourceforge.net/projects/win32diskimager/).

With the SD card inserted into your mac select the IMG file and hit Restore Backup to burn the image to the SD card. This could take a while so you might want to go and grab a cup of tea (or a beer if it’s the evening!) whilst you wait.

Once that’s all done we can move on to putting the SD card into the Raspberry Pi, connecting the keyboard, screen and power supply and waiting for it to boot up. TO be perfectly honest, that’s almost all you need to do… However, sometimes you’ll need to change some of the setup options.

One thing that’s probably a good idea to do is expand the filesystem, which allows you to make full use of all the space on the Pi for adding game ROMs etc. Not only this but having WiFi is often preferable, so if you have a spare wifi adapter laying around you can use that too. To expand the filesystem you can use the steps [described here](https://github.com/RetroPie/RetroPie-Setup/wiki/First-Installation#expand-file-system). The instructions are slightly out of date so your setup might look a little different, but the general idea of where to go and what options to select are still correct.

Setting up WiFi can be found [here](https://github.com/RetroPie/RetroPie-Setup/wiki/First-Installation#configuring-wifi), and is pretty simple really.

The final thing you’ll want to do is be able to transfer your newly curated ROMs to the Pi so that you can use them. There are three ways to do this, depending on whether you’ve connected your Pi to your local network via ethernet or WiFi. The first, that doesn’t require a network connection, is to use a USB drive:

- (ensure that your USB is formatted to FAT32)
- first create a folder called retropie on your USB stick
- plug it into the pi and wait for it to finish blinking
- pull the USB out and plug it into a computer
- add the roms to their respective folders (in the retropie/roms folder)
- plug it back into the raspberry pi
- wait for it to finish blinking
- refresh emulationstation by pressing F4, or choosing quit from the start menu

These steps are taken directly form the [RetroPie project](https://github.com/RetroPie/RetroPie-Setup/wiki/First-Installation#transferring-roms) Github website.

The second and third methods of transferring ROMs requires some form of network connection. I won’t go into detail of the FTP method, as that’s not one that I have tried out. Instead I’ll show you how to transfer them over a file share, which is as simple as drag and drop once it’s setup.

If you’re on windows you can go into File Explorer by pressing the Windows Key + E, and in the address bar at the top type in \retropie which will bring up a list of folders on the Pi. If you’re on Mac simply open Finder, select the Go menu at the top of the screen, select Connect to Server and type in smb://retropie in the subsequent dialog box. From this, the folder you need to copy your ROMs to is aptly named ROMs.

I forgot to mention, there is one last step to all of this… HAVE FUN! Go ahead and test out your newly configured RetroPie console. There’s a lot of documentation on the web of what works and what doesn’t and more configuration that you can do if you want. But for now, I’ll leave you with this, and hope you have a retrotastic time!
