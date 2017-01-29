---
layout: post
published: true
author: Joshua Mason
date: '2015-09-18'
comments: true
title: Android – Rounded Window Corners
category:
  - Android
---
Recently I came across the issue of needing to round the corners of some popup windows. At first I thought, simple, I’ll just use an XML shape as the background of my window and use a radius on the corners… But then I quickly realised that if I did this, and then put an image full screen as the background it would overlap the corners and make them square once again.

In order to get the effect that I wanted, I needed to prevent anything from drawing on the corner of the windows in the arc of the rounded corner. The code to do this is fairly simple. By extending a layout (In my case I used a FrameLayout as my parent layout), and overriding the draw function we are able to change the default behaviour of the canvas.

```java
public class RoundedFrameLayout extends FrameLayout {
   private Path mPath;
   float mCornerRadius;


   public RoundedFrameLayout(Context context) {
      super(context);
      init();
   }


   public RoundedFrameLayout(Context context, AttributeSet attrs) {
      super(context, attrs);
      init();
   }


   public RoundedFrameLayout(Context context, AttributeSet attrs, int defStyle) {
      super(context, attrs, defStyle);
      init();
   }


   private void init() {
      mCornerRadius = 10 * getResources().getDisplayMetrics().density;
   }


   @Override
   public void draw(Canvas canvas) {
      canvas.save();
      canvas.clipPath(mPath);
      super.draw(canvas);
      canvas.restore();
   }


   @Override
   protected void onSizeChanged(int w, int h, int oldw, int oldh) {
      super.onSizeChanged(w, h, oldw, oldh);
      RectF r = new RectF(0, 0, w, h);
      mPath = new Path();
      mPath.addRoundRect(r, mCornerRadius, mCornerRadius, Path.Direction.CW);
   }


   /** @param radius This should be in dp */
   public void setCornerRadius(int radius) {
      mCornerRadius = radius * getResources().getDisplayMetrics().density;
      invalidate();
   }
```

If you use this layout at the root of your XML and place all other views within you can be sure that nothing will extend over your rounded corners. You can programatically set the amount to round the corners by calling the setCornerRadius method, or alternatively just by leaving the code as is the corners will automatically be rounded by 10dp.
