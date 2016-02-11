---
layout:     post
title:      "using git submodules to track vim/tmux/zsh extensions"
date:       2016-01-11 11:45:00 pm
tags: git setup vim 
categories: tools
author:     "colleowino"
excerpt: After switching over to vim am always on the lookout for extensions that make me more productive. Vim save you time as it is but some things are just a pain to do. In this post go over how I started using submodules to keep track of changes occuring in the extensions I added. 

---
#### Use aliases
In the root folder of my dotfiles, my home directory. I have a .gitmodules file that lists each extension along with its name and directory. I have .oh-my-zsh, tmux and vim extensions included. To make it easier I made new aliases to add modules, update and one to quickly edit the modules file if I ever needed to.

{% highlight rb %}
# git submodules 
alias gitmods="vim .gitmodules "
alias gitnewmod="git submodule add "
alias gitmodupdate="git submodule update "

# vim bundles folder
alias vimbundles='cd ~/.vim/bundle'
{% endhighlight %}

#### add your extension
Grab the link e.g https://github.com/easymotion/vim-easymotion, navigate to your vim extensions folder. I prefer to use pathogen, all I you need to do is place the file in the bundle folder.  
<code>vimbundles</code> and to clone it as a submodule

<code> gitnewmod https://github.com/easymotion/vim-easymotion </code>


#### profit
You can even checkout the .gitmodule file to see if it has been update.<code>gitmods</code>
If everything went well, the gitmodules file should look like this

{% highlight js %}
[submodule ".vim/bundle/vim-easymotion"]
	path = .vim/bundle/vim-easymotion
	url = https://github.com/easymotion/vim-easymotion.git
{% endhighlight %}

### References
[my dotfiles](https://github.com/colleowino/dot-files) You can see what other extensions am using. 
<br/>
[gitmodules manual](https://git-scm.com/book/en/v2/Git-Tools-Submodules) Sometimes you need the manual.

-----

