---
layout:     post
title:      "testing okhttp java library though ubuntu terminal"
date:       2017-2-10 04:14:00 pm
tags: java okhttp ubuntu terminal
categories: ubuntu
author:     "colleowino"
header-img: /img/okhttp.png

---
![okhttp](/img/okhttp.png "a HTTP & HTTP/2 client for android and java applications")
I wanted to add okhttp library to an android app and noticed that I could also use the same library in a regular java file. So I went for it. Good thing they provided some sample code.

## 1. Download the Code
Get the libraries for `okttp` and `okio`, you have to enclose the `wget` for okio  because it contains an '&' and also provide the output file name otherwise it will save it with an inconvenient name 

	wget http://repo1.maven.org/maven2/com/squareup/okhttp3/okhttp/3.6.0/okhttp-3.6.0.jar	
	wget -O okio.jar "https://search.maven.org/remote_content?g=com.squareup.okio&a=okio&v=LATEST"	

Fetch the sample code as well and remove the package name[package okhttp.guide] just to make things simpler.

	wget https://raw.github.com/square/okhttp/master/samples/guide/src/main/java/okhttp3/guide/GetExample.java 

### 2. Build the code.
I had a hard time figuring out how to do this but the trick was using the wild card in the classpath argument sent to `javac`. That will include any jar files within the current directory.

	javac -cp "*" GetExample.java

### 3. Run the code
This part actually caused me most of the problem if you don't include current directory in the classpath argument you will run into `Error: Could not find or load main class GetExample`
	java -cp ".:./*" GetExample.java

### References
1. [okhttp](http://square.github.io/okhttp/)
2. [Putting the Current Directory in the CLASSPATH
](http://javaevangelist.blogspot.co.ke/2008/06/putting-current-directory-in-classpath.html)

