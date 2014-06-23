title: 'D3.js Rollups'
tags:
  - d3
  - 'data sci'
  - javascript
id: 498
categories:
  - 'Tech Tips'
date: 2014-01-04 18:28:17
---

Do you have all the data and none of the visuals? Do you just want a pretty, fast way to compare lots of data that centers around maybe just a handful of moments?

[D3.js](http://d3js.org/) can help you tame all of your data and `d3.rollup` is especially useful if you have lots of data that you need to combine into just a couple of data points. All it takes is a couple of (pretty long) lines of code and you will have an awesome visual that's very customizable.

Lets start with a really straightforward example of a rollup. In all of these examples, I'm using code straight from my HeatVote project, which requires me to pull voting data from our server API that I receive as a [JSON blob](http://jsonblob.com/). Here's an example entry:
```javascript
{ video_id: 'T-D1KVIuvjA',
  timestamp: 2,
  vote: 1,
  id: 1,
  createdAt: Sat Dec 21 2013 14:55:42 GMT-0800 (PST),
  updatedAt: Sat Dec 21 2013 14:55:42 GMT-0800 (PST) }
```

Now obviously there are a bunch of these, and technically there are easier ways to do this, but to show off the structure of a rollup, lets count how many entries we had in our database using a d3 rollup!

```javascript
var total = d3.nest()
  .rollup(function(d){
    return d.length;
  })
  .entries(data);
```
Remember, `data` here is my array of JSON entries, so in our rollup function the `d` is just shorthand for all of the data. This isn't a very interesting example though, lets take a look at something that really shows off the beauty of a d3 rollup.

```javascript
var averages = d3.nest()
  .key(function(d) {
    return d.timestamp;
  })
  .sortKeys(d3.ascending)
  .rollup(function(d){
    return d3.mean(d, function(g) {
      return +g.vote;
    });
   })
   .entries(data);
```

Now there is a **lot** going on in this very compact few lines, so well go through them one by one, but the result is that `averages` is equal to an array of objects with the properties `key` (that is equal to each unique timestamp) and `value` (that is equal to the mean of all votes at that timestamp).

So lets break it down:

*   `.key(...)` is just used to tell the function what our keys are, only grabbing unique values of that property.
*   `.sortKeys` is just a prettiness thing, it sorts my keys into an order (when they're pulled off the server the only order is by the time they were created on the database).
*   and finally our lovely `.rollup(...)`. Now instead of d being an array of the whole data, it's now an array of only the data for each individual key (so all of the data with the same timestamp). The inner function `d3.mean` takes a specific property from all of the data for each key and averages them up.
And that, is d3 rollup in a nutshell, it's really lovely at coercing relationships out of your raw data and you can obviously do a lot more with it that just averaging things. The [d3 nest docs](https://github.com/mbostock/d3/wiki/Arrays#wiki-d3_nest) are probably the next best place to look to get your hands dirty (.rollup is a property of nest).
