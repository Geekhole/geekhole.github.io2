---
layout: post
published: true
author: Joshua Mason
date: '2016-01-11'
comments: true
title: Targeting the iPad – CSS
category:
  - Web
---
Sometimes we want websites to look different in certain platforms. In this case we will be looking at targeting iPads with CSS to make it look different from other platforms.

To do this we will be making use of media queries, which are usually used to target different screen sizes. Below are the relevant media queries required for the various iPads.

iPads in portrait and landscape:

```css
@media only screen and (min-device-width : 768px) and (max-device-width : 1024px) {
/* YOUR STYLES HERE */
}
```

iPads in landscape:

```css
@media only screen and (min-device-width : 768px) and (max-device-width : 1024px) and (orientation : landscape) {
/* YOUR STYLES HERE */
}
```

iPads in portrait:

```css
@media only screen and (min-device-width : 768px) and (max-device-width : 1024px) and (orientation : portrait) {
/* YOUR STYLES HERE */
}
```

### iPad 3 & 4 Queries

If you want to target the iPad 3 & 4 then you’re in luck!

Retina iPads in portrait and landscape:

```css
@media only screen and (min-device-width : 768px) and (max-device-width : 1024px) and (-webkit-min-device-pixel-ratio: 2) {
 /* STYLES GO HERE */
}
```

Retina iPads in landscape:

```css
@media only screen and (min-device-width : 768px) and (max-device-width : 1024px) and (orientation : landscape) and (-webkit-min-device-pixel-ratio: 2) {
 /* STYLES GO HERE */
}
```

Retina iPads in portrait:

```css
@media only screen and (min-device-width : 768px) and (max-device-width : 1024px) and (orientation : portrait) and (-webkit-min-device-pixel-ratio: 2) {
/* STYLES GO HERE */
}
```

### iPad 1 & 2 Queries

Again, we can also specifically target iPads version 1 and 2.

iPads 1 & 2 in portrait & landscape:

```css
@media only screen and (min-device-width : 768px) and (max-device-width : 1024px) and (-webkit-min-device-pixel-ratio: 1){
/* STYLES GO HERE */
}
```

iPads 1 & 2 in landscape:

```css
@media only screen and (min-device-width : 768px) and (max-device-width : 1024px) and (orientation : landscape) and (-webkit-min-device-pixel-ratio: 1)  {
/* STYLES GO HERE */
}
```

iPads 1 & 2 in portrait:

```css
@media only screen and (min-device-width : 768px) and (max-device-width : 1024px) and (orientation : portrait) and (-webkit-min-device-pixel-ratio: 1) {
/* STYLES GO HERE */
}
```

### iPad Mini

Finally, this wouldn’t be complete without looking at the iPad Mini!

iPad mini in portrait & landscape:

```css
@media only screen and (min-device-width : 768px) and (max-device-width : 1024px) and (-webkit-min-device-pixel-ratio: 1)  {
/* STYLES GO HERE */
}
```

iPad mini in landscape:

```css
@media only screen and (min-device-width : 768px) and (max-device-width : 1024px) and (orientation : landscape) and (-webkit-min-device-pixel-ratio: 1)  {
/* STYLES GO HERE */
}
```

iPad mini in portrait:

```css
@media only screen and (min-device-width : 768px) and (max-device-width : 1024px) and (orientation : portrait) and (-webkit-min-device-pixel-ratio: 1)  {
/* STYLES GO HERE */
}
```
