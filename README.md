## Section 1

<!-- * What is Node and why would we use it? -->
Node is a platform that uses JS to create network applications. It allows JS to run on a server. You can use node to build chat servers, or a file upload client, etc. However, it is ot a web framework on it's own. We like it because it is non-blocking!

<!-- * How do we initialize a folder for use with node? -->
Once we navigate to that folder using terminal, we type npm init.

<!-- * What does `npm init` do? -->
Initializes Node Package Manager on our project

<!-- * What is a module and how does it relate to Node? -->
A module allows us to write code, bundle it up into a file, and use that file somewhere else in our project. This is great for node because we can essentially template things.

<!-- * I need to install a node module before I can use it. How can I install a node module so that it is accessable in javascript? -->
npm install --save 'module name'

<!-- * How would I import a module into node? -->
var module = require('module');

<!-- * When using require(), where is the module being pulled in from? -->
it's location in our folder

<!-- * List some common modules we have used in node. There are at least two. -->
body-parser
path
express-ejs-layouts

## Section 2

#### Express Setup
<!-- * What is Express and why would we want to use it?
 -->Express is a server framework. We use it to create web apps using Node.

<!-- * How do we import express into our node application?
 -->npm install --save express

<!-- * After Express is imported, we need to initialize it. We can save this to a variable so that we can reuse it later. What would this line of code look like?
 -->var express = require('express');

<!-- * What is app.use()? What does it do?
 -->app.use() runs apps like ejslayouts

<!-- * What are static files? Why would we want a static file?
 -->Static files do not change while the app is running. We want things like CSS, HTML and JS to be static files.

<!-- * In contrast, what is the opposite of a static file? Why would we want a dynamic file being served?
 -->A dynamic file is used when information will change. For example, a search results page. Templates make our website dynamic.

<!-- * What would we pass into app.use() to serve up static files? *Hint: This one-liner doesn't really change. -->
app.use(express.static(path.join(__dirname, 'static')));

<!-- * What does the module body-parser do? -->
body-parser takes incoming requests and extracts the body portion, making it easier to do something with or display.

<!-- * We need to tell express that we want to use body parser. Simplying requiring it isn't enough to activate it. How do we tell express we want to use body-parser? -->
app.use(bodyParser.urlencoded({ extended: false }));

<!--
* If we use body-parser, we can retreive data from a POST (RESTful routing). How would we access this data from the 'req' object? `app.get('/', function(req, res) {})` -->
req.body

#### EJS & Setup
<!-- * What is an EJS file? -->
EJS is an embedded JS file.

<!-- * Is a EJS a static or a dynamic file? -->
Dynamic!

<!-- * Why would we want to use an EJS? -->
We use it to create templates to inject values in HTML.

* Is EJS used by a templating engine?

<!-- * If so, how do we tell express to use the ejs templating engine? *hint: app.use()* -->
app.use(ejsLayouts);

<!-- * Write out the syntax tags for using javascript in EJS. If it helps, add 2+2 in this div tag: `<div></div>`  -->
<%= %>

<!-- * We render ejs only when we are ready to send the page to the user. How do we render EJS for the browser? What is the function? *hint: this would be within the route (app.get(); )* -->
app.get('/', function(req, res) {

});

<!-- * Following up on the last question, how do we pass data into EJS template? *hint: you will modify the previous answer* -->
app.get('/', function(req, res) {
  res.sendFile('index.html');
});

## Section 3

#### Routes
<!-- * req params vs req query -->
req params contains the route paramaters
req query addresses the url query paramaters

<!-- * Write a route that utilizes req.params -->

app.get('/game/:name', function(req, res) {
    var nameOfTheGame = req.params.name;

    var games = getGames();
    var game = getGame(games, nameOfTheGame);

    for (var i = 0; i < games.length; i++) {

        if (games[i].name.toLowerCase() === nameOfTheGame.toLowerCase()) {
            game = games[i];
            break;
        }
    }

    res.render('games-new');
});

<!-- * Adding onto the previous question: Inside the callback of the route, how can I access those parameters? *hint: thing back to /add/:x/:y/* -->
app.get('params-here', function...)

<!-- * Identify the parts of this url: `localhost:3000/results?search=star+wars`
 -->
 server/nameoffile/params

<!-- * What part of the url above matches the express route? -->
after the server

<!-- * What is the difference between using req.params and req.query -->
answered above

<!-- * How can I access the query key/value pairs inside the route callback? -->
res.render


## Section 4

<!-- * What is RESTful Routing? -->
Your URL shoud realted to the type of item you're inteacting with, as well as the action you'll perform.
REST: Representational State Transfer

<!-- * What is CRUD? -->
Create, Read, Update, Destroy // Almost everything we do on the internet

<!-- * How to set your node/express app to stay open on a certain port? -->
var port = 3000;
console.log("http://localhost:" + port);
app.listen(port);

#### Breakdowns
Identify the following parts:
`var express = require('express');`
variable = calling express to be used;

`app.use(express.static(path.join(__dirname, 'static')));`

`app.get('/', function(req, res){});`

`app.set('view engine', 'ejs');`

`app.use(bodyParser.urlencoded({ extended: false }));`

