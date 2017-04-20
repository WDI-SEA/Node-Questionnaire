## Section 1

* What is Node and why would we use it?

Node is a runtime environment where both the client and server use JavaScript.  It's mainly useful because it's asynchronous/non-blocking, allowing several requests to be handled at once instead of one by one.



* How do we initialize a folder for use with node?

Create/navigate to the folder you want to initialize in the Terminal, and then type "npm init".



* What does `npm init` do?

Creates the package.json file in our project that contains imporant info, like Name, Version, Description, as well as any dependencies your project needs to run correctly.



* What is a module and how does it relate to Node?

A module encapsulates related code into a single unit of code.  We can utilize this in Node to take complex operations and execute them significantly less code, often just a single word.



* I need to install a node module before I can use it. How can I install a node module so that it is accessable in javascript?

Navigate to your project folder in the Terminal and then type "npm install --save *name of module*"



* How would I import a module into node?

At the top of your node.js file, store the module in a variable by using the require function.  Something like:

var varName = require('moduleName');



* When using require(), where is the module being pulled in from?

From the node_modules folder in your project folder.



* List some common modules we have used in node. There are at least two.

express, path, ejs, body-parser


## Section 2

#### Express Setup
* What is Express and why would we want to use it?

Express is a Node.js framework that allows us to build software with JavaScript on the server side.  It also allows us to build pages that are malleable, getting info from APIs and building a page's HTML with that data.



* How do we import express into our node application?

Make sure express is saved to your project directory.  "npm install --save express"



* After Express is imported, we need to initialize it. We can save this to a variable so that we can reuse it later. What would this line of code look like?

Require it at the top of your node.js file.  "var app = require('express');"



* What is app.use()? What does it do?

It mounts a specified middleware function(s) at a specified path.  For us, we use it without a specified path to enable 3rd party middleware to add functionality to our Express app.



* What are static files? Why would we want a static file?

Static files are things like images, CSS files, JavaScript files and some HTML files.  Static HTML pages are useful if your landing page doesn't have any outside/user info to incorporate, as they're easier to code.  CSS files, images and JavaScript files will always be static but are still important in creating a beautiful/dynamic website.



* In contrast, what is the opposite of a static file? Why would we want a dynamic file being served?

Dynamic files use data pulled from APIs and/or data bases to generate content on the page.  This means we can use information/applications created by others in our websites without having to do all the legwork, and/or display information specific to a particular user.



* What would we pass into app.use() to serve up static files? *Hint: This one-liner doesn't really change*

app.use(express.static(path.join(__dirname, 'static')));
Although you would also need the 'path' module for this to work.



* What does the module body-parser do?

Takes the string that an API call returns and puts it into a JSON object that we can then interact with.



* We need to tell express that we want to use body parser. Simplying requiring it isn't enough to activate it. How do we tell express we want to use body-parser?

app.use(bodyParser.urlencoded({ extended: false }));



* If we use body-parser, we can retreive data from a POST (RESTful routing). How would we access this data from the 'req' object? `app.get('/', function(req, res) {})`


app.get('/', function(req, res) {
		req.body
})



#### EJS & Setup
* What is an EJS file?

It's an Embeded JavaScript file.  It kind of combines HTML and JavaScript, allowing the HTML of elements to be generated using data pulled from APIs or data bases, instead of hard coded.



* Is a EJS a static or a dynamic file?

Dynamic file



* Why would we want to use an EJS?

Our webpages become much more malleable and can change on the fly with user interaction.



* Is EJS used by a templating engine?

....yes?  I thought it WAS a templating engine?




* If so, how do we tell express to use the ejs templating engine? *hint: app.use()*

app.use(ejsLayouts); ???

or did you mean for the hint to say 'app.set'?  In which case, I would have put:

app.set('view engine', 'ejs');



* Write out the syntax tags for using javascript in EJS. If it helps, add 2+2 in this div tag: `<div></div>`

<div>
	<% 2 + 2 %>
</div>



* We render ejs only when we are ready to send the page to the user. How do we render EJS for the browser? What is the function? *hint: this would be within the route (app.get(); )*

app.get('path', function (req, res) {
	res.render('ejs file name');
});



* Following up on the last question, how do we pass data into EJS template? *hint: you will modify the previous answer*

app.get('path', function (req, res) {
	res.render('ejs file name', { key: body});
});



## Section 3

#### Routes
* req params vs req query

req params are pulled from the url itself, req query pulls from the query string in a url



* Write a route that utilizes req.params

app.get('/:x/:y', function (req, res) {

});



* Adding onto the previous question: Inside the callback of the route, how can I access those parameters? *hint: thing back to /add/:x/:y/*

app.get('/:x/:y', function (req, res) {
	var x = req.params.x;
	var y = req.params.y;
	res.send( x + y );
});



* Identify the parts of this url: `localhost:3000/results?search=star+wars`

localhost = host
3000 = port
results = path
?search=star+wars = query string



* What part of the url above matches the express route?

/results



* What is the difference between using req.params and req.query

req params are pulled from the url itself, req query pulls from the query string in a url



* How can I access the query key/value pairs inside the route callback?

req.query



## Section 4

* What is RESTful Routing?

Requesting data from an API by using a path/url that the API authenticates and responds to with the data you requested.



* What is CRUD?

Create, Read, Update, Destroy



* How to set your node/express app to stay open on a certain port?

app.listen(port)



#### Breakdowns
Identify the following parts:
`var express = require('express');`

Tell's our Node that it will require express in order to run properly



`app.use(express.static(path.join(__dirname, 'static')));`

Tell's our app to load pages from the static folder if no other path is specified?



`app.get('/', function(req, res){});`

Set's a route on our homepage



`app.set('view engine', 'ejs');`

Tell's our Node to use EJS as our view engine



`app.use(bodyParser.urlencoded({ extended: false }));`

Tell's our Node to use the body-parser module to parse data from APIs


