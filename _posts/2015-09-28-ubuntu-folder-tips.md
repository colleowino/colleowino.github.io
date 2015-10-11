---
layout:     post
title:      "Ubuntu folder tips"
date:       2015-09-28 08:42:00
tags: ubuntu linux nautilus tips shortcut hacks productivity 
categories: ubuntu
author:     "colleowino"
excerpt: I have tend to organize my files into distinct folders, each with a particular purpose. To get the most out of this, I utilize keyboard shortcuts among other things. Here I share my process.
published: true

---

Ubuntu ships with nautilus as its default file explorer. It's listed as "files" in the programs list. The screenshots I have used my explanations may have a different icons and theme different from the default ubuntu theme. On my machine I am using the [arc theme](https://github.com/horst3180/Arc-theme) and [moka icons](http://snwh.org/moka/moka-icon-theme/download/)

#### Add a global shortcut to open the files explorer (nautilus).

After switching over to ubuntu, one of the first things I missed was the ability to open the file explore with the **`Win+E`** font combination. But its easy to fix. 

- Open system settings
- Select Keyboard, shortcuts tab and launcher Panel.
- Locate and click **Home folder**, then click type the desired keyboard shortcut. In this case the "win" key or super and E. 
- Close The settings dialog and try out the shortcut.

![placeholder]({{site.base-url}}/img/ubuntu-keyboard-shortcuts.png "setting home folder keyboard shortcut")

#### Auto mount the extra partitions on your hard drive 

I had have 3 partitions on my hard drive, one for windows, another for ubuntu and a third for all my data. This structure enables me to only worry about wiping one partition in case my OS started acting up. 

Unfortunately after booting into ubuntu the other partitions are not mounted by default so I had to set them up to auto mount.

- Open Disks application
- Select the partition you wish to automount
- Click on the cog wheels and select "Edit mount options..." from the menu that shows up
![disks]({{site.base-url}}/img/open-ubuntu-disks.png "start up ubuntu disks program")
- Toggle the "Automatic mount options" It should appear "off" after
- Tick the "mount at startup" option.
- Optional: I recommend you use a descriptive mount Point eg /mnt/backup
![auto mount]({{site.base-url}}/img/edit-mount-options.png "auto mounting partitions")
- click done, type in your password when prompted to and your auto mount is setup. 
- You may have to restart ubuntu for the changes to take effect

#### Bookmark folders you use often 

When you have the explorer open you can type **`ctrl+D`** and the shortcut will appear below the default folders e.g. Documents and other mounted file-systems.

#### Use tabs.
![folder tabs]({{site.base-url}}/img/ubuntu-folder-tabs.png "using tabs")
They are better than having multiple file explorers open through **`ctrl+T`**


#### Edit the address bar
![address bar]({{site.base-url}}/img/edit-address-bar.png "editing the address bar")

Nautilus folders up the directory tree through a set of button tabs at the top of each folder. To edit the folder manually you can use **`Ctrl+L`**, the press **`Esc`** while the cursor is still on the address to return back to the default view 

