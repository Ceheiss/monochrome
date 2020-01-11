---
title: You Don't Need jQuery
description: A couple of learnings after transforming a jQuery app into Vanilla Javascript
header: You Don't Need jQuery
---

![](https://miro.medium.com/max/3200/1*k9eIDARy3rAEuyGjlpaTqg.png)

There was a time where jQuery was the lord of the land when it came to web apps and DOM manipulation. Today, thanks to the catch-up of web apis, the rise of modern JS libraries and Frameworks, and the fact that modern browsers have a much more consistent implementation of Javascript than before, have rendered the need for jQuery in a massive way (although there are a TON of websites that currently use it).

![](https://f0.pngfuel.com/png/1007/564/java-script-logo-png-clip-art.png)
As sidenote, is it me, or before people prefered to write **JavaScript** in UpperCamelCase, and know with the fancy -semi offical- black and yellow logo people prefer to write **Javascript**? Anyway, back to the post.
![](https://upload.wikimedia.org/wikipedia/commons/6/6a/JavaScript-logo.png)

"The word on the street" on jQuery is so strong, that there even is a whole repo/website called ["You might not need jQuery"](http://youmightnotneedjquery.com/) by [@adamfschwartz](http://twitter.com/adamfschwartz) and [@zackbloom](http://twitter.com/zackbloom) with the purpose of showing how simple is today to do things with native tools, and how we should think twice before adding jQuery as a dependency (and if we do, do it informed).


Thanks to an exercise deviced by [Gordon Zhu](https://twitter.com/gordon_zhu?lang=en), I got to experience this myself. I recently refactored the [jQuery Todo MVC](https://github.com/tastejs/todomvc/blob/master/examples/jquery/js/app.js) by stripping all use of jQuery in the app, one method at a time. Obviously, the idea was to keep the same functionality. My result is [here](https://glitch.com/edit/#!/no-jquery-here?path=public/js/app.js:183:9).


My code has **222 lines vs the 197 that the original with jQuery has**, so trading 25 extra lines of code for a whole library seems desirable in my opinion (probably if I went through it again, I could make it more compact and elegant, but the idea was just to safely remove jQuery). So yes, in my experience, you might not need jQuery.


### Learnings


Besides the point of jQuery not being super necessary today (although I hardly ever use it, I think that doing this exercise was the time I've been exposed the most to it) this exercise was very good as a forced way of reading source code. In order to refactor it, having an understanding of the code in the first place is quite relevant.


I also got a lot of practice with Chrome's debugger. I constantly stopped the runtime to take a look at the current state of things, and get a better look at how the methods were working. 


Using things like `document.getElementById("someId")` is very common, but I also got to play around with other methods I don't frequently use like `e.target.closest("li")` that finds the closest element with a particular tag (li) in this case, of the element that was targeted throw a particular event. Also the use of `getAttribute` and `setAttribute` was cool and powerful (I used it for custom data attributes).


Last learning is: damn getting the correct value of `this` is still a tricky bussiness for me (specially when working with nested DOM elements). There are plenty of times I make a -in my mind- good argument regarding the value of `this`, just to be followed by a nonchalant, yer recurring in my programming journey, **"WTF"**.
