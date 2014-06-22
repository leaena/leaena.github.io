title: 'Time Complexity in Algorithms'
tags:
  - 'big o'
  - Interview
  - knowledge
id: 457
categories:
  - Programming
date: 2013-11-29 17:09:20
---

Time complexity is a useful concept in programming. It's essential for job interviews, but beyond that to really be a good programmer you need to know how cumbersome your algorithm is going to be. For 10 items, something that takes 2 seconds per item is only 20 seconds, but what if you have a million items?

In general, time complexity is measured by how long it takes a number of items (n) to be processed. It is the relationship between the number of things you have to do and the work to be done. Something that takes the same amount of time no matter have much of it you have to do, would be constant time. If I had 10 items or 1 million it would only take me 2 seconds to process. On another extreme is something called the handshake problem. If you only have two people in a room they only have to shake one another's hands (one handshake). If you have 10 people, they each shake 9 other hands (55 handshakes total, we'll get to the math in a moment). This is quadratic time.

Here's a visual of the common programming time complexities:

![bigo](http://leaena.com/wp-content/uploads/2013/11/bigo.png)

&nbsp;

Lets start with **constant time** again. In programming, constant time is like deciding whether a number is even or odd:

     n % 2 = ? `</pre>
    This is just one expression. You run and you're done. It's always going to take a certain amount of time, no matter what n you give it. <span style="text-decoration: underline;">In big O notation we would write this as O(1).</span>

    Next, my favorite, as far as understanding goes. **Linear time.** In programming, linear time, is like running through a loop of n numbers and doing something.
    <pre>` for( var i = 0; i &lt; n; i++ ){
       do something..
     }`</pre>
    The more things ('n's) you have, the longer the algorithm is going to take. It's a 1:1 ratio. If 1 thing takes 1 second, 2 things are going to take 2 seconds. <span style="text-decoration: underline;">This is O(n).</span>

    **Quadratic time** is worse than linear time. It's like the handshake problem or in programming terms a for loop within a for loop. For each n we need to run through all the numbers 1 through n.
    <pre>` for( var i = 0; i &lt; n; i++ ){
       for( var j = 0; j &lt; n; j++ ){
         do something..
       }
     }`</pre>
    Each n thing is done n times. <span style="text-decoration: underline;">This is n * n or in big O terms O(n<sup>2</sup>).</span>

    **Logarithmic time** is all kinds of magic. It tapers off to a near constant for larger 'n's. This is possible because of the magic of halves. In a binary search tree there are only two options to descend, left (options lower than the current value) or right (options higher than the current value). Either choice will cut off roughly half of all the possible values. On the next level, you have the same choice, either you've found your value, or you go left or right, halving your options again.
    <pre>` while ( low &lt;= high ) {
       var mid = ( low + high ) / 2;
       if ( target &lt; list[mid] ){
         var high = mid - 1;    
       } else if ( target &gt; list[mid] ){
         var low = mid + 1;
       } else { break; }
     }

If you're constantly halving the amount of things you have to check, eventually you hit a roughly constant time for an n search. <span style="text-decoration: underline;">This is O(log n).</span>

_This post has been brought to you by [a forum post on time complexity](http://www.daniweb.com/software-development/computer-science/threads/13488/time-complexity-of-algorithm), bits and pieces of [the wiki article on time complexity](http://en.wikipedia.org/wiki/Time_complexity), and [this inspirational code class ad featuring my lead instructor from his Twitter days](https://www.youtube.com/watch?v=sh4O6DRs26M)._