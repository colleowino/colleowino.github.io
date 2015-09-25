---
layout:     post
title:      "Html, Css and pesticide."
date:       2015-05-13 14:45:00
tags: html css javascript browser-addon newbie
categories: web
author:     "colleowino"
published: true
---

<div class="message">
This is actually a cross posted blog post I had written on Moringa school's <a href="https://moringaschool.wordpress.com/2015/05/13/html-css-and-pesticide/">blog</a> targeted at those who are curious about how web pages work but had never really the gone far in their quest. 
</div>

We all browse the web once in a while. I won’t ask you to tell your neighbor which websites you visit regularly but I would love to hear you explain to him/her how you think it works in “your own words”.

let me give you my version of how it goes down and then at the end, you can judge for yourself if what wrote down fits into your mental model. Either way, the web works and we hope to keep it that way.

When you type in the address eg <a title="http://pesticide.io" href="http://pesticide.io">http://pesticide.io </a>and click enter, the browser creates a request which is then sent to the server.
The server will interpret the request and return a response in a format that the browser understands &#8212; usually HTML along with its associated CSS and optionally Javascript files.
Everything that happens on the server is server-side and what happens in your browser is client side
As a visitor to a webpage, you are rarely concerned about the design but I want to empower you by introducing you to client-side (browser) web technologies in the hopes that you will have a better appreciation for the effort that goes on behind the scenes.
There are 3 technologies used in the browser: *HTML, CSS and Javascript*.

**HTML**:<br/> 
A “Markup language”. It has tags that mark-out different parts of the your HTML page.
The html tags can be nested and each tag has attributes eg

{% highlight html %}
 <h1 class="main_title" > Zorro </h1>
{% endhighlight %}

**CSS**:<br/>
For specifying how to display the contents of html file e.g all h1 tags should have a blue text color

{% highlight css %}
h1 { color: blue }
{% endhighlight %}

**Javascript:**<br/>

Enables you to manipulate the elements of the page after it finishes loading.
When the page loads the browser saves a tree like structure of where every HTML element is as a node. You can then traverse this tree structure, adding and removing elements or even changing the attributes.

**How it works:**<br/>

* In a webpage, everything is a rectanglular “block”. Even the text. All represented by tags, some blocks will occupy a single line no matter their width, you can’t have other elements next to them.
* Blocks/elements follow the box-model. They have borders, padding between the border and content inside them and margins between the border and elements outside them.
* The important attributes of an element are its. width, height and position. They are just 2D boxes.

**Play time:**</br>

1. Open chrome browser and go to [http://pesticide.io](http://pesticide.io), click the “install on chrome” button.
This extension will help you see the true beauty of html. We will use my favourite website as the example, you can substitute mine with any other.

2. Ok, navigate to [https://dribbble.com/](http://dribbble.com)
click the “bug icon” on your top right corner of the browser just to see the border lines.
Then Right-click anywhere in the browser. Then click “inspect element”
A devTools will appear below the page.
The html tags will be displayed in the first column and the next column will show the css for selected element.
Take the magnifying glass, choose one big block in the html tags colum of the devTools.
Unselect the css rules applied to it and then you even see the changes.

###Summary

**HTML:** Specifies the different parts of the page e.g headings(h1-h6), paragraphs(p).

**CSS:**  Defines the styling/presentation e.g Headings font size should be 24px 
<br/>
like h1{ font-size: 24px; }

**Javascript:**  Adds effects to the page, e.g transitioning in/out animations, validating user input and making ajax calls in the background.

-----


