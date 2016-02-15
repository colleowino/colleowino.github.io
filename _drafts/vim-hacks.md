---
layout:     post
title:      "vim editor: hacks and tricks"
date:       2015-10-11 02:21:00 PM
tags: vim terminal hacks tips productivity
categories: drafts
author:     "colleowino"
excerpt: As a developer knowing your tools in and out will save you a great deal of time and make you more productive. I was a big fan of sublime text but after I gave vim a chance I never looked back 

---

#### Changing case:
This usually works in visual mode after selecting text. Press `u` to convert to lowercase, press `U` to convert to uppercase and backtick <code>`</code> to toggle case.

#### Working with lines:
Deleting lines `dd` or `D`<br/>
Selecting an entire line `V`

#### Shortcuts:
Vim is all about mastering the keys that will get you what you want.

##### folding:
![vim folding cheat](/img/vim-folding.png)
[vim-folding-fun](https://www.linux.com/learn/tutorials/442438-vim-tips-folding-fun)

#### Plugins:
[best of vim](http://www.bestofvim.com/plugin/)

##### emmet
If you do a lot of html/css work you can't go wrong with this one. The default trigger
keys being `<C-y>,` 

	git clone https://github.com/mattn/emmet-vim.git ~/.vim/bundle/vim-easymotion

##### easy-motion
If the cursor was at the first line and you wanted to move to the 5th word of the 8th
line, you would have to move 4j, 8w. With easy-motion you don't have to do this mental
math. <br/>

	git clone https://github.com/easymotion/vim-easymotion ~/.vim/bundle/vim-easymotion

#### lightline
I prefer this status bar enhancement plugin compared to airline because it light weight.

	git clone https://github.com/itchyny/lightline.vim.git ~/.vim/bundle/lightline

#### youCompleteMe
Its a fast, as-you-type, fuzzy-search code completion engine for Vim.
- it requires you to build some things from source and download other things as well

	git clone https://github.com/Valloric/YouCompleteMe.git ~/.vim/bundle/youCompleteMe

### More reading
2. The best article so far on vim [learn vim progressivley](http://yannesposito.com/Scratch/en/blog/Learn-Vim-Progressively/)
1. [all the right moves](http://vim.wikia.com/wiki/All_the_right_moves)
2. [vim wikia](http://vim.wikia.com/wiki/Vim_Tips_Wiki)
2. [vim casts](http://vimcasts.org/)
2. [usevim](http://usevim.com/)
2. [vim as IDE](http://yannesposito.com/Scratch/en/blog/Vim-as-IDE/)
2. [lococast vim](http://lococast.net/archives/tag/vim)
