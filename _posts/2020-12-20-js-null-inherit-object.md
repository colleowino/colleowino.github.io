---
layout: post
title: "Today I Learned #4: Null type does not inherit from Object"
date: 2020-12-02 9:14:00 pm
tags: javascript codewars coding lessons
categories: coding
author: "colleowino"
header-img: /img/codewars.jpg
---

This is drawn from the challenge [You're not my type](https://www.codewars.com/kata/57157a7c2ad76331360002d0).
Which requires returning members of an array that are the type defined in the argument. The solution has to work for both objects and primitive types.

According to MDN documentation [JavaScript data types and data structures](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures)
Null is the only type that doesn't inherit from Object. So that means you have to take that into account as an edge case.

```
Six Data Types that are primitives, checked by typeof operator:
undefined : typeof instance === "undefined"
Boolean : typeof instance === "boolean"
Number : typeof instance === "number"
String : typeof instance === "string"
BigInt : typeof instance === "bigint"
Symbol : typeof instance === "symbol"

Structural Types:
Object : typeof instance === "object".
Special non-data but Structural type for any constructed object instance also used as data structures: new Object, new Array, new Map, new Set, new WeakMap, new WeakSet, new Date and almost everything made with new keyword;
Function : a non-data structure, though it also answers for typeof operator: typeof instance === "function". This is merely a special shorthand for Functions, though every Function constructor is derived from Object constructor.

Structural Root Primitive:
null : typeof instance === "object". Special primitive type having additional usage for its value: if object is not inherited, then null is shown;44

```

#### Challenge solution

```js
Array.prototype.ofType = function (type) {
  //code me
  return this.filter((x) => {
    return (
      x instanceof type || (x != null && typeof x === type.name.toLowerCase()) //x.constructor == type  works just as well
    );
  });
};
```

---
