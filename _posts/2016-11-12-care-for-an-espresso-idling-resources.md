---
layout: post
published: true
author: Joshua Mason
date: '2015-09-20'
comments: true
title: Care for an Espresso? – Idling Resources
category:
  - Android
---
One major problem when doing integrated testing of any kind is that if you have asynchronous operations you need your tests to wait for these operations to complete before going forwards. After I recently start using Espresso this issue came up pretty quickly, and despite it being quite an obvious thing, google searches turned up very little. Consequently I am documenting the way to deal with these cases here to make things a little easier for others!

So, what we will be talking about here are called Idling Resources. The best way that I have found to implement these into a large projects is to put seven methods into a base class that all of your activities and fragments extend. Three of these methods are required when you implement `IdlingResources`, the other four are an easy way to manage these resources, especially if you have more than one asynchronous operation that may be running at the same time. So, to get started I will be using a base class called `BaseActivity` (Such an imaginative name, I know).

```java
public class BaseActivity extends Activity implements IdlingResource {

    protected boolean idle = true;
    private List resources = new ArrayList<>();
    private IdlingResource.ResourceCallback callback;

    @Override
    public String getName() {
        return getClass().getName();
    }

    @Override
    public boolean isIdleNow() {
        return idle && resources.size() == 0;
    }

    @Override
    public void registerIdleTransitionCallback(ResourceCallback callback) {
        this.callback = callback;
    }

    protected void registerResource(String identifier) {
        resources.add(identifier);
        updateIdle();
    }


    protected void unregisterResource(String identifier) {
        resources.remove(identifier);
        updateIdle();
    }


    protected void setIdle(boolean idle) {
        if (this.idle != idle) {
            this.idle = idle;
            if (idle) {
                if (callback != null) {
                    callback.onTransitionToIdle();
                }
            }
        }
    }


    private void updateIdle() {
        setIdle(resources.size() == 0);
    }
}
```

The three methods `getName()`, `isIdleNow()` and `registerResource()` are used in espresso when we register the resource with the testing framework (as we will see later). The other methods allow us to mange the resources to tell espresso whether we are idle yet. By using `registerResource()`, we add a string to the resources list, which in turns prevents the `isIdleNow()` from returning true. We can then register as many resources as we want. Of course, we need to remember to unregister the resources when we are done with them.

One example of when we would use this is if we are using a thread to do some operation, and then using an interface to call back to the main thread. We would register the resource just before the beginning of the thread, and then at the end of the callback in the activity / fragment we would then unregister the resource. Usually when using a Thread or a normal `AsyncTask` we shouldn’t need to worry about using an `IdlingResource` because Espresso deals with them itself. However if we are not using the default thread pool for the `Thread` / `AsyncTask` then Espresso is not able to deal with it itself, and consequently we will need the use the `IdlingResource`s. Typically, libraries such as Retrofit do NOT use the default thread pool. Retrofit is the cause of the reason I often have to use `IdlingResource`s in my tests.

The next step is to register the fact that we are using these `IdlingResources` with Espresso, so that it knows to check. This is a little tricky if we have gone into an activity that we didn’t start off with using an `IntentsTestRule` or `ActivityTestRule`. However, luckily we can use some code to get the currently running activity and from there any fragments that we may be using. This code can be found in another of my posts located [here](https://geekhole.github.io/android/2015/09/19/care-for-an-espresso-i-need-the-current-activity/).

```java
@Test
public void myIdlingResourcesTest(){
    IdlingResource resource = (BaseActivity) getActivityInstance();
    Espresso.registerIdlingResources(resource);
}
```

This code is all you need to call before you begin the asynchronous operation. So, if the operation begins when you click a button, call the `registerIdlingResources()` function just before you tell Espresso to click the button. At the end of the test, or when you are finished with the resource, remember to unregister the resource.

```java
 @Test
 public void myIdlingResourcesTest(){
        ...
        Espresso.unregisterIdlingResources(resource);
}
```

If you have a lot of `IdlingResource`s it might be a good idea to create a helper class that registers all the resources for the tests, and then cleans them all up in the `@After` all.

Something like the following does the trick nicely for me.

```java
public class IdlingResourcesHelper {
   private static ArrayList<IdlingResource> idlingResources = new ArrayList<>();

   private static void registerResource(IdlingResource resource) {
      Espresso.registerIdlingResources(resource);
      idlingResources.add(resource);
   }


   /** Unregisters all resources and cleans all static data in the IdlingResources class. This should be used after
    * each test has been completed to ensure we start with a new set of data each time. */
   public static void clean() {
      for (IdlingResource resource : idlingResources) {
         Espresso.unregisterIdlingResources(resource);
      }

      idlingResources.clear();
   }
}
```
