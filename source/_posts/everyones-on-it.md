title: 'Everyone''s On It'
tags:
  - geeky
  - ruby
  - work
id: 150
categories:
  - Programming
date: 2013-08-07 19:42:10
---

I just made something! For the first time ever I made a stupid little ruby program to do something that a PivotTable was giving me fits over at work. I had a spreadsheet like so:

![Spreadsheet of Traits](http://res.cloudinary.com/leaena/image/upload/v1391709246/Screen-Shot-2013-08-07-at-7_37_57-PM_jg1m72.png)

But what I really needed was a text file that I could print and hand out to people like so:

![Formatted Strengths](http://res.cloudinary.com/leaena/image/upload/v1391709242/Screen-Shot-2013-08-07-at-7_38_22-PM_vvikzc.png)

And I did it with the power of Ruby! I was so proud of myself. I've never taken a real world problem (from my work no less) and made a tiny bit of code do exactly what I want it to. It just adds to my love of coding.

```javascript
require 'csv'

contents = CSV.open "strengths.csv", headers: true, header_converters: :symbol
File.open("out.txt", 'w') do |f|
  contents.each do |row|
    headers = contents.headers
      name = row[0]
    strength = {}
      i = 1
    while i &lt; row.length
      if row[i]
        strength[(row[i].to_i)] = i
      end
      i += 1
    end
    f.write("#{name} \n")
    stren = strength.sort_by { |k, v| k }

    stren.each do |k,v|
      f.write("\t #{headers[v].to_s.capitalize} \n")
    end
    f.write("\n")
  end
end
```

And yes, those are my StrengthsFinder top 5 in the second picture. Everyone at work had to do them and I think mine are very accurate.
