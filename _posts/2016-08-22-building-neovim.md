---
layout:     post
title:      "building neovim from source"
date:       2016-08-22 07:43:00 pm
tags: git neovim vim customization
categories: tools
author:     "colleowino"
excerpt: I heard a lot about neovim and decided to try it, it wasn't smooth sailing but am glad that eventually I got to work.

---

Decided to do something exciting this weekend, so I built neovim from it source.
Started out by finding a site that actually explained how to do it but it was a bit misleading. Installed dependencies but still couldn't build the thing. Any who if you decide to build neovim from its source better make sure that you install the libtools-bin and optionally remove linuxbrew.
The best part is that the python support is on by default but you need to add neovim python package.
If you run the build from the build folder it will complain about syntax issues.

#### clone neovim:

	git clone https://github.com/neovim/neovim


#### install dependencies:
	
	sudo apt-get install libtool libtool-bin autoconf automake cmake libncurses5-dev g++

#### make python bindings available:

	sudo apt-get install python-dev python-pip python3-dev python3-pip

#### Go to the root of the project and build: 

	make 
	make test

#### Install to access helptags and fix missing "syntax.vim" in /usr/share...

	make install

#### You may want to user your current vim config for the instance:
{% highlight rb %}

	ln -s ~/.vim ~/.config/nvim
	ln -s ~/.vimrc ~/.config/nvim/init.vim

{% endhighlight %}
#### Even fix some incompatibility issues:

{% highlight rb %}

	if !has('nvim')
		set ttymouse=xterm2
	endif

{% endhighlight %}

### Profit!

### References
2.	[neovim wiki](http://github.com/neovim/neovim/wiki/Installing-Neovim)
<br/>
3.	[a nice article on the same](http://veelenga.com/editors/how-to-start-using-neovim-instead-of-vim/)

-----

