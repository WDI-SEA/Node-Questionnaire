## Section 1

* What is Node and why would we use it?
It's a framework based on javascript and it allows us to create web apps.

* How do we initialize a folder for use with node?
npm init

* What does `npm init` do?
creates the json file that houses information about our app.

* What is a module and how does it relate to Node?
modules add functionality to node, you download them and then require them in the file to attach them.

* I need to install a node module before I can use it. How can I install a node module so that it is accessable in javascript?
npm install --Save <module name>

* How would I import a module into node?
with the require call

* When using require(), where is the module being pulled in from?
from the modules folder

* List some common modules we have used in node. There are at least two.
ejs,request,body-parse,express

## Section 2

#### Express Setup
* What is Express and why would we want to use it?
It's a framework to run with node to make ease of creating web apps

* How do we import express into our node application?
nmp install --save express

* After Express is imported, we need to initialize it. We can save this to a variable so that we can reuse it later. What would this line of code look like?
var express = require('express');
var app = express();

* What is app.use()? What does it do?
app.use() calls on express to give functions in node.

* What are static files? Why would we want a static file?
static files are files that don't change through manipulation. We want these files because they don't change, images, css, and javascript files are good examples.

* In contrast, what is the opposite of a static file? Why would we want a dynamic file being served?
dynamic files are opposites, we want them because they provide updatable and active pages.

* What would we pass into app.use() to serve up static files? *Hint: This one-liner doesn't really change.*
app.use(express.static(path.join(__dirname, 'static')));

* What does the module body-parser do?
It allows us to parse body requests easier.

* We need to tell express that we want to use body parser. Simplying requiring it isn't enough to activate it. How do we tell express we want to use body-parser?
app.use(bodyParser.urlencoded({ extended: false }));

* If we use body-parser, we can retreive data from a POST (RESTful routing). How would we access this data from the 'req' object? `app.get('/', function(req, res) {})`
app.get('/games', function(req, res) {
    var games = getGames();

    res.render('games-index', { games: games });
});


#### EJS & Setup
* What is an EJS file?
a templating file.

* Is a EJS a static or a dynamic file?
dynamic

* Why would we want to use an EJS?
to make dynamic pages where we can update given retrieved data

* Is EJS used by a templating engine?
yes

* If so, how do we tell express to use the ejs templating engine? *hint: app.use()*
app.set('view engine', 'ejs');

* Write out the syntax tags for using javascript in EJS. If it helps, add 2+2 in this div tag: `<div></div>`
<% %>

* We render ejs only when we are ready to send the page to the user. How do we render EJS for the browser? What is the function? *hint: this would be within the route (app.get(); )*
     res.render('results', { movies: data.Search });

* Following up on the last question, how do we pass data into EJS template? *hint: you will modify the previous answer*
     res.render('results', { movies: data.Search });

## Section 3

#### Routes
* req params vs req query


* Write a route that utilizes req.params
app.get("/greet/:name/:lastname", function(req, res) {
});

* Adding onto the previous question: Inside the callback of the route, how can I access those parameters? *hint: thing back to /add/:x/:y/*
app.get("/greet/:name/:lastname", function(req, res) {
  res.send("Hello " + req.params.name + " " + req.params.lastname);
});

* Identify the parts of this url: `localhost:3000/results?search=star+wars`
                                     ^host          ^api call  ^ query string

* What part of the url above matches the express route?
query string

* What is the difference between using req.params and req.query
params are set with : and query auto pairs key values

* How can I access the query key/value pairs inside the route callback?
      res.render('results', { movies: data.Search });


## Section 4

* What is RESTful Routing?
a routing scheme designed to be dynamic

* What is CRUD?
Create, Read, Update, Destroy

* How to set your node/express app to stay open on a certain port?
var server = app.listen(process.env.PORT || 3000);


#### Breakdowns
Identify the following parts:
`var express = require('express');`
initializing module

`app.use(express.static(path.join(__dirname, 'static')));`
initializing static folder

`app.get('/', function(req, res){});`
creating path

`app.set('view engine', 'ejs');`
initializing ejs for views

`app.use(bodyParser.urlencoded({ extended: false }));`
making body-parser not throw errors

