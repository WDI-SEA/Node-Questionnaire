## Section 1

1. What is Node and why would we use it?

Here's the answer I located, "Node.js is a platform built on Chrome's JavaScript runtime for easily building fast and scalable network applications. Node.js uses an event-driven, non-blocking I/O model that makes it lightweight and efficient, perfect for data-intensive real-time applications that run across distributed devices." We use it to serve out content on the Web using JavasScript to program it.

2. How do we initialize a folder for use with node?

	We run 'npm init' to set up the initialization file within the repo.

3. What does `npm init` do?

	It initializes a file within the repo that documents information about the Node repo and stores information about the modules that the Node repo needs to install and run successfully.

4. What is a module and how does it relate to Node?

	A module is a code library of functions that extends the capabilities available within Node.

5. I need to install a node module before I can use it. How can I install a node module so that it is accessable in javascript?

	From Terminal, in the Node repo's directory, run 'npm install --save ' and the name of the node module to be installed.

6. How would I import a module into node?

	within .js file, such as the 'app.js' file, add an entry like, "var express = require('express');"

7. When using require(), where is the module being pulled in from?

	The module is being pulled in from the 'node-modules' folder within the Node repo.

8. List some common modules we have used in node. There are at least two.

	We have used modules such as 'express' and 'path', also 'bodyParser'.

## Section 2

#### Express Setup
1. What is Express and why would we want to use it?

	Express is a very popular module that extends the capabilities of Node.js that provides functions to make Node easier to code.

2. How do we import express into our node application?

	We run 'npm install --save express' to import express into the Node app.
	We include "var express = require('express')" in our Node application to use Express in the Node app.

3. After Express is imported, we need to initialize it. We can save this to a variable so that we can reuse it later. What would this line of code look like?

var express = require('express'); makes it available for use.
var app = express();   We also define a reference to express with this statement.

4. What is app.use()? What does it do?

It defines a reference to additional features that we need to use within our Node application.

5. What are static files? Why would we want a static file?

Static files are html, css or js files that Node serves out that do not change, that is, staticly served out.

6. In contrast, what is the opposite of a static file? Why would we want a dynamic file being served?

The opposite are dynamic files. We would want to use them to provide different files depending on what the Node server needs to output.

7. What would we pass into app.use() to serve up static files? *Hint: This one-liner doesn't really change.*

app.use(express.static(path.join(__dirname, 'static')));

8. What does the module body-parser do?

It parses the body of the content that the browser sent to Node, such as the form data sent to Node by a web page.
Body-parser is a piece of express middleware that reads a form’s input and stores it as a javascript object accessible through
“req.body”.

9. We need to tell express that we want to use body parser. Simplying requiring it isn't enough to activate it. How do we tell express we want to use body-parser?

We use this statement:
app.use(bodyParser.urlencoded({ extended: false }));

10. If we use body-parser, we can retrieve data from a POST (RESTful routing). How would we access this data from the 'req' object? `app.get('/', function(req, res) {})`

ex.) 	app.post('/games', function(req, res) {
			var newGame = req.body;   (this contains the body contents as an object)
				...
			)};

#### EJS & Setup
11. What is an EJS file?

It is a view file that provides a template for Node to use to serve dynamic files to clients.

12. Is a EJS a static or a dynamic file?

It is a dynamic file.

13. Why would we want to use an EJS?

To provide web pages to clients that vary depending on the functions needed by the clients.

14. Is EJS used by a templating engine?

Yes, it is.

15. If so, how do we tell express to use the ejs templating engine? *hint: app.use()*

app.set('view engine', 'ejs');

16. Write out the syntax tags for using javascript in EJS. If it helps, add 2+2 in this div tag: `<div></div>`

<div><%= 2 + 2 %></div>

17. We render ejs only when we are ready to send the page to the user. How do we render EJS for the browser? What is the function? *hint: this would be within the route (app.get(); )*

What is the command that causes the ejs file to be rendered.

answer: res.render()

app.set('view engine', 'ejs');
...
app.get('/', function(req, res){
	res.render('videogames', {});

});

18. Following up on the last question, how do we pass data into EJS template? *hint: you will modify the previous answer*

tbd


## Section 3

#### Routes
1. req params vs req query



2.  Write a route that utilizes req.params



3. Adding onto the previous question: Inside the callback of the route, how can I access those parameters? *hint: thing back to /add/:x/:y/*



4. Identify the parts of this url: `localhost:3000/results?search=star+wars`

	localhost is the local machine
	3000 is the listening port
	/results is the route that the browser is accessing in its request
	?search=star+wars is the parameters that the browser is requesting

5. What part of the url above matches the express route?



6. What is the difference between using req.params and req.query


7. How can I access the query key/value pairs inside the route callback?



## Section 4

1. What is RESTful Routing?

Routing that maps HTTP VERBS + URLs to specific actions in the Node application
It reads or modifies the host server's resource.

2. What is CRUD?

It is short for Create, Read, Update and Destroy, the primary functions that a web server needs to provide for data management.

3. How to set your node/express app to stay open on a certain port?

Place this code at the end of your .js file:
app.listen(3000);
where 3000 is the port it listens on.

#### Breakdowns
Identify the following parts:
`var express = require('express');`

This makes the express module available within the Node application.

`app.use(express.static(path.join(__dirname, 'static')));`

This makes the static web pages available within the Node application by adding the static folder to the path.

`app.get('/', function(req, res){});`

This provides the routing for gets on the base URL of the website.

`app.set('view engine', 'ejs');`

Enables ejs to run within the Node application.

`app.use(bodyParser.urlencoded({ extended: false }));`

Enables bodyParser to run within the Node application.
