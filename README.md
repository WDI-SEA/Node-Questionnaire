## Section 1

1. What is Node and why would we use it?

A runtime environment for running JS.

2. How do we initialize a folder for use with node?

In terminal, type: NPM init.

3. What does `npm init` do?

Makes sure all packets are installed & available.

4. What is a module and how does it relate to Node?

A container(file) of related code allowing that code to be imported & exported into other files.

5. I need to install a node module before I can use it. How can I install a node module so that it is accessable in javascript?

In terminal: "npm install --save nameOfFile.js"

6. How would I import a module into node?
- Use the keyword "require"...
		var require = function(path) {
		...
		return module.exports;
}

- Then in your main.js "require"...
		// main.js
		var greetings = require("./greetings.js")

- Use the methods of greetings.js as a property of the greetings variable in main.js...
		var greetings - require("./greetings.js");
		greetings.sayHelloInEnglish();
		greetings.sayHelloInSpanish();

7. When using require(), where is the module being pulled in from?
node_modules folder


8. List some common modules we have used in node. There are at least two.
body-parcer
express

## Section 2

#### Express Setup
1. What is Express and why would we want to use it?

A web module & app server framework used to create app's with Javascript.

2. How do we import express into our node application?

npm install --save express

3. After Express is imported, we need to initialize it. We can save this to a variable so that we can reuse it later. What would this line of code look like?

var express = require('express');
var app = express();

4. What is app.use()? What does it do?

app is a var refering to 'express' & 'express' uses (whatever comes in here)

5. What are static files? Why would we want a static file?

Static files (css, images, html, main.js) don't change from a server. You can refer to it for your dynamic pages.

6. In contrast, what is the opposite of a static file? Why would we want a dynamic file being served?

Dynamic files. They can be changed on the serverside by many different users.

7. What would we pass into app.use() to serve up static files?
*Hint: This one-liner doesn't really change.*

app.use(express.static(path.join(__dirname, ‘static’)));

8. What does the module body-parser do?

Body-parser is a piece of express middleware that reads a form's input and stores it as a javascript object accessible through
"req.body".

9. We need to tell express that we want to use body parser. Simplying requiring it isn't enough to activate it. How do we tell express we want to use body-parser?

//load body parser module
var bodyParser = require('body-parser');

//tell express to "use" it as a middleware
app.use(bodyParser.urlencoded({ extended: false }));

10. If we use body-parser, we can retreive data from a POST (RESTful routing). How would we access this data from the 'req' object? `app.get('/', function(req, res) {})`

app.use(bodyParser.urlendcoded({ extended: false }));

#### EJS & Setup
1. What is an EJS file?

Combines templates & data to make HTML.

2. Is a EJS a static or a dynamic file?

Dynamic.

3. Why would we want to use an EJS?

It allows many pages to be made from a small ammount of coding work.

4. Is EJS used by a templating engine?

Yes.

5. If so, how do we tell express to use the ejs templating engine? *hint: app.use()*

app.set('view engine', 'ejs');

6. Write out the syntax tags for using javascript in EJS. If it helps, add 2+2 in this div tag:

`<div><%= 2 + 2 %></div>`


7. We render ejs only when we are ready to send the page to the user. How do we render EJS for the browser? What is the function? *hint: this would be within the route (app.get(); )*

app.get('/', function(req, res) {
	res.render('videogames', {...})
});

videogames.ejs is understood because ejs is the render.

8. Following up on the last question, how do we pass data into EJS template? *hint: you will modify the previous answer*

???

## Section 3

#### Routes
1. req params vs req query

req query for get routes will be used for our course.

2. Write a route that utilizes req.params
3. Adding onto the previous question: Inside the callback of the route, how can I access those parameters? *hint: thing back to /add/:x/:y/*
4. Identify the parts of this url: `localhost:3000/results?search=star+wars`

localhost:3000  - our domain (on our computer) & port
/results  - route ()
?search=star+wars  - parmeters (length varies based on our form)

5. What part of the url above matches the express route?
6. What is the difference between using req.params and req.query
7. How can I access the query key/value pairs inside the route callback?



## Section 4

1. What is RESTful Routing?

Representational State Transfer (REST)
The basic premise is, instead of relying exclusively on the URL to indicate what webpage you want to go to (and just using the one method), it's a combination of VERB and URL.

This way, the same URL, when used with a different verb (such as GET, PUT, POST, DELETE), will get you to a different page. This makes for cleaner, shorter URLs, and is particularly adapted to CRUD applications, which most web apps are.

2. What is CRUD?

Create, Read, Update, Delete.

3. How to set your node/express app to stay open on a certain port?

Either hardcode it: app.set('port', process.env.PORT || 3000);
or: $ PORT=8080 node app.js

app.listen

#### Breakdowns
Identify the following parts:

`var express = require('express');`

Makes Express module a var & requires our project to use it.

`app.use(express.static(path.join(__dirname, 'static')));`

???

`app.get('/', function(req, res){});`

???

`app.set('view engine', 'ejs');`

Enables EJS to run in Node.

`app.use(bodyParser.urlencoded({ extended: false }));`

