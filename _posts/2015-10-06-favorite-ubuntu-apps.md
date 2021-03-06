---
layout:     post
title:      "my favorite ubuntu applications"
date:       2015-10-06 23:21:00
tags: ubuntu favorite shell apps 
categories: ubuntu
author: "colleowino"
excerpt: After installing ubuntu you need to install your some apps that will make your experience using ubuntu that much better. 

---
#### Initialize ubuntu software sources
First things first, after the initial install you need to give ubuntu a list of software packages and then this list will be reloaded any time you run the apt-get update command.
<code> sudo apt-get update </code>

#### Get restricted extras:
There are some software that ubuntu isn't allowed to include as part of the vanilla install but they do provide the location to download them. Among them audio/video codecs. Without them you won't be able to play mp3, mp4 and other popular media files. 
To install You need to use apt-get: <code> sudo apt-get install ubuntu-restricted-extras</code>

#### Gdebi
I find it annoying to have to open ubuntu software center any time I need to install a .deb package. You can set gdebi as the default .deb package installer.
<code>sudo apt-get install gdebi </code>

#### z-shell and oh-my-zsh
Through oh-my-zsh you can get better terminal auto completion, plugins and customization options.
<code> sudo apt-get install zsh</code>set it as the default terminal shell <code> chroot </code>

Install zsh <code>curl -L https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh | sh</code> add update your `.zshrc`

References: 
[Become A Command-Line Power User With Oh-My-ZSH And Z](http://www.smashingmagazine.com/2015/07/become-command-line-power-user-oh-my-zsh-z/)

#### VLC
It plays all the popular media formats, set it as the default file type for all your media files and change the settings to open only a single vlc instance.
`sudo apt-get install vlc`

#### Ranger and tree
![ranger](/img/ranger.png)
When looking at a the directory structure of a folder ls may not be enough but tree and ranger are the best addons you could use.
<code>sudo apt-get install ranger</code> & <code>sudo apt-get install tree</code>
[Installing and Using Ranger, a Terminal File Manager, on a Ubuntu](https://www.digitalocean.com/community/tutorials/installing-and-using-ranger-a-terminal-file-manager-on-a-ubuntu-vps)

#### Chrome and Opera browser.
You will have to download the .deb files for each installer but you can them up to update whenever you update the os [chrome](https://www.google.com/chrome/browser/desktop/) and 
[opera](http://www.opera.com/computer)

#### Vim-gnome and tmux
I find it better to work within the terminal and I can edit code using vim. The reason I chose vim-gnome is because it enables you to copy the the system clipboard "\* and through tmux you can open many tabs or windows in one terminal window.
<code>sudo apt-get install tmux vim-gnome </code> 
Then customize your <code>.tmux.conf </code> and <code>.vimrc</code> files as you see fit.

#### get WPS (formerly Kingsoft) office
I tried creating documents using libre office and I didn't like the experience, the best alternative is getting the free community version of kingsoft office.
[kingsoft community](http://wps-community.org/download.html)
![kingsoft writer](/img/kingsoft-writer.png " screen after launching kingsoft office ")

#### cmus and comp terminal music players
Ever wanted to play music right from your terminal without opening up a pesky gui. Well, this is what you are looking for. Unfortunately they don't support vim navigation shortcut keys.
`sudo apt-get install mocp cmus`
