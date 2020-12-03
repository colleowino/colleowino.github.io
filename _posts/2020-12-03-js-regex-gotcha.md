---
layout: post
title: "Today I Learned #3: Javascript RegExp gotcha"
date: 2020-12-02 9:14:00 pm
tags: javascript codewars coding lessons
categories: coding
author: "colleowino"
header-img: /img/codewars.jpg
---

Whenever I find myself working with strings I usually end up using regex to life easier. I was quite shocked to stumble on a regex gotcha
within Javascript while working on [Find the unique string](https://www.codewars.com/kata/585d8c8a28bc7403ea0000c3).

A quick summary of the problem. You have a list of strings made using the same characters except one string made up of unique characters.
My solution takes the first string, converts it into a regular expression and then splits the strings based on if they match the other strings.
Finally I return the first string from the shortest list.

#### RegEx solution

```js
function findUniq(arr) {
  // do magic
  let pick = new Set(arr[0]);
  let reg = new RegExp(`[^${[...pick].join("")}]`, "ig");
  /// assuming its generic
  let withPick = [];
  let without = [];
  for (let i = 0; i < arr.length; i++) {
    let current = arr[i];
    if (reg.test(current)) {
      withPick.push(current);
    } else {
      without.push(current);
    }
  }

  if (without.length == 1) {
    return without[0];
  } else {
    return withPick[0];
  }
}
let t = ["Tom Marvolo Riddle", "I am Lord Voldemort", "Harry Potter"]; // 'Harry Potter'
```

It seemed to pass the basic tests but the result wasn't reliable. It would pass one test and the same test on retries.
The reason was that I had included the global 'g' modifier and if you reuse the same same regex with different strings, it will move to the lastIndex Of
the last match. In a sense it is treating each new string you are testing as a continuation of the last matched word.
To avoid that situation I decided to remove the global modifier. I could have also initialized the regEx for each line I was testing.

Links:

- [RegEx.test() returns alternating results](https://medium.com/@nikjohn/regex-test-returns-alternating-results-bd9a1ae42cdd)

---
