---
layout:     post
title:      "Building eye-of-gnome/gthumb from source"
date:       2016-09-04 10:16:00 pm
tags: C builds source linux ubuntu
categories: ubuntu
author:     "colleowino"
excerpt: After switching over to ubuntu, the one app that I missed the most turned out to be google's picasa. I thought it would be a good idea to implement some of the features I missed from picasa into either gThumb or Eye-of-gnome. Little did I know the pain that was waiting for me.

---

I was a big fan of google picasa and it when google finally killed it I was worst affected. Being a windows user for the longest time, I had become accustomed to viewing images through picasa. After switching over to ubuntu, I quickly discovered that viewing pics wasn't the same. So I looked around but there weren't any suitable replacements. As a result I decided to hack the various image viewers to see if I can implement the features that I missed the most. Particularly where the background around the image is transparent.

Since the source is readily available, I thought hacking it would be simple. I would just download the sources of gthumb, eye-of-gnome and optionally shotwell. Learn how they work the boom! implement the feature I wanted. Then reality struck, starting with gThumb and Eog, I learned it isn't easy to build these things from source as I thought. Gthumb was fairly easy.

Basically, You clone the source, navigate to the folder, install the dependencies, configure the build if isn't already and finally make and install. You may be required to pass in build flags if it supports building for different platforms. Most of the instructions are in INSTALL file.

I prefer getting the source from github, they host mirrors to the launchpad repos. Although you can't make pull requests unless you switch to launchpad repos.

{% highlight js %}
 ./configure 
make 
make install
{% endhighlight %}

##### Build gThumb from source [gthumb homepage](https://wiki.gnome.org/Apps/gthumb/development) 
  git clone https://github.com/GNOME/gthumb.git

  sudo apt-get install yelp-tools, libgtk-3-dev, gsettings-desktop-schema-dev

### Build pix from source 
Pix is linuxmints take on gthumb, they forked it and added stuff .
I was building it in ubuntu and run into the issue of missing definitions " AM_INIT_AUTOMAKE", fixed it through reinitiallizing the configure script
autoreconf --install

  git clone https://github.com/linuxmint/pix.git

pix libraries:
You will need all libraries required by gthumb plus **libwebp**

##### Build Eye-of-gnome(Eog) - heartache central
git clone https://github.com/GNOME/eog.git

You require the following libraries:

  libpeas-dev, gnome-common, gtk-doc-tools, yelp-tools
  libjpeg-dev, gobject-introspection,  liblcms 
  libgnome-desktop-3-dev, libgtk-3-dev

Had to fight to figure out which libaries were missing when it didn't compile, It wasn't easy. At that point I didn't even know that you had to look for **-dev** libs to install the C headers required. Eventually I stumbled freshports site that listed the required libraries.

It requires gtk_version 3.19.2 in **configure.ac** I ended up checking what gtk version I had and changed it to the one I had (3.16.7) . Turns out this version they want me to compile with was released in nov 2015, I didn't expect it to be that recent

    dpkg -s libgtk-3-0|grep '^Version'

[Eog on freshports](https://www.freshports.org/graphics/eog)

-----

Want to see something else added? <a href="mailto:colleowino@gmail.com?Subject=Hello">email me</a>

