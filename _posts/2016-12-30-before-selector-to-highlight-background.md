---
layout:     post
title:      "highlight list element using :before selector"
date:       2016-12-30 01:23:00 pm
tags: html css tricks
categories: web
author:     "colleowino"
excerpt: Using the css before selector to highlight a selected div 

---
![before hover selector](/img/before-hover.png "on mouse hover the before selector adds orange highlight")
Moving the mouse on an item in the list changes the backgound of the image and color of the title. Figuring out which element's hover state created the effect was key.
The hover state was linked to the list and its css linked to the other components.
![toogle hover state](/img/toggle-list-state.png "toggling hover state through dev-tools")

The img itself has to be in a div `img_wrap` and on mouse over the before select of the wrapper div is modified

{% highlight css tabsize=2 %}

.articles-lst li .img_wrap {
    position: relative;
}

.articles-lst li:hover .img_wrap:before {
    content: '';
    display: block;
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    background: rgba(255,63,13,.4);
}

{% endhighlight %}

Alternatively you can create a new div in img_wrap with the same properties along with `display:hidden` and reveal it on hover state

### References
1. [original source of css technique](http://illusion.scene360.com/art/98099/katie-shocrylas/)
2. [W3 School: before selector examples](http://www.w3schools.com/cssref/sel_before.asp)

