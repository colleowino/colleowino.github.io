---
layout:     post
title:      "Theming your rails application"
date:       2015-10-04 13:25:00
tags: ruby rails bootstrap css 
categories: ruby
author:     "colleowino"
excerpt: There are wide variety of ways to include custoom css files into your bootsrap application, preferably including them in the 'public' folder 
published: true

---

I wanted to use bootstrap css in my rails application without using any gems. 
That mean't downloading the actuall files and including them in the rails application directory. 

### step 1: get the files
My prefered way is to place them in the `public` folder, this way you won't have to juggle different directory refrences for the file to be loaded correctly. No need to add any backslashes for the file name and you can import it as you would do any normal html file.

I naviged to the `public` folder of the rails app and used bower to fetch the files.

`$ bower install bootstrap`

### step 2: Link your css files
Depending on where you want to access the import the css files, You can add the link to either a particular controller's view or to the applications layout file to apply the settings globally.

I placed these files into my `index.html.erb` file and after that everything was styled according to bootstrap, including the glyphicons.

{% highlight html tabsize=4 %}

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta name="description" content="">
    <meta name="author" content="">

    <title>Theming a rails application</title>

    <!-- Bootstrap Core CSS -->
    <link href="bower_components/bootstrap/dist/css/bootstrap.min.css" rel="stylesheet">

</head>
{% endhighlight %}

-----

Want to see something else added? <a href="mailto:colleowino@gmail.com?Subject=Hello">email me</a>

