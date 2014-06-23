title: 'I Did All the Things'
tags:
  - coderbyte
  - javascript
id: 213
categories:
  - Programming
date: 2013-08-15 23:38:14
---

Finally finished up the last 6 [Coderbyte](http://coderbyte.com) challenges. I had planned to finish them on Tuesday but I got home from an all day work "thing", took a shower and passed out. On Wednesday I had a much-needed pajama party with relatives and watched some old Downton Abbey (season 2, Matthew just got the use of his legs again &#42;sniff&#42;). The last 6 challenges were plagued with me forgetting what variable type I was juggling. Most of my errors were fixed by type conversions. I still believe nothing was as hard as that stupid [Array Addition](https://github.com/leaena/coderbyte/blob/master/17arrayadditioni.js). Everything else I was able to piece together on my own, but I don't think I would have ever solved that one without a bit of a nudge from other coders. I think I need more math logic. I should probably take a class or find a good book (oh the torture) on the subject. I plan on reading through [Professional JavaScript for Web Developers](http://www.amazon.com/Professional-JavaScript-Developers-Nicholas-Zakas/dp/1118026691) over the weekend and maybe running through all 26 again (no peeking!) on Sunday as prep for Tuesday's interview. After I get in (I need to tone down the bravado), I want to go back and try the harder challenges. Wish me luck on everything! Also, as always, my [Github](http://github.com/leaena/coderbyte/) with the updates. My favorite code this time was MeanMode which checks to see if the mean and the mode of an array are the same. It's probably my favorite because I literally couldn't remember what the mode of an array was and had to look up remedial math stuffs. That was humbling.
```javascript
    function MeanMode(arr) {  
      var mode;  
      var modeCount = [];  
      var count = 0;  
      var sum = 0;  

      for (i = 0; i &amp;lt; arr.length; i++) {  
        sum += arr[i];

        if(!modeCount[arr[i]-1]){
          modeCount[arr[i]-1] = 0;  
        }

        modeCount[arr[i]-1] += 1;  
      }  
      for(i = 0; i &amp;lt; modeCount.length; i++) {

        if(modeCount[i] &amp;gt; count) {  
          mode = i+1;  
          count = modeCount[i];  
        }  
      }

      var mean = sum/arr.length;

      if (mean === mode) {  
        return 1;  
      } else {  
        return 0;  
      }  
    }  
```
