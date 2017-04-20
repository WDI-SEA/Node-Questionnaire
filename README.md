## Section 1

* What is Node and why would we use it?

Node is a platform that uses JavaScript for creating network applications. It's used because it allows JS to be run on a server.

* How do we initialize a folder for use with node?
npm init

* What does `npm init` do?

It ensures that all appropriate packages are downloaded for use.

* What is a module and how does it relate to Node?

A module in relation to Node allows for code in written in a particular file (or folder) to be exported, and then imported into other files.

* I need to install a node module before I can use it. How can I install a node module so that it is accessable in javascript?

npm install


* How would I import a module into node?

var variable = function(name) {
	this.name = name;
};

module.exports = variable;

* When using require(), where is the module being pulled in from?
A separate .js file.


* List some common modules we have used in node. There are at least two.




## Section 2

#### Express Setup
* What is Express and why would we want to use it?

A web app server framework which allows for creation of a web application using Node.

* How do we import express into our node application?

npm install --save express


* After Express is imported, we need to initialize it. We can save this to a variable so that we can reuse it later. What would this line of code look like?

var app = express();

* What is app.use()? What does it do?



* What are static files? Why would we want a static file?

Unchanging files -- basically builds the framework.

* In contrast, what is the opposite of a static file? Why would we want a dynamic file being served?

Dynamic files seem to be mainly used for user input, which creates the interactive aspect of the webpage.

* What would we pass into app.use() to serve up static files? *Hint: This one-liner doesn't really change.*

app.use(express.static(path.join(__dirname, 'views')));


* What does the module body-parser do?
Parses parameters from a form.


* We need to tell express that we want to use body parser. Simplying requiring it isn't enough to activate it. How do we tell express we want to use body-parser?

app.use(bodyParser.urlencoded({extended: false}));


* If we use body-parser, we can retreive data from a POST (RESTful routing). How would we access this data from the 'req' object? `app.get('/', function(req, res) {})`

#### EJS & Setup
* What is an EJS file?

Embedded JS template engine.

* Is a EJS a static or a dynamic file?

dynamic

* Why would we want to use an EJS?

It allows for manipulation of the page.

* Is EJS used by a templating engine?
Yes

* If so, how do we tell express to use the ejs templating engine? *hint: app.use()*

app.set('view engine', 'ejs');

* Write out the syntax tags for using javascript in EJS. If it helps, add 2+2 in this div tag: `<div></div>`

<!-- <div> <%= name %> </div> -->

* We render ejs only when we are ready to send the page to the user. How do we render EJS for the browser? What is the function? *hint: this would be within the route (app.get(); )*

not sure if this is correct, but:
function(res, req){
	res.render();
}

* Following up on the last question, how do we pass data into EJS template? *hint: you will modify the previous answer*

app.get('/', function (req,res) {
	res.render('index', {whatever the entry here is});
});

## Section 3

#### Routes
* req params vs req query
* Write a route that utilizes req.params



* Adding onto the previous question: Inside the callback of the route, how can I access those parameters? *hint: thing back to /add/:x/:y/*



* Identify the parts of this url: `localhost:3000/results?search=star+wars`

localhost:3000 - the root url, in this case this is straight from the test computer
results? - the query being run -- this is searching for the user's input
search=star+wars -- user input being searched for - could have potentially been an entry in a form on the site


* What part of the url above matches the express route?



* What is the difference between using req.params and req.query

params is more specific --- if the params are defined as url/:x/:y, the user needs to enter exactly 2 paramaters to reach the page

query is more dynamic & searches for whatever the web page is that the user may be trying to be directed to --  url/?q=

* How can I access the query key/value pairs inside the route callback?



## Section 4

* What is RESTful Routing?

The route should relate to the type of item you are interacting with, as well as the action you'll be performing to change/view the state of the item.

* What is CRUD?

Create, Read, Update, Destroy

* How to set your node/express app to stay open on a certain port?

app.listen(3000);
3000 is an example, this could be any other port number

#### Breakdowns
Identify the following parts:
`var express = require('express');`


`app.use(express.static(path.join(__dirname, 'static')));`

`app.get('/', function(req, res){});`

`app.set('view engine', 'ejs');`

`app.use(bodyParser.urlencoded({ extended: false }));`

