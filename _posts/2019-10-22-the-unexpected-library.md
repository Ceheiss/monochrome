---
title: The Unexpected Library
description: How rewriting existing methods for TDD practice led to an unusual library.
header: The Unexpected Library
---

Sometimes unexpected things happen. For example, today I planned on reading about TDD and Unit Testing, and later blogging it. Yet, here I am, and -spoiler alert- this isn’t a post about TDD… at least not conceptually.


As a mean of practicing Test Driven Development, and familiarize with beautiful array methods such as map, reduce, indexOf, reverse and other goodies, I started a repository you can ["check out here"](https://github.com/Ceheiss/testing-tests). The idea is not my original but comes from the curriculum ["Gordon Zhu"](https://twitter.com/gordon_zhu?lang=en) put together in ["Watch and Code"](https://watchandcode.com/). Anyhow, back to my point.\


So I was working on the Array.reverse method when I noticed that although reversing the order of the elements in an array is very strict forward, I had no idea how to reverse an iterable object that looks like this:


```javascript
	{0: 'a', 1: 'b', 2: 'c', index: 3};
```
 
 
I talked about this with my mentor Wolfram, and he suggested that I could use Array.from() to make that object an array and later use it in my reverse method. Somehow that felt like cheating, so he suggested I build my own Array.from and then use it here. Hell, why not, I’m already doing this so I built the function.


### The Library
 
 
So when I finished writing the basics of Array.from() I noticed it accepted a callback as second argument to map the newly formed array. Dang it, I wasn’t going to use the map function to do it (the whole reason I was creating my version if Array.from() was to not used these functions), but I realized I had built a map replica before. I decided to take a bunch of functions I already replicated and called the file: rewriteLibrary.js I used my map in the Array.form() and worked perfectly.
