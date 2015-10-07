---
layout:     post
title:      "my favorite ubuntu applications"
date:       2015-10-06 23:21:00
tags: ubuntu favorite shell apps 
categories: ubuntu
author: "colleowino"
excerpt: After installing ubuntu you need to install your some apps that will make your experience using ubuntu that much better. 

---
#### First things first:
After the initial install you need to give ubuntu a list of software packages and then this list will be reloaded any time you run the apt-get update command.
<code> sudo apt-get update </code>

#### Get restricted extras:
There are some software that ubuntu isn't allowed to include as part of the vanilla install but they do provide the location to download them. Among them audio/video Codecs. Without them you won't be able to play mp3, mp4 and other popular media files. 
To install You need to use apt-get: <code> sudo apt-get install ubuntu-restricted-extras</code>

#### Get gdebi
I find it annoying to have to open ubuntu software center any time I need to install a .deb package. You can set gdebi as the default .deb package installer.
<code>sudo apt-get install gdebi </code>

#### Install z-shell and oh-my-zsh
Through oh-my-zsh you can get better terminal auto completion, plugins and customization options.
<code> sudo apt-get install zsh</code>set it as the default terminal shell <code> chroot </code>

install zsh <code>curl -L https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh | sh</code> add update your `.zshrc`

References: 
[Become A Command-Line Power User With Oh-My-ZSH And Z](http://www.smashingmagazine.com/2015/07/become-command-line-power-user-oh-my-zsh-z/)

-----

