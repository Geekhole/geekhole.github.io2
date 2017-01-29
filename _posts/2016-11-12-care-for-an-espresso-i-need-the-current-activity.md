---
layout: post
published: true
author: Joshua Mason
date: '2015-09-19'
comments: true
title: Care for an Espresso? – I need the current Activity!
category:
  - Android
---
One problem that I faced recently was needing to obtain access to a fragment directly from within my tests. Unfortunately this fragment was added to a different activity to the one that I originally started in. Consequently, whenever I tried to get an instance of the fragment, I could not. To solve this, I had to get an instance of the currently running activity. The following code works like a charm.

```java
public static Activity getActivityInstance() {
   getInstrumentation().runOnMainSync(new Runnable() {
      public void run() {
         Collection resumedActivities = ActivityLifecycleMonitorRegistry.getInstance()
               .getActivitiesInStage(RESUMED);
         if (resumedActivities.iterator().hasNext()) {
            resumedActivity = (Activity) resumedActivities.iterator().next();
         }
      }
   });
   return resumedActivity;
}
```
