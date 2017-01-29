---
layout: post
published: true
author: Joshua Mason
date: '2015-09-24'
comments: true
title: Care for an Espresso? – Custom Actions
category:
  - Android
---
Using Espresso can be a bit of a chore, especially since there seems to be quite a lot of things that you can’t do. However, there is always a way around these things, and using custom actions is one such way. There is a simple framework that you can use which enables you to gain access to the view itself, thus allowing you to get any information about the view that you would be able to if you were programming natively in Android.

One reason that I use this, personally, is to get the number of rows in a `ListView` (Which is now deprecated, so I would not recommend that you use it!!). By doing this I can then randomize which items are selected from the view to better test how my app works. The framework in question is incredibly simple, as follows:

```java
protected static int getListViewChildCount(Matcher matcher) {
   final int[] count = { 0 };
   matcher.perform(new ViewAction() {
      @Override
      public Matcher getConstraints() {
         return isAssignableFrom(ListView.class);
      }


      @Override
      public String getDescription() {
         return "getting ListView child count";
      }


      @Override
      public void perform(UiController uiController, View view) {
         ListView rv = (ListView) view;
         count[0] = rv.getAdapter().getCount();
      }
   });
   return count[0];
}
```

To explain this a little, what we are doing is defining a custom action to perform on the view itself, using the new `ViewAction()` code, and creating an anonymous inner class. The getConstraints method tells the action what constraint we want to impose on the item we are matching. If you want to be able to perform this action on any view, you could change the parameter of isAssignableFrom to `View.class`. Of course, in this case I only want to be acting upon a list view, other later on we will run into problems.

The `getDescription()` method (as far as I am aware) is only really used when displaying an error in the console. For example, if you tried to perform this action on something that does not match the ListView class you may see something along the lines of `Unable to find matching view for isAssignableFrom ListView`. Don’t quote me word for word on that though!

The final method is where the magic happens. The `perform()` method allows you to act directly on the view in question. As you can see in the example above, I am casting the view that is passed in to a ListView (which is ok, because we know that the view must be a `ListView` of subclass thereof because of the constraints imposed in getConstraints), and then getting the item count from the adapter directly. Voila!

Naturally, because we are within an anonymous inner class we need a field that we can use within it, hence why we have a final integer array declared at the beginning of the method, which we can then modify the first value of within the perform method and then return.

**If there’s any other Espresso testing related things you’d like to see on this blog please let me know and I’ll do my best to write something up on it!**
