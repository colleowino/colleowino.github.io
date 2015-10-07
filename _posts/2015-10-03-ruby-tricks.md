---
layout:     post
title:      "Ruby hacks/tricks"
date:       2015-10-03 22:07:00
tags: ruby hacks tips curiosity
categories: ruby
author:     "colleowino"
excerpt: I wanted to know where ruby gem files are intalled and the where require actually looked for scripts 
published: true

---

### Get pry
Its like irb with super powers  
`gem install pry pry-doc`

### finding where require seeks scripts
`ruby -e 'puts $:'`

### where gem files installed 
`gem environment` or <code> bundle show [gemname]</code> inside your rails application

### use gem in ruby script
I wanted to generate some random data for an app I was testing so I opted to use the ffaker gem. I found out it was easier than I expected. All you have to do is to include the gem, possibly the version and then require the gem afterwards.

{% highlight rb tabsize=2 %}
gem 'ffaker' # You don't need this line to use in pry/irb 
require 'ffaker'

#### profit
10.times do
	puts  FFaker::Name.first_name
end 
{% endhighlight %}

### Use better\_errors gem
Its a lot nicer than the default error display in rails

{% highlight rb tabsize=2 %}

group :development do
  gem "better_errors"
end

{% endhighlight %}

