---
layout: post
title: "Don't overthink, Just howl"
date: 2021-02-28 12:32:00 pm
tags: python kattis coding lessons
categories: coding
author: "colleowino"
header-img: /img/kattis.png
---

This is solution for [howl](https://open.kattis.com/problems/howl) challenge from [kattis](https://open.kattis.com/).
The question requires that you return a **Howl** that is longer than the one provided in the input. The howl has to meet some requirements.

- It must consist of a combination of the letters A, H, O and W. Each letter must occur at least once.

- The howl can not contain two consecutive W’s, or two consecutive H’s.

- The howl can not contain an H followed immediately by a W or an A.

- There can never be an A after the first occurrence of an O.

At first I didn't have a clue how to solve it. I thought that maybe I would have to come up with all sorts of valid combinations and then pick the first one that was longer
than the input. Alternatively I could have modified the input by making it longer but still valid.
Then I noticed something interesting. The tests for this question was only asking for a longer string even if its just by one character. So why not build my own
custom string that just add a bunch of 'O' character to the end. Once again Occam's razor prevails.

#### Challenge solution

```py
print(input()+'O')
```

---
