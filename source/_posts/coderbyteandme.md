title: 'Coderbyte and Me'
tags:
  - coderbyte
  - hackreactor
  - javascript
id: 193
categories:
  - Programming
date: 2013-08-11 21:37:46
---

I've been practicing my JavaScript for the [HackReactor](http://hackreactor.com) interview on the 20th (wish me luck by the way). They sent around an email saying to be prepared so you didn't have to reschedule (I'm suddenly glad I couldn't get an appointment straightaway). They recommended being able to get through all the easy challenges on[ Coderbyte](http://coderbyte.com) in &lt; 5 minutes. Yikes? Surprisingly not. I'm having a lot of fun.

There are a couple things I've obviously forgotten (I had to look up the regex to keep only alpha characters, I suck at regex), but I'm pretty fast. I'm also realizing just how not amazing I am at the trickier puzzles. There are one or two in there that I still don't understand, even after I caved and looked up how others solved them (Array Addition I, I'm glaring at you).

There are 26 easy challenges. I've decided to run through at least 10 a day, so I finished the first 10 today and uploaded them to my [GitHub](https://github.com/leaena/coderbyte). My favorite one so far was the TimeConvert, which took a number (e.g. 126) and converted to the amount of hours and minutes (e.g. 2:6). I could have made it prettier by added a preceding 0 in the minutes, but the goal of these is speed and the instructions didn't ask for that pretty extra. This was my favorite because I just have this weird love for modulus. The code to solve it:
```javascript
function TimeConvert(num) {
  var minutes = num % 60;
  var hours = parseInt(num/60);

  return "" + hours + ":" + minutes;
}
```
