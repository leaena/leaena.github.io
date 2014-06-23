title: 'Solver of Problems'
tags:
  - coderbyte
  - javascript
id: 202
categories:
  - Programming
date: 2013-08-12 22:20:42
---

I figured it out! Sort of on my own, sort of studying how others had "solved" it in different languages (a few of the "solutions" didn't seem to work). Array Addition I is now my bitch. Also the next 10 easy problems from [Coderbyte](http://coderbyte.com) are on my [GitHub](http://github.com/leaena/coderbyte). 6 more to go (well 7 actually, I gave up on ArithGeo, but the solving of Array Addition gives me hope that I will figure it out tomorrow). **Problem description:** Using the JavaScript language, have the function ArrayAdditionI(**arr**) take the array of numbers stored in **arr** and return the string **true** if any combination of numbers in the array can be added up to equal the **largest number** in the array, otherwise return the string **false**. For example: if **arr** contains [4, 6, 23, 10, 1, 3] the output should return **true** because 4 + 6 + 10 + 3 = 23\. The array will not be empty, will not contain all the same elements, and may contain negative numbers. **And my solution:** (basically grabs the largest value out of a provided array and it runs through all the possible sum combinations of all the other numbers to see if one of those sums equals the largest values)
```javascript
    function ArrayAdditionI(arr) {
      arr.sort(function(a,b){return a - b})
      var largest = arr.pop();
      var sum = 0;

      for (var i = 0; i &amp;lt; arr.length; i++){
        sum += arr[i];

        for (var j = 0; j &amp;lt; arr.length; j++){
          if (i != j) {
            sum += arr[j];
            if (sum == largest) {
              return true;
            }
          }
        }

        for (var k = 0; k &amp;lt; arr.length; k++) {
          if (i != k) {
            sum -= arr[k];
            if (sum == largest) {
              return true;
            }
          }
        }

        sum = 0;
      }

      return false;
    }
```