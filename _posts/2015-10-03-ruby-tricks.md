---
layout:     post
title:      "Ruby hacks/tricks"
date:       2015-10-03 22:07:00
tags: ruby curiosity
categories: ruby
author:     "colleowino"
excerpt: I wanted to know where ruby gem files are intalled and the where require actually looked for scripts 
published: true

---

### finding where require seeks scripts
{% highlight js %}
	ruby -e 'puts $:'
{% endhighlight %}

### where gem files installed 
{% highlight js %}
gem environment
{% endhighlight %}

### use gem in ruby script
I wanted to generate some random data for an app I was testing so I opted to use the ffaker gem. I found out it was easier than I expected. All you have to do is to include the gem, possibly the version and then require the gem afterwards.

{% highlight rb tabsize=2 %}
gem 'ffaker'

require 'ffaker'

# profit

10.times do
	puts  FFaker::Name.first_name
end 

{% endhighlight %}
-----

Want to see something else added? <a href="mailto:colleowino@gmail.com?Subject=Hello">email me</a>

