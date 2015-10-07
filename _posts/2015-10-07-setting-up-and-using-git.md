---
layout:     post
title:      "setting up and using git"
date:       2015-10-07 09:15:00 pm
tags: git setup newbie
categories: tools
author:     "colleowino"
excerpt: Version control is key to any software development activity. There are many options and I prefer using git because its easier to branch and I host most of my code on... Tada! github. 

---
#### Install git
<code>sudo apt-get install git</code>

#### Setup git
You need to configure you git installation with your username and email. This email is atttached to every commit you make <code> git config --global user.email "youremail@provider.com </code> <code> git config --global user.name "user name" </code>

### Play around with git 
[git immersion](http://gitimmersion.com/)

### Cheat a little
The best way to learn git commands is to use them frequently and a cheat sheet can help with that. Here's a github [repo](https://github.com/arslanbilal/git-cheat-sheet) with one that you can download in pdf

### Add aliases:
Once you get the hang of git commands you will find it easier to use short-hand commands instead of typing the whole line. You can modify your <code>.bashrc</code> if you use bash, <code>.zshrc</code> if you fancy zsh or modify your <code>.gitconfig</code> file which is neautral to both
Immersion [lab-11](http://gitimmersion.com/lab_11.html) has more on the same.

{% highlight rb %}
alias gs='git status '
alias ga='git add '
alias gb='git branch '
alias gc='git commit'
alias gd='git diff'
alias go='git checkout '
alias gk='gitk --all&'
alias gx='gitx --all'
alias got='git '
alias get='git '
{% endhighlight %}

-----

