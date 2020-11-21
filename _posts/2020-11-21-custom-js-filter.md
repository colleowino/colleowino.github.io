---
layout: post
title: "Today I Learned #1: Custom Javascript Array Filter"
date: 2020-11-21 6:24:00 pm
tags: javascript codewars coding lessons
categories: coding
author: "colleowino"
header-img: /img/js-filter.jpg
---

Turns out I really did not know how javascript's array filter works. Indeed I have used it for a while
but never really made use of some of its advanced features. E.g it accepts an extra param after the callback
that is used as the execution context **this** for the callback.

I filtered out the questions on codewars, pun intended. Looking for something easy withing 6kyu.
The [Javascript from the Inside #2: Filter](https://www.codewars.com/kata/55afe435d2ce100356000032/train/javascript)
seemed like the perfect match.

It took me a bit of time to figure it out, my attempts were mired by lots of frustration. I knew what I wanted it to do
but how was the big question. Every time I changed something, some tests would pass while others would fail.
I almost gave up a few times but now that I have solved it, the journey is much more worthwhile.

I thought that maybe all it needed invoking the callback in a for loop and saving the results in a new array.
Then I realized that I had to implement the complete api. Thankfully mozilla has amazing [documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter).

Initial solution

```js
Array.prototype.filter = function (fun, that) {
  let out = [];
  let vals = [...this];

  if (that) {
    fun = fun.bind(that);
  }
  for (let i = 0; i < vals.length; i++) {
    if (vals[i] && fun(this[i], i, this)) {
      out.push(this[i]);
    }
  }
  return out;
};
```

The code above covered most of the test cases, I figured if I had a new array with only existing values I could avoid arrays with empty slots.
Sadly it saved me from empyt slots but it also prevented me from capturing falsy values.

I thought maybe if I used `entries()` method would give me a better view of what was going on in the array.

```js
> for(k of j.entries()){
    console.log(k)
}

[ 0, undefined ]
[ 1, undefined ]
[ 2, undefined ]
```

Although the empty slots still evaluated to undefined and it wasn't helping me at all.
Another issue was that the array could be modified by the callback and to account for that I had to pass in the newly created array.
when that happens the length of the array in my filter function would increase. `vals.length` then turns into an infinite loop.

The final solution involves binding the context of the callback if it was provided and capturing the length of the initial array.
To overcome the fact that some slots could be empty e.g `[1,2,,,5]` The for loop checks for presense of the key.
I came close to giving up a few times and if it wasn't for mozilla's filter polyfill I couldn't have made it through.

```js
Array.prototype.filter = function (fun, that) {
  let out = [];

  if (that) {
    fun = fun.bind(that);
  }

  let t = this;
  let len = t.length;
  for (let i = 0; i < len; i++) {
    if (i in t) {
      if (fun(t[i], i, t)) {
        out.push(t[i]);
      }
    }
  }
  return out;
};
```

---
