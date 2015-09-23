---
layout:     post
title:      "Aligning Html elements"
date:       2015-09-23 18:45:00
author:     "colleowino"
published: true
---

<div class="message">
Often you want to align html elements either to the center or side of the line. I will go over a few solutions using uxpin's 
<a href="http://www.uxpin.com/about-us.html">about</a> page as the sample along with chrome dev tools to investigate what's going in the background. 
</div>

### Workflow:

You have two options depending on what you want to align. The only requirement is that the component has block level properties. That means it could occupy a single line or be shifted to the right or left. You could use:

- text-align
- Margins/paddings
- Offset positioning
- floats


##### aligning text:
![placeholder]({{ site.baseurl }}/img/uxpin-text-left.png)

{% highlight css %}
.content {
	text-align: right;
	/* options: left, right, center */
	/* Applies to: Headings, paragraphs, spans, mostly text within an element.*/
}
{% endhighlight %}


### Moving whole elements:
![placeholder]({{ site.baseurl }}/img/uxpin-div-center.png)
If you want to align a block level element, Lets say a div to the right or the left you can easily do that using float. The only downside is that the element will be no longer occupy the whole line after but collapse to the width of its content.
You can fix that using *clear*

{% highlight css %}
.content {
	float: left;
	/* options: right/left*/
	/* Applies to: Nearly all block level elements eg headings, paragraphs */
	clear: right; /* you want no element to occupy the vacant space beside this element */
}
{% endhighlight %}

You can center align divs using auto for right and left margins instead.

{% highlight css %}
.content {
	margin: 0 auto;
}
{% endhighlight %}


### Moving withing element aboundaries:
![placeholder]({{ site.baseurl }}/img/uxpin-margins.png)
Some time you just want the text to move slightly to the side. Lets say 100px from the left edge of the viewport. You are have the option of adding specific left margins/paddings.

##### Margins and paddings:
Padding/margin depends on where the space will come from either within the element or outside it. Not different unless you intend to add outlines on the element

{% highlight css %}
.content {
	margin-left: 30px;
	padding-left: 30px;
	/* options: You can use specific measurements eg em, 20%, px  */
	/* Applies to: Nearly all elements, I doubt if it works on the body tag.*/
}
{% endhighlight %}

##### Offset properties:
Similar to Margins and Paddings but only apply to absolutely positioned elements. If you want to position elements relative to the parent element you have set parent positioning to relative and then child elements to absolute. This is an alternative to using huge amounts of padding.

{% highlight css %}
.parent {
	width:50%; /* maintain the parent element's size even when its empty */
	position: relative;
}

.child {
	position: absolute;
	/* move 30px from both the left and bottom edges */
	left: 30px;
	bottom: 30px;
	z-index: 2; /* raise the child above the parent element */
}

{% endhighlight %}


-----

Want to see something else added? <a href="mailto:colleowino@gmail.com?Subject=Hello">email me</a>
