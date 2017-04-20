BOWMAN NEELY

## Section 1

1) What is Node and why would we use it?

	Node runs javascript to create aplications where both the client and server use JS.

	Node is a platform that uses JavaScript for creating network applications. It allows JavaScript to be run on a server. 

2) How do we initialize a folder for use with node?

	"npm init" in the terminal.

3) What does `npm init` do?

	"npm" stands for 'node package manager' and it makes sure the packages you are using are valid and running thier most current versions.  Additionally, it lets people who use your code know which packages and which versions of those packages your code uses.

4) What is a module and how does it relate to Node?

	A module is a container of files that allows code written in a particular file to be exported or imported into other files.

5) I need to install a node module before I can use it. How can I install a node module so that it is accessable in javascript?

	In the command-line type "npm install --save express."  Then create an index.js file by typing "touch index.js".  Then start "npm install -g nodemon" (-g 'global').  Now you simply enter the name of your file to create it, "nodemon nameOfFile.js" 


6) How would I import a module into node? 

	You can use the keyword 'require' is used to import modules in Node.js.

7) When using require(), where is the module being pulled in from?

	From the exported files.

8) List some common modules we have used in node. There are at least two.

	Request, EJS, Express, http.


## Section 2

#### Express Setup
1) What is Express and why would we want to use it?

	A:  Express is a web app server framework used to create web applications in Node.


2) How do we import express into our node application? 

	"npm install --save express"


3) After Express is imported, we need to initialize it. We can save this to a variable so that we can reuse it later. What would this line of code look like?

	var express = require('express');
		var app = express();


4) What is app.use()? What does it do?

	App.use() is an HTTP method to request  'middleware' functions handle (e.g. GET, PUT, POST).

5) What are static files? Why would we want a static file?

	Static files include images, Java Script, and CSS are examples of static files.  They are files that do not change in response to user input.  It contains the same prebuilt content each time the page loads.


6) In contrast, what is the opposite of a static file? Why would we want a dynamic file being served?

	The opposite of a static file is a dynamic file.  We would want a dynamic file being served to respond to user input.


7) What would we pass into app.use() to serve up static files? *Hint: This one-liner doesn't really change.*

	app.use(express.static(path.join(__dirname, 'views')));


8) What does the module body-parser do?

	The body-parser interprets the data and displays it in a more useable form. (i.e. inserting spaces between words instead of "+"'s')


9) We need to tell express that we want to use body parser. Simplying requiring it isn't enough to activate it. How do we tell express we want to use body-parser?

	
	var bodyParser = require('body-parser');

	app.use(bodyParser.urlencoded({extended: false}));



10) If we use body-parser, we can retreive data from a POST (RESTful routing). How would we access this data from the 'req' object? `app.get('/', function(req, res) {})`



#### EJS & Setup

11) What is an EJS file?

 	A template engine that combines data and a template to produce HTML.


12) Is a EJS a static or a dynamic file?

	Dynamic.


13) Why would we want to use an EJS?

	To create a layout with a special place for our page content.


14) Is EJS used by a templating engine?

	Yes.


15) If so, how do we tell express to use the ejs templating engine? *hint: app.use()*

	after installing...
	npm install --save express-ejs-layouts

	require the module to add it to the app...
	var ejsLayouts = require("express-ejs-layouts");
	app.use(ejsLayouts);


16) Write out the syntax tags for using javascript in EJS. If it helps, add 2+2 in this div tag: `

	 <div> %> 2+2 <% </div> 


17) We render ejs only when we are ready to send the page to the user. How do we render EJS for the browser? What is the function? *hint: this would be within the route (app.get(); )*

	app.get("/", function(req, res) {
  		res.render("index", {__: "__", __: ["__", "__"]})
});


18) Following up on the last question, how do we pass data into EJS template? *hint: you will modify the previous answer*

## Section 3

#### Routes
1) req params vs req query

	req params contain route parameters in the path portion of the url.  req query contains the url query parameters after the url.

2) Write a route that utilizes req.params

	app.get(“/greet/:name/:middlename”, function(req, res) {
 	res.send(“Whaddup ” + req.params.name + ” ” + req.params.middlename);
});
	

3) Adding onto the previous question: Inside the callback of the route, how can I access those parameters? *hint: thing back to /add/:x/:y/*

	app.get(“/add/:x/:y”, function(req, res) {
 	res.send(“Check't: ” + (parseInt(req.params.x) + parseInt(req.params.y)));
});


4) Identify the parts of this url: 

`localhost:3000/results?search=star+wars`
domainname/port/path/query/parameters



5) What part of the url above matches the express route?

 the "/" "?"


6) What is the difference between using req.params and req.query

	Params is used for the route parameters, query for the URL qurery parameters.


7) How can I access the query key/value pairs inside the route callback?

	Using the 'require'.

## Section 4

1) What is RESTful Routing?

Representational State Transfer (REST) is a set of software architecture practices used to create scalable web services (through a combination VERB and URL)

2) What is CRUD?

	Crud stands for: Create, Read, Update, Delete

3) How to set your node/express app to stay open on a certain port?

	Using the GET verb.

#### Breakdowns
Identify the following parts:
`var express = require('express');`

	Putting express into a variable we can reuse later.


`app.use(express.static(path.join(__dirname, 'static')));`

	A function 'one liner' used to serve up static files.

`app.get('/', function(req, res){});`

	A function allowing EJS to render the page to the user.

`app.set('view engine', 'ejs');`

	Enables ejs to run in the node application.

`app.use(bodyParser.urlencoded({ extended: false }));`

	This line lets Express know we want to use bodyParser.
