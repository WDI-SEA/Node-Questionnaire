## Section 1

* What is Node and why would we use it?
- Node is a runtime environment - we use it for it non-blocking code to be run on our websites
* How do we initialize a folder for use with node?
- Move into the folder and run npm init
* What does `npm init` do?
- npm init creates our .json file that has the name verson description etc information
* What is a module and how does it relate to Node?
- modules encompass lots of code into a single area and allows us to do complex actions with far less code.
* I need to install a node module before I can use it. How can I install a node module so that it is accessable in javascript?
-npm install --save /*name of moduel*/
* How would I import a module into node?
var ____ = require('.....')
* When using require(), where is the module being pulled in from?
the module is being pulled from our node modules folder
* List some common modules we have used in node. There are at least two.
- path, ejs, body-parser


## Section 2

#### Express Setup
* What is Express and why would we want to use it?
-Express is a Node.js framework that allows the construction of server side javascript and to pull information from API's
* How do we import express into our node application?
- npm install --save express
* After Express is imported, we need to initialize it. We can save this to a variable so that we can reuse it later. What would this line of code look like?
- var ___ = require('express')
* What is app.use()? What does it do?
- is an example of middlewarethat helps handle functions like GET PUT POST
* What are static files? Why would we want a static file?
-Static files are possible our html but always our JS CSS and Image files.
* In contrast, what is the opposite of a static file? Why would we want a dynamic file being served?
- Dyanmic files are files we use when we want to be actively changing the information on the page - this would like updating any information from a backend or pulling information from api's through a request
* What would we pass into app.use() to serve up static files? *Hint: This one-liner doesn't really change.*
- app.use(express.static(path.join(__dirname, 'static')));
* What does the module body-parser do?
- it takes a string of information from an api call and turns it into a json object
* We need to tell express that we want to use body parser. Simplying requiring it isn't enough to activate it. How do we tell express we want to use body-parser?
- app.use(bodyParser.urlencoded({ extended: false }));


* If we use body-parser, we can retreive data from a POST (RESTful routing). How would we access this data from the 'req' object? `app.get('/', function(req, res) {})`
- app.get('/', function(req, res) { req.body })....pretty sure


#### EJS & Setup
* What is an EJS file?
- E is for effective! but ejs is embedded javascript - it allows us to generate html elemtns with the use of api calls on the fly.
* Is a EJS a static or a dynamic file?
-Dynamic
* Why would we want to use an EJS?
- we can create a responsive website that changes with user i/o
* Is EJS used by a templating engine?
- Pretty sure it is - the internet calls it a templating language..?
* If so, how do we tell express to use the ejs templating engine? *hint: app.use()*
- app.set('view engine', 'ejs')
* Write out the syntax tags for using javascript in EJS. If it helps, add 2+2 in this div tag: `<div></div>`
<% 2 + 2 %>
* We render ejs only when we are ready to send the page to the user. How do we render EJS for the browser? What is the function? *hint: this would be within the route (app.get(); )*
- app.get('path', function (req, res) { res.render('ejs file name'); });
* Following up on the last question, how do we pass data into EJS template? *hint: you will modify the previous answer*
-app.get('path', function (req, res) { res.render('ejs', { key: body?}); });
## Section 3

#### Routes
* req params vs req query
- req params comes from the url and req.query pulls from the query string.
* Write a route that utilizes req.params
- app.get('/:x/:y', function (req, res) {
* Adding onto the previous question: Inside the callback of the route, how can I access those parameters? *hint: thing back to /add/:x/:y/*
app.get('/:x/:y', function (req, res) {
var x = req.params.x;
 var y = req.params.y;
  res.send( x + y );
  });
* Identify the parts of this url: `localhost:3000/results?search=star+wars`
* What part of the url above matches the express route?
- /results
* What is the difference between using req.params and req.query
-
* How can I access the query key/value pairs inside the route callback?
-req.query.___



## Section 4

* What is RESTful Routing?
* What is CRUD?
* How to set your node/express app to stay open on a certain port?

#### Breakdowns
Identify the following parts:
`var express = require('express');`
- Tells node we will require express

`app.use(express.static(path.join(__dirname, 'static')));`
- tells our app to path to the static fold on / ?
`app.get('/', function(req, res){});`
- sets the route of our index/homepage?
`app.set('view engine', 'ejs');`
- tells the our node to use EJS for the view engine?
`app.use(bodyParser.urlencoded({ extended: false }));`
- Tells our node to use body-parser when recieves data from api calls.
