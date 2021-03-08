---
layout: post
title: "Converting webp files to png via terminal"
date: 2021-03-08 03:50:00 pm
tags: ubuntu tools terminal shell
categories: ubuntu
author: "colleowino"
---

I believe you are familiar with [Dribbble](https://dribbble.com/). Often enough I download images to use as a moodboard but unfortunately they come in webp format and ubuntu doesn't show thumbnails by default. I figured I could just convert all of them to png instead of installing more stuff. I used **ffmpeg**

```sh
find ./ -name "\*.webp" -exec ffmpeg -i {} {}.png \;
```

You end up with weird names like **handle-bars.webp.png** but I can live with that.

Then i removed all the **.webp** files in that directory

```sh
  rm *.webp
```

Links:

- [stackoverflow](https://unix.stackexchange.com/questions/70622/convert-webp-to-jpg-error-no-decode-delegate-for-this-image-format-and-missi/70673#70673)

---
