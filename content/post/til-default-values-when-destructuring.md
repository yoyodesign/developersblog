---
title: "TIL: Default values when destructuring (ES6)"
date: 2018-11-12T16:29:34Z
publishdate: 2018-11-12
lastmod: 2018-11-12
draft: true
categories:
  - TIL
tags:
  - JavaScript
  - ECMAScript 6
---

Today I learnt that you can specify default values when destructuring arrays or objects.

I've been using desctructuring for a short time now, often using it to create variables from comma-separated values in strings.

{{<highlight js>}}
const arr = "calvin,mark,davis".split(",");
const [ first, middle, last ] = arr;

// first = "calvin"
// middle = "mark"
// last = "davis"
{{</highlight>}}

One day it occured to me that because this is variable assignment, perhaps default values would work here. One quick Google later, and here you have it:

{{<highlight js>}}
const arr = "calvin,mark".split(",");
const [ first, middle, last = "(unknown)" ] = arr;

// first = "calvin"
// middle = "mark"
// last = "(unknown)"
{{</highlight>}}

Brilliant right? One little "gotcha" is that default values are only used when the supplied value is `undefined`.

{{<highlight js>}}
const str = "calvin,mark,"; // Note the trailing comma!
const arr = str.split(","); // arr = [ "calvin", "mark", "" ] (Note the empty string!)
const [ first, middle, last = "(unknown)" ] = arr;

// first = "calvin"
// middle = "mark"
// last = "" (Uh oh!)
{{</highlight>}}

## Further reading

1. https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment#Default_values
