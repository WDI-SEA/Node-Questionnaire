## Section 1

* What is Node and why would we use it?


 A: Node is a runtime environment for JS. It allows us to create applications where both the client and serve use JS. 


* How do we initialize a folder for use with node?

 A: npm init 


* What does `npm init` do?

 A: Allows you to start a project (JSON) and specify a file to use 


* What is a module and how does it relate to Node?

 A: A system that allows code written in a file to be exported 



* I need to install a node module before I can use it. How can I install a node module so that it is accessable in javascript?

 A: npm install --save express
touch 'index.js' 


* How would I import a module into node? 

 A: declare a variable = to a function(path)
declare a variable = require('./YOUR PATH') 


* When using require(), where is the module being pulled in from?

 A: from your exports project folder (module.exports) 



* List some common modules we have used in node. There are at least two.

A:
 
express and request


## Section 2

#### Express Setup
* What is Express and why would we want to use it?

 A: Import a web app server. To create web apps with Node 


* How do we import express into our node 
application? 

 A: npm install --save express
 var express = require('express')


* After Express is imported, we need to initialize it. We can save this to a variable so that we can reuse it later. What would this line of code look like?

 A: var app = express() 

* What is app.use()? What does it do?


 A: Gives us a route to files




* What are static files? Why would we want a static file?

 A: Contains the same built content you load a page. html, css, JS



* In contrast, what is the opposite of a static file? Why would we want a dynamic file being served?

A: For users experiences. For an example, you are buying something on Amazon and the cart is updated with a subtotal without having to refresh the page


* What would we pass into app.use() to serve up static files? *Hint: This one-liner doesn't really change.*

A: A: Gives us a route 
app.use(express.static(path.join__dirname + 'PATH_NAME')); 


* What does the module body-parser do?

A: Body-parser is a piece of express middleware that reads a form’s input and stores it as a javascript object accessible through
“req.body”.


* We need to tell express that we want to use body parser. Simplying requiring it isn't enough to activate it. How do we tell express we want to use body-parser?

A:
npm install --save body-parser
var bodyParser = require('body-parser')

app.use(bodyParser.urlencoded({extended: false}));


* If we use body-parser, we can retreive data from a POST (RESTful routing). How would we access this data from the 'req' object? `app.get('/', function(req, res) {})`

A: app.get('/', function(req ,res) {
	req.body('paramenters sent from the client')
})


#### EJS & Setup
* What is an EJS file?
A: Embeded JS. Uses <%%> control tags. html embeded with JS

* Is a EJS a static or a dynamic file?
A: Dynamic

* Why would we want to use an EJS?
A: EJS is a template that we can set specific tags to change dynamically for users during interactions


* Is EJS used by a templating engine?
A: yes


* If so, how do we tell express to use the ejs templating engine? *hint: app.use()*

A:app.use('view engine', EJS)

* Write out the syntax tags for using javascript in EJS. If it helps, add 2+2 in this div tag: `<div></div>`
A: <div <%2+2%> </div>


* We render ejs only when we are ready to send the page to the user. How do we render EJS for the browser? What is the function? *hint: this would be within the route (app.get(); )*

A:
app.render('PATH', function(error, response, body) {
	code here
})

* Following up on the last question, how do we pass data into EJS template? *hint: you will modify the previous answer*

A:app.render('PATH', function(error, response, body) {
	res.render('/'{objects})
})

## Section 3

#### Routes
* req params vs req query

A:req params = creates routes with different variables that is pulled out by express
req query = contains the URL query parameters


* Write a route that utilizes req.params

A: app.get("/posts/:id", function(req, res)) 


* Adding onto the previous question: Inside the callback of the route, how can I access those parameters? *hint: thing back to /add/:x/:y/*

A:  req.params.x
	req.params.y
	app.send(x+y)


* Identify the parts of this url: `localhost:3000/results?search=star+wars`

A: 

localhost:3000/ = the server you are listening for

results = the route your server is going to

?search= = query id

star+wars = query movie title parameter


* What part of the url above matches the express route?


A: /results

* What is the difference between using req.params and req.query

A: req.params are paths of the url, req.query are query parameters. Anything searched


* How can I access the query key/value pairs inside the route callback?

A: req.query[]

## Section 4

* What is RESTful Routing?
A: Representational State Transfer is a software to create scalable web services


* What is CRUD?

A: Create Read Update Destroy. your verbs

* How to set your node/express app to stay open on a certain port?

A:app.listen(port)

#### Breakdowns
Identify the following parts:
`var express = require('express');`
A:
declared a variable to require 'express'
express being the framework for Node



`app.use(express.static(path.join(__dirname, 'static')));`

A: app.use is talking to express to access the static folder and defaulting to an html file


`app.get('/', function(req, res){});`

A: .get responds to a GET method route 


`app.set('view engine', 'ejs');`


A: loads the template file ejs once to be referenced multiple times


`app.use(bodyParser.urlencoded({ extended: false }));`
 
 A: onced body-parser is installed and declared as a variable you can parse data called from the web. 






