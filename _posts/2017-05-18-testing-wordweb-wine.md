---
layout:     post
title:      "WordWeb on Ubuntu via wine"
date:       2017-5-18 18:38:00 pm
tags: wordweb wine utility tools
categories: ubuntu
author:     "colleowino"
header-img: /img/wordweb.png

---
Sometimes you need to look up a certain word but you do not have the luxury of looking it up online. An offline dictionary will suffice. I was accustomed to using WordWeb on windows but after making the switch to ubuntu I wasn't able to find a replacement. Turns out I can continue using it by installing <a href="https://www.winehq.org/">wine</a> on my machine **(wordweb8, ubuntu 17.04, wine 1.87)**.

#### install wine

	sudo apt-get install -y wine1.6-amd64

#### install word web
After downloading it from <a href="http://wordweb.info/free/">here</a> it you will need to install it through the terminal. Navigate to where you downloaded it and use the wine command to start the process

	wine wordweb8.exe

#### post install
If all went well you will have the wordweb indicator appearing on the panel.
![okhttp](/img/wordweb-indicator.png "wordweb indicator")
