title: 'Clojure Makes Me Feel Stupid'
tags:
  - clojure
  - 'functional programming'
id: 700
categories:
  - 'Tech Tips'
date: 2014-06-16 23:58:50
---

...but I'm kinda in love with it. Thanks to a friend/coworker I'm cautiously dipping my toe into the world of "functional programming". I'm still not 100% certain I get the full gist of functional programming but, to my newb mind, I'd explain it as programming without consequences. Functions only depend on their inputs and external forces/state cannot muck with your function.

Apparently this makes it easier to predict what's going on, but I still have issues reading what I just wrote. Parenthesis all the way down dudes. Also prefix notation is technically useful, but warping my poor little brain.

So 1 + 1 in Clojure is actually written as (+ 1 1). Makes sense, right? Sorta, except for the years and years of basic math classes that NEVER LOOKED LIKE THIS. Oh my brain. But it's kinda cool that instead of 1 + 2 + 3 + 4 I only need to write (+ 1 2 3 4).

But seriously. This is a function in Clojure:

``` clojure
(defn adder
  [x y]
  (+ x y))

(adder 3 4) ;; 7
```

Wat? So the first line defines the function name. The second line is the parameters that you give to the function and then the last line adds those two parameters together. I then call the function on line 5 with the arguments 3 and 4 and then the semicolons denote comments and I use that do show what the output of the function is... 7.

As a super ridiculous aside. **Parameters** vs** arguments**? **Parameters** are the things that you define with the function. So x and y on line 2 are **parameters**. **Arguments** are what you pass to the function when you what to actually use it. So 3 and 4 on line 5 are **arguments**. Now go forth and be awesome!

So how do you be Clojure learners too? Currently I'm running through the [clojurebridge curriculum](https://github.com/ClojureBridge/curriculum) on my own.[ Clojure in 15 minutes](http://adambard.com/blog/clojure-in-15-minutes/) looks like a decent-y rundown of most of my syntax options. If you don't want to put anything on your system yet, or just want to mess around with the syntax, there's always [Try Clojure](http://tryclj.com/) which lets you program from your browser. And I've bookmarked [Clojure for the Brave and True](http://www.braveclojure.com/) mostly for the title, but I haven't really read any of it yet.
