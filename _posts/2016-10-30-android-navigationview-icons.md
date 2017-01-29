---
layout: post
published: true
author: Joshua Masonw
text-color: FFFFFF
comments: true
title: 'Android NavigationView: Icons'
category:
  - Android
---
In brief, I’ll be describing how to add icons to the Android `NavigationView` component, as well as changing the colours of those icons.

First we need to start off with the XML. You’ll need to start out with a `DrawerLayout`, and within that include your `NavigationView`.

```xml
<android.support.v4.widget.DrawerLayout
    android:id="@+id/drawer_layout"
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:fitsSystemWindows="true"
    tools:openDrawer="start">

    <include
        layout="@layout/app_bar_main"
        android:layout_width="match_parent"
        android:layout_height="match_parent"/>

    <android.support.design.widget.NavigationView
        android:id="@+id/navigation_view"
        android:layout_width="wrap_content"
        android:layout_height="match_parent"
        android:layout_gravity="start"
        android:fitsSystemWindows="false"
        app:headerLayout="@layout/nav_header_main"
        app:menu="@menu/activity_main_drawer" />

</android.support.v4.widget.DrawerLayout>
```

You’ll also notice that here I’ve included the a layout with id `app_bar_main`. This is just a layout for if you want to have a toolbar at the top of your app.

The important thing to notice here for getting our icons into the `NavigationView` is the `app:menu` attribute. This allows us to specify a menu resource, which has the information on what items we want to place in our menu. If you are using Android Studio you can find the “menu” folder within the “res” directory. Right clicking on this folder and selecting New > menu resource file. A typical menu resource will look similar to this:

```xml
<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:android="http://schemas.android.com/apk/res/android">
    <group android:checkableBehavior="single">
        <item android:id="@+id/menu_home"
        android:icon="@drawable/menu_home_black"
        android:title="Home"/>
    </group>
</menu>
```

This XML is at the heart of adding items and icons to the menu. I’m sure from looking at this you can work out that the `android:title` attribute is the title to display in the `NavigationView`, and the `android:icon` attribute is similarly used to specify what drawable resource to use for the icon on the left hand side of the title.

However, this isn’t all. You may notice that if you select a colour icon to be displayed (i.e. not just black and white) it will only display in black and white.This is because of the background tint that is automatically set on the items. To solve this, we need to obtain a reference to the icon in java code, and set the background tint for items to null.

```java
navigationView.setItemIconTintList(null);
```

And that’s it!
