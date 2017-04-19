## Section 1

* What is Node and why would we use it?
* How do we initialize a folder for use with node?
* What does `npm init` do?
* What is a module and how does it relate to Node?
* I need to install a node module before I can use it. How can I install a node module so that it is accessable in javascript?
* How would I import a module into node? 
* When using require(), where is the module being pulled in from?
* List some common modules we have used in node. There are at least two.


## Section 2

#### Express Setup
* What is Express and why would we want to use it?
* How do we import express into our node application? 
* After Express is imported, we need to initialize it. We can save this to a variable so that we can reuse it later. What would this line of code look like?
* What is app.use()? What does it do?
* What are static files? Why would we want a static file?
* In contrast, what is the opposite of a static file? Why would we want a dynamic file being served?
* What would we pass into app.use() to serve up static files? *Hint: This one-liner doesn't really change.*
* What does the module body-parser do?
* We need to tell express that we want to use body parser. Simplying requiring it isn't enough to activate it. How do we tell express we want to use body-parser?
* If we use body-parser, we can retreive data from a POST (RESTful routing). How would we access this data from the 'req' object? `app.get('/', function(req, res) {})`

#### EJS & Setup
* What is an EJS file?
* Is a EJS a static or a dynamic file?
* Why would we want to use an EJS?
* Is EJS used by a templating engine?
* If so, how do we tell express to use the ejs templating engine? *hint: app.use()*
* Write out the syntax tags for using javascript in EJS. If it helps, add 2+2 in this div tag: `<div></div>`
* We render ejs only when we are ready to send the page to the user. How do we render EJS for the browser? What is the function? *hint: this would be within the route (app.get(); )*
* Following up on the last question, how do we pass data into EJS template? *hint: you will modify the previous answer*

## Section 3

#### Routes
* req params vs req query
* Write a route that utilizes req.params
* Adding onto the previous question: Inside the callback of the route, how can I access those parameters? *hint: thing back to /add/:x/:y/*
* Identify the parts of this url: `localhost:3000/results?search=star+wars`
* What part of the url above matches the express route?
* What is the difference between using req.params and req.query
* How can I access the query key/value pairs inside the route callback?



## Section 4

* What is RESTful Routing?
* What is CRUD?
* How to set your node/express app to stay open on a certain port?

#### Breakdowns
Identify the following parts:
`var express = require('express');`


`app.use(express.static(path.join(__dirname, 'static')));`

`app.get('/', function(req, res){});`

`app.set('view engine', 'ejs');`

`app.use(bodyParser.urlencoded({ extended: false }));`

