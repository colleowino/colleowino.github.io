---
layout:     post
title:      "Helpful ubuntu terminal commands"
date:       2015-10-05 17:00:00
tags: hacks bash terminal 
categories: ubuntu
author:     "colleowino"
excerpt: To get the most out of your terminal you often need to remember commands. Like how to display all directories. How to find files etc. 

---

#### Listing only directories in the current path
` ls -d */ `  # use -C to sort the files

#### Add lines to the end of a text file
` echo "some text" >> output-file.txt `

#### Finding files in current directory. 
` find -name "random-name*" ` # This lists the matching files and their paths 

` find -name "random-nae*" | wc -l ` #lists number of results through wc

#### List all aliases and their definitions
` alias ` or <code>which [keyword]<code>

-----

