title: 'Advanced Filtering with Angular.js'
tags:
  - angular
id: 500
comment: false
categories:
  - 'Tech Tips'
date: 2014-02-06 16:49:28
---

Everyone (who's used angular or seen an angular tutorial) has seen the awesome realtime angular search. This is used with a filter property, but there are more complex things you can use with filtering. On my Hack Reactor [hackathon project](http://github.com/leaena/blogmark) I used filtering for just about everything. From picking out individual objects to finding just the right combinations and I learned some awesome tricks and some pitfalls to avoid.

One of the coolest things you can do is filter by lots of things together. The filter ends up looking a lot like a JavaScript object:

```javascript
filter:{TEXT: text, notes: noted, category: category}
```

They way this works the best is if you have a number of searches all on one page to pull together. Say a regular text search (`text` above) that needs to interact with a drop down menu filter (`category`). Just throw all the variables into one object and filter on that.

Another neat thing you can do is filter by IDs. For example, if you want to have individual pages for each item, you can normally just call to it based on the $index of that item. But what if you have searched and filtered your list of data into a more manageable grouping? Index doesn't work! It's pulling the index of the new filtered list and not the actual index that data point has in the entire data structure.

My fun work around for this was to send the object that you had selected to a function within my Angular controller for that page and find the data that way.

```javascript
$scope.add = function(website){
    $rootScope.selected = $rootScope.selected || [];
    if($rootScope.selected.indexOf(website) === -1){
        $rootScope.selected.push(website);
    }
};
```

Of course this requires something in the `$rootScope`, but that also benefited me because I wanted to have access on a separate page to all of the data points a user chose. That way I could fill out a detailed report of the chosen bookmarks with user defined notes all on one screen.
