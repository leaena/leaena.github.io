title: 'Recent Projects'
id: 529
date: 2014-01-11 14:22:40
---

# Helix

<iframe title="YouTube video player" width="640" height="390" src="http://www.youtube.com/embed/JbIL3asjZBs" frameborder="0" allowfullscreen=""></iframe>

*   Front End: Famo.us
*   Server: Node/Express
*   Database: Firebase
*   Web Scraper: Python/Flask

Helix is a mobile-ready web-based application which displays a traversable 3D visualization of a user's genome. We wanted to create a tactile experience for a user and connect them to their own genetic information in a way never before seen.

Primary responsibilities include writing a [Python/Flask API wrapper](https://github.com/leaena/snp-api) for SNPedia to find genetic traits ([blog post](http://leaena.com/2014/01/web-scraping-science/ "Custom APIs and Web Scraping for Science")) and writing a Node/Express server to query the 23andme API. The whole team also learned Famo.us, a private beta framework that made the beautiful visuals web and mobile friendly using just JavaScript.

# HeatVote

![](https://github-camo.global.ssl.fastly.net/1a3e93531a0e6bd168a849eb9f6587f49b44f1d6/687474703a2f2f692e696d6775722e636f6d2f30614759514f352e706e67)

[GitHub](http://github.com/leaena/videoheatmap) / [Live](http://heatvote.com/)

*   Front End: Backbone, Jade &amp; Styl preprocessors
*   Server: Node/Express
*   Database: PostgreSQL (Sequelize ORM)
*   Data Viz: D3

Heatvote allows users to vote on moments within a video. These votes are then aggregated into a heat map, where users can see where the most liked, least liked, and the most controversial moments occur before watching the video. All features are integrated into a standalone video player. There's no need to worry about APIs, compatibility issues, and you can host your own videos.

Primary responsibilities included Node server creation/API, Postgres/Sequelize database creation and connections, and creating the D3 visualizations. This project spawned a few blog posts as I learned, primarily from the server/database side ([Adding a Database Node Module](http://leaena.com/2013/12/setting-up-a-database-node-module-on-a-nodeexpress-server-with-sequelize/ "Setting Up a Database Node Module on a Node/Express Server with Sequelize") and [Using Heroku PostgreSQL](http://leaena.com/2013/12/cloud-postgresql-servers-with-heroku/ "Cloud PostgreSQL Servers with Heroku")) and one on [D3 and the magic powers of .rollup()](http://leaena.com/2014/01/d3-js-rollups/ "D3.js Rollups").