---
layout:     post
title:      "save time through shell script unzipping multiple zip files"
date:       2016-12-15 06:32:00 am
tags: shell bash utility javascript browser-addon newbie
categories: ubuntu
author:     "colleowino"
excerpt: I got carried away and downloaded lots of pdf files in zip files, so I needed a way to extract each file into one directory. I had to brush up on shell scripting to ...

---
![zipfiles](/img/extract-zip.png "the zip files I wanted to extract")
I got carried away and downloaded lots of pdf files in zip files, so I needed a way to extract each file into one directory. I had to brush up on shell scripting to get the job done. Extracting a single file was becoming to tedious. Most of these zip files had either pdf, epub or mobi files. I prioritiezed pdf files. 
My goal was to get the pdf files if there wasn't one, I would take the epub and if that wasn't included I would extract the whole zip archive into a specific dir. (out)
![file types](/img/zip-preview.png "3 possible file type in zip archive")

First off I checked how many zip files I was dealing with about 148 zip archives

	ls *.zip | wc -l 

Guided by the assumption that if there was only 1 file it had to be a pdf file I hacked a script to fetch file count in a zipfile using **zipinfo**,
then grep the number. If it had more than one file I could extract only the pdf file or else extract the single files. 
Started testing commands see if I could successfuly get the file count correctly.

	ls *.zip | xargs zipinfo | grep -Eo '[0-9]{1,4} file'

![xargs zipinfo ](/img/xargs-zipinfo.png "testing zipinfo with without xargs flag")
That didn't work, zipinfo was expecting the arguments to be piped one at a time, so I added -l flag to xargs 

![duplicates ](/img/beware-duplicates.png "duplicates causing you worries")
testing it out shows that It has problems with duplicate files names (1) so I wrote another line to get rid of duplicates

	find -iname "*[0-9]*" -exec rm {} +

Things are moving on smoothly and I moved the snippet to float.sh
	
{% highlight sh tabsize=2 %}

# !/bin/bash
# float.sh
for i in $(ls *.zip)
do
	myvar=$(zipinfo $i | grep -Eo '[0-9] file' | grep -Eo '[0-9]')
	if [ $myvar -gt 1 ]
	then
		unzip $i -d out "*.pdf"
	else
		unzip $i -d out
	fi
done

{% endhighlight %}

Finally run the code ` ./float.sh `
Checked if the files I extracted were equal to the number of files ` cd out  && ls | wc -l `. Surprise, surprise I had 145 files. Something wasn't right
wrote another script to use the zip file names to check if the files had already been extracted. That's how I noticed that some zip files had single file but it was either misspelled e.g .Epub instead of .epub or it was a single .mobi file so It wasn't getting extracted

#### checking if files had already been extracted
{% highlight sh tabsize=2 %}

for i in $(ls *.zip)
do
	str=$(echo $i | cut -c1-33 )
	found=$(find out -iname "$str*")

	# in bash empty strings == false & found returns the filename if found e.g out/file-name.pdf or ''
	if ! [[ $found ]]
	then
		echo $i
	fi

done

{% endhighlight %}

Ended up switching the logic to check if pdf, epub files exist in the zip and extracting them to the correct folder
#### improved logic 

{% highlight sh tabsize=2 %}

for i in $(ls *.zip)
do
	haspdf=$(unzip -l $i | grep -o .pdf)
	hasepub=$(unzip -l $i | grep -o .epub)
	if [ $haspdf ]; then
		echo "pdf: "
		unzip $i -d out "*.pdf"
	elif [[ $hasepub ]]; then
		echo "epub:" 
		unzip $i -d out "*.epub"
	else
		echo "somme: "$i
		unzip $i -d out
	fi
done

{% endhighlight %}
![end result ](/img/end-result.png "the final outcome")

Last but not least rename the files, remove the (www.ebook-dl.com)

	rename -v 's/\(.*\)//' ./*

The biggest take away from this is that you should test your scripts with a few files and always carry out sanity checks. Test each command because one bad command will ruin the whole pipe sequence.

links:
1. [fixing xargs error](http://www.markhneedham.com/blog/2013/06/09/unix-find-xargs-zipinfo-and-the-caution-filename-not-matched-error/)
1. [use zipinfo to read filecount](http://unix.ittoolbox.com/groups/technical-functional/shellscript-l/file-count-in-a-zip-archive-3243725)
1. [fetching numbers in grep](http://askubuntu.com/questions/184204/how-do-i-fetch-only-the-numbers-in-grep)
1. [remove files after calling find](http://askubuntu.com/questions/666001/piping-find-name-to-xargs-results-in-filenames-with-spaces-not-being-passed-to)
1. [shell scripting basics](http://codewiki.wikidot.com/shell-script)
1. [bash arithmetic](http://stackoverflow.com/questions/8304005/how-do-i-do-if-statement-arithmetic-in-bash)
1. [bash cheatsheet](http://ricostacruz.com/cheatsheets/sh.html#ifs)
1. [unzip to particular directory](https://www.cyberciti.biz/faq/linux-howto-unzip-files-in-root-directory/)
1. [unzip specific extensions only](http://stackoverflow.com/questions/908679/unzip-specific-extension-only)
1. [finding strings withing string](http://stackoverflow.com/questions/229551/string-contains-in-bash/229585#229585)
1. [cutting strings in bash](http://stackoverflow.com/questions/219402/what-linux-shell-command-returns-a-part-of-a-string)
1. [mass rename files](http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal)
1. [case insensitive grep](http://droptips.com/using-grep-and-ignoring-case-case-insensitive-grep)
