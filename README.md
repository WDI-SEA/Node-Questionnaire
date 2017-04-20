## Section 1

* What is Node and why would we use it?
    -node allows us to handle server commands (back end) in javascript
    -use data users input in forms
    -handle databases
    -multiple users
    -private data

* How do we initialize a folder for use with node?
    -npm init

* What does `npm init` do?
    -it creates a server from the files in the folder
    -it guides you through making a package.json file that houses all your details about the server.

* What is a module and how does it relate to Node?
    - a module is a package that can contains additional commands/features to use in node

* I need to install a node module before I can use it. How can I install a node module so that it is accessable in javascript?
    - npm install --save modulename

* How would I import a module into node?
    - require("module"); (save it to a variable)

* When using require(), where is the module being pulled in from?
  - node_modules folder

* List some common modules we have used in node. There are at least two.
  -ejs, body-parser, request, express

## Section 2

#### Express Setup
* What is Express and why would we want to use it?
  -express is a module that simplifies writing server response/request and routing handlers. we didn't do a ton of stuff without express so i don't really know much about plain node

* How do we import express into our node application?
  - var express = require('express');

* After Express is imported, we need to initialize it. We can save this to a variable so that we can reuse it later. What would this line of code look like?
    -var app = express();

* What is app.use()? What does it do?
    -app.use() tells the app we are going to be using certain files or folders etc

* What are static files? Why would we want a static file?
    -static files are what we have been making until now. they won't be changed in the browser by back end work
    - we want them when we know we won't need to render them dynamically

* In contrast, what is the opposite of a static file? Why would we want a dynamic file being served?
    - dynamic files allow for one file to be used in many ways. for example, if we have a bunch of users on a site we would want each of their home pages to look similar but only show their information. it would be tedious to create a new static page for each user, especially if you have a big user base

* What would we pass into app.use() to serve up static files? *Hint: This one-liner doesn't really change.*
  - app.use(express.static(path.join(__dirname, "static")));
      also would need to require('path');

* What does the module body-parser do?
    - this allows us to access different parts of the body we received in the users request, example, access different input fields in a form

* We need to tell express that we want to use body parser. Simplying requiring it isn't enough to activate it. How do we tell express we want to use body-parser?
    - app.use(bodyParser.urlencoded({ extended: false }));

* If we use body-parser, we can retreive data from a POST (RESTful routing). How would we access this data from the 'req' object? `app.get('/', function(req, res) {})`
    - req.body['propertyname'] or
    - req.body.propertyname


#### EJS & Setup
* What is an EJS file?
    - it is similar to HTML but lets us add code tags where we want the HTML to be dynamic and the browser won't show anything but what is being evaluated in the back end.

* Is a EJS a static or a dynamic file?
    - dynamic

* Why would we want to use an EJS?
    - we can make a template and only change the parts that need to be changed based on different data pieces

* Is EJS used by a templating engine?
    - yes, the view engine

* If so, how do we tell express to use the ejs templating engine? *hint: app.use()*
    - app.use("view engine", "ejs");

* Write out the syntax tags for using javascript in EJS. If it helps, add 2+2 in this div tag:
    - `<div><%= 2 + 2%> </div>`
* We render ejs only when we are ready to send the page to the user. How do we render EJS for the browser? What is the function? *hint: this would be within the route (app.get(); )*
    - app.render("name_of_ejs_file", {data you want to be used in tempate file as a key-value pair});

* Following up on the last question, how do we pass data into EJS template? *hint: you will modify the previous answer*
    - it is passed as an object {} where the keys are the data as you would call it in the ejs template and the values are the actual data you are sending into the ejs template

## Section 3

#### Routes
* req params vs req query
    - params are in the route and noted with colons. /path/:nameofparam. accessed by req.params.nameofparam
    - req queries are appened onto the route by the browser??form?? on submit and can be accessed in the route handler by using req.query.nameofqueryfromform

* Write a route that utilizes req.params
    - app.get("/dinner/:food", function(req, res){
        res.send("we are having " + req.params.food + "for dinner tonight");
    });

* Adding onto the previous question: Inside the callback of the route, how can I access those parameters? *hint: thing back to /add/:x/:y/*
    - i did that above

* Identify the parts of this url: `localhost:3000/results?search=star+wars`
    - localhost:3000
          => telling the browser this port is where the server is
    - /results
          => go to this route on the server
    -?search=
          => this is our query parameter
    -star+wars
          =>  this is the value of the query parameter

* What part of the url above matches the express route?
    - "/results"
* What is the difference between using req.params and req.query
    - i had a good thought in class but i forgot it...
    - the gist of it was that using req.query is more flexible because you have to know how many req.params you have where as you can pass as many req.queries as you need in the object

* How can I access the query key/value pairs inside the route callback?
    - req.query.property or req.query[property]


## Section 4

* What is RESTful Routing?
    - honestly im not really sure other than that it has to do with defining a path and an action like show or edit or delete (but using HTTP verbs) and putting that into a route handler

* What is CRUD?
    - CREATE READ UPDATE DESTROY - main 4 verbs for what you can do to information
* How to set your node/express app to stay open on a certain port?
    app.listen(port#);

#### Breakdowns
Identify the following parts:
`var express = require('express');`
  -this is importing the module express and setting it to a variable

`app.use(express.static(path.join(__dirname, 'static')));`
  - this is telling the app that our static files are in the outlined directory(commonly named "static") and we can use them. the filepath is made generic for cross-OS compatibility

`app.get('/', function(req, res){});`
  - this is telling the app to use the GET method on the root, and whatever is in the function will occur when we a request is sent via GET at that root

`app.set('view engine', 'ejs');`
  - our views (templates) will be in ejs format

`app.use(bodyParser.urlencoded({ extended: false }));`
  - use the body-parser module. the urlencoded part prevents it from failing since it has been depreciated?? and this is the work around
