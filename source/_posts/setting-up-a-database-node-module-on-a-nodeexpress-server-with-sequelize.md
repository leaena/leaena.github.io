title: 'Setting Up a Database Node Module on a Node/Express Server with Sequelize'
tags:
  - express
  - javascript
  - nodejs
  - sequelize
id: 502
categories:
  - 'Tech Tips'
date: 2013-12-29 17:17:28
---

If you just need to get a node server up and running with very few lines of code then you hopefully already know about [Node](http://nodejs.org/)/[Express](http://expressjs.com/) (if you don't, the Express website has [a pretty good intro tutorial](http://expressjs.com/guide.html) and has [good documentation to get started serving up static assets](http://expressjs.com/api.html#app.use)). If you need all of that and to be able to route queries to a database quickly and easily then you might not know about the awesome power of [Sequelize](http://sequelizejs.com/).

If you haven't messed around with a ORM ([Object Relational Mapper](http://en.wikipedia.org/wiki/Object-relational_mapping), a program that maps your code to a database) before, Sequelize is a really straight forward one to start with.
```javascript
var voteTable = sequelize.define('vote', {
  video_id: Sequelize.STRING,
  timestamp: Sequelize.INTEGER,
  vote: Sequelize.INTEGER
});

voteTable.sync();
```

Once I had my server set up (and installed the sequelize dependencies). This was the line of code I needed to use to create a new table for my current group project. Sequelize automatically includes extra columns like unique id and created at/updated at timestamps (there are ways to tell it not to too).

The rest of the initial set up is easy too, but it's well documented over in the Sequelize docs. The fun part comes when you can start to make your database more modular. The first thing I did was to take out the actual username/password information from my database connection. I stored them as an object in a separate JavaScript file (so I could add it to [.gitignore](https://help.github.com/articles/ignoring-files) and not share my passwords with the world).

```javascript
//module.exports allows us to use this code in other places as a node module,
//we'll see it again when I make the database calls modular
module.exports = {
  database: 'database_name',
  username: 'username',
  password: 'secret_password',
  host: 'host_url',
  port: 5432,
  dialect: 'postgres', //obviously you don't have to use PostgreSQL
  native: true //required for Heroku Postgres (I'll cover that in another post)
};
```

I saved that snipped to a file called `db_config.js` at the root directory and then created my main database module in the subfolder `/controller/` called `database.js`. So to have access to the private config object, all I need to do is set up my dependencies, import the `db_config` file, and I can start using my config variables to connect to my database:

```javascript  
var Sequelize = require('sequelize');
var pg = require('pg').native; //again this line is specific to using a Postgres database
var config = require('../db_config');

var sequelize = new Sequelize(config.database, config.username, config.password, {
  host: config.host,
  port: config.port,
  dialect: config.dialect,
  native: config.native //Heroku Postgress again
});
```
Now between that code and my creating a table I have full access to a database, but now I need to get this all into my main `app.js` simple server I created with Node/Express. This is a super easy leap. First I create my functions to send and retrieve data in `/controller/database.js`:

```javascript
module.exports.createVote = function(req, res){
  //code to bundle up the created object and save it do the database
};

module.exports.getVotes = function(req, res){
  //code to find votes based on specific requests from the user
};
```

Now to have access to these functions (which are a part of the `database.js` node module, thanks to the module.exports object which is [a feature of Node](http://nodejs.org/api/modules.html#modules_the_module_object)) I only need to require `database.js` in my main server app and call the functions where I need them:

```javascript
var database = require('./controllers/database');

//many lines later
app.post('/votes', database.createVote);
app.get('/votes/:vidID', database.getVotes);
```

The `/votes/:vidID` is a [handy trick of Express](http://expressjs.com/api.html#app.param) to pass information to the server. The value gets attached to the `req.param.vidID` property so I can use it when I request specific information from the server. For example if I wanted to query for results from a video ID of 123 I would send a post request to `/votes/123` and then my `req.param.vidID === 123`.

One last trick, in Sequelize when you query the database you get back quite a few more rows than you might expect. When I query my `voteTable` (the one I only explicitly created three columns for?) I get back something that looks like this monster:

```javascript
{ dataValues:
     { video_id: '7QBgK0_RbkE', timestamp: 2, vote: 1, id: 192,
       createdAt: Sun Dec 22 2013 22:19:33 GMT-0800 (PST),
       updatedAt: Sun Dec 22 2013 22:19:33 GMT-0800 (PST) },
    __options:
     { timestamps: true, createdAt: 'createdAt', updatedAt: 'updatedAt',
       deletedAt: 'deletedAt', touchedAt: 'touchedAt', instanceMethods: {}, classMethods: {},
       validate: {}, freezeTableName: false, underscored: false, syncOnAssociation: true,
       paranoid: false, whereCollection: [Object], schema: null, schemaDelimiter: '',
       language: 'en', defaultScope: null, scopes: null, hooks: [Object], omitNull: false,
       hasPrimaryKeys: false },
    hasPrimaryKeys: false,
    selectedValues:
     { video_id: '7QBgK0_RbkE', timestamp: 2, vote: 1, id: 192,
       createdAt: Sun Dec 22 2013 22:19:33 GMT-0800 (PST),
       updatedAt: Sun Dec 22 2013 22:19:33 GMT-0800 (PST) },
    __eagerlyLoadedAssociations: [],
    isDirty: false,
    isNewRecord: false,
    daoFactoryName: 'votes',
    daoFactory:
     { options: [Object], name: 'votes', tableName: 'votes', rawAttributes: [Object],
       daoFactoryManager: [Object], associations: {}, scopeObj: {}, primaryKeys: {},
       primaryKeyCount: 0, hasPrimaryKeys: false, autoIncrementField: 'id', DAO: [Object] }
 }
 ```

And that's just **ONE** entry in the database! To fix that add an option to your sequelize query: `{raw: true}` so the query would look like:

```javascript
voteTable.findAll(query, {raw: true})
```

And one entry of output would be:

```javascript
{ video_id: 'T-D1KVIuvjA',
  timestamp: 2,
  vote: 1,
  id: 1,
  createdAt: Sat Dec 21 2013 14:55:42 GMT-0800 (PST),
  updatedAt: Sat Dec 21 2013 14:55:42 GMT-0800 (PST) }
```

That is enough database tricks for today. If you want to just stare at my code for a while to create &amp; retrieve votes from our database you can find [my gist here](https://gist.github.com/leaena/8174127) (with sanitized login info for the db_config). The real (still being modded by the team) code is [forked on my GitHub](https://github.com/leaena/videoheatmap). I have a few more of these in the works from my adventures slinging code and I hope to post a few more before Hack Reactor starts back up and I lose all free time again.
