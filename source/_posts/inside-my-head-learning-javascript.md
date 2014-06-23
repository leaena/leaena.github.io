title: 'Inside My Head: Learning JavaScript'
tags:
  - coderbyte
  - javascript
id: 473
categories:
  - Programming
date: 2013-11-30 13:06:16
---

I have had a very productive weekend so far (and it's only Saturday!). I am spending some of my day today going back through my easy [Coderbyte](http://coderbyte.com/) solutions and cleaning most of them up. I will also be adding in comments for most of the lines explaining my logic. So a lot of the files will look like this:

```javascript
function FirstReverse(str) {
  return str.split("")  //splits the string into an array of characters
            .reverse()  //reverses the array
            .join("");  //joins the array back into a string, with no space between the characters
}
```

This is actually a lot of fun for me. Now that we're getting into more abstract concepts like MVCs and servers it's nice to just go back and power through some JavaScript code and understand exactly what it's doing.

As always, you can find my [coderbyte solutions on GitHub](https://github.com/leaena/coderbyte) (I will be posting updates to it throughout the day), but I feel like I need to start adding a caveat, because of the amount of people who have said they found my blog looking for coderbyte solutions. Just staring at my code isn't going to make you understand JavaScript. You need to do it for yourself. If you're brand new to JavaScript, just seeing the cool tricks is not going to make you a programmer. I really recommend things like [Udacity](https://www.udacity.com/), [Codecademy](http://www.codecademy.com/) and other sites that talk about the fundamentals of comp sci/programming.
