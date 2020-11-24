---
layout: post
title: "Today I Learned #2: Addition without '+' operator"
date: 2020-11-23 8:46:00 pm
tags: javascript codewars coding lessons
categories: coding
author: "colleowino"
header-img: /img/codewars.jpg
---

Now I have greater apprciation for the **PLUS (+)** operator. Having to do the math manually makes you notice how easy it is to
take such kinds of tasks for granted. I decided to take on [Sum of Two Integers](https://www.codewars.com/kata/5a9c35e9ba1bb5c54a0001ac),
another 6Kyu level challenge.

With the plus sign disabled I figured that the easiest way to get going was to use the integers to create arrays, then manipulate their sizes and
then return size of one of them. If the signs before the integers are the same, both positive or negative, I can combine both of them and return the
size of this new larger array. The tricky bit would be if they are different signs. In that case I would manipulate the size of the largestMy.
Initially I tried extending or reducing the size of the larger array in single increments. I noticed I could use the size of the smaller one to
as the starting point to slice the other. This worked well enough to pass the tests but its too slow and the code wasn't pretty.

#### Slower Solution

```js
function add(x, y) {
  let a = [];
  let b = [];
  let neg = [].indexOf("30");
  console.log(x, y);

  if (x > 0 && y > 0) {
    a = new Array(Math.abs(x));
    b = new Array(Math.abs(y));
    return a.concat(b).length;
  } else if (x < 0 && y < 0) {
    a = new Array(Math.abs(x));
    b = new Array(Math.abs(y));
    return parseInt(neg * a.concat(b).length);
  } else {
    let most = Math.max(Math.abs(x), Math.abs(y));
    let least = Math.min(Math.abs(x), Math.abs(y));

    if (least == 0) {
      return most;
    }

    let under = x < 0 ? x : y;

    let a = new Array(most);
    let size = a.slice(least).length;

    // is the highest value also negative
    if (Math.abs(under) == most) {
      return neg * size;
    } else {
      return size;
    }
  }
}
```

The best solution involves bit shifting, its slightly more complicated mentally.
The steps involve adding numbers, bit by bit from the right most to the left most.
Since **PLUS (+)** is forbidden, **XOR (^)** does the work of adding the bits but it doesn't take into account bits carried over from previous calculations.
Hence **AND (&)** is used to check any numbers will be carried over.
If they exist, they will be shifted left **LEFT SHIFT(<<)** to the correct position to be added on the next iteration.
Then the cycle continues until no others numbers need to be carried over.

#### Iterative solution

```js
const add = (x, y) => {
  while (y != 0) {
    const carry = x & y;
    x = x ^ y;
    y = carry << 1;
  }
  return x;
};
```

#### Recursive solution

```js
function add(x, y) {
  if (y == 0) return x;
  else return Add(x ^ y, (x & y) << 1);
}
```

A much better write up is available at [geeks for geeks](https://www.geeksforgeeks.org/add-two-numbers-without-using-arithmetic-operators/).
If you prefer videos you can check out the video below from **sBack to SWE**

{% include youtube.html id="qq64FrA2UXQ" %}

---
