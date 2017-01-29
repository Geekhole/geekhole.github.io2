---
layout: post
published: true
author: Joshua Mason
date: '2016-01-21'
comments: true
title: 'IllegalStateException: The specified child already has a parent'
category:
  - Android
---
To be precise, this error reads:

> java.lang.IllegalStateException: The specified child already has a parent. You must call removeView() on the child’s parent first.

This is an error I recently came across when trying to get a recycler view to work. At first this can seem a bit confusing, but really it is very simple. Generally it means that you’ve forgotten one tiny detail in your onCreateViewHolder method.

When inflating the layout resource for your view holder, you’ll likely have a line similar to

```java
View view = LayoutInflater.from(parent.getContext()).inflate(R.layout.row, parent);
```

This is all very well and good… except that using this version of the `inflate()` method actually tells the layout that it should attach itself to the layout parent… Instead we need to tell it not to do this by using

```java
View view = LayoutInflater.from(parent.getContext()).inflate(R.layout.row, parent, false);
```

The only difference here is we have added a parameter at the end; the boolean ‘false’. And that little parameter will solve all your problems! (well, perhaps not all, but at least one)
