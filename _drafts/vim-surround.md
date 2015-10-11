---
layout:     post
title:      "using vim surround plug-in"
date:       2015-10-11 03:21:00 PM
tags: vim terminal hacks tips productivity
categories: ubuntu
author:     "colleowino"
excerpt: Dealing with markup is hard enough but after installing the surround plug-in things got a little easier 

---

#### Installation:
I prefer using pathogen to manage my plug-ins all you have to do is clone the repo in the <code>~/.vim/bundle</code> directory and you are good to go. 

<code>git clone https://github.com/tpope/vim-surround.git </code>

##### workflow:
There are different types of surrounding tags

* Quotes: single **'** and double **"**, even backticks **`**
* Brackets: square **[]**, curly **{}** and the usual **()**
* Tags: mostly html <strong> opening and /closing </strong>

#### Surrounding words
Place the cursor within that word and type `ysiw` followed by the desired container eg `ysiw<em>` <strong> Yank(copy) surround to inner word </strong>
Using opening brackets adds spacing before and after word, while the closing ones don't.
Try `ysiw{` vs `ysiw}`

#### Removing surrounds 
To remove them `ds`+ surround depending on which type of quotes you used. e.g `ds"` or `ds{`

##### Interchanging surrounds :
You can change 'hello' to "hello" by placing the cursor inside the word and typing `cs'"`
Which read <strong>change surround single-quotes to double-quotes</strong> you can interchange them.<br/>
That works for all other surrounds except tags e.g.	`<em>` For those you have to change them to another surround then back to your desired tag. So `cst'` <strong>Change surround to single-quote</strong> then `cs'<p>`

