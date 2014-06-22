title: 'Custom APIs and Web Scraping for Science'
tags:
  - API
  - BeautifulSoup
  - DNA
  - flask
  - python
  - SNP
id: 569
categories:
  - 'Tech Tips'
date: 2014-01-31 15:16:49
---

So my team's most recent application, Helix, involved genome visualization. We integrated it with the [23andme](http://23andme.com) API, but still needed a way to find out interesting information about specific RSIDs (used by researchers and databases to refer to specific base pairs of DNA). By far the most useful and open source repository of genetic information is [SNPedia](http://snpedia.org), but I needed access to lots of information and to integrate calls to specific SNPs. Basically I needed an API. So being ever resourceful, I decided to make my own.

Tools for the task were an easy choice. I needed a small fast server that I could implement a web scrapper on. I have always wanted a reason to use [BeautifulSoup](http://www.crummy.com/software/BeautifulSoup/), but it's a Python library so I knew it would be easier to build a Python server to run the API endpoints. I chose [Flask](http://flask.pocoo.org/) because of its lightweight nature and how much it reminds me of a Node/Express server at times.

Thankfully there are some really good tutorials for both Flask and BeautifulSoup, my favorites (and the ones I referenced when I hit weirdness) were [Designing a RESTful API](http://http://blog.miguelgrinberg.com/post/designing-a-restful-api-with-python-and-flask) and [Website Scraping with BeautifulSoup](http://www.briancarpio.com/2012/12/02/website-scraping-with-python-and-beautiful-soup/). Both of these tutorials said a lot of things better than I could have myself.

For access to my SNPedia API and information on how to use it, [check out my project on GitHub](https://github.com/leaena/snp-api).