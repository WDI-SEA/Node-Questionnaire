## Section 1

<!-- 1.  What is Node and why would we use it?  -->

Node is a runtime environment for running JavaScript, and it allows us to create applications where both the client and server use JavaScript. Specifically, we'll use a web framework called Express in order to create a secure web server that interacts with a database.

<!-- 2. How do we initialize a folder for use with node?  -->
index.js

<!-- 3.  What does `npm init` do? -->
Initiates a node and inserts meta data such as the JSON package to define the entry point for the app


<!-- 4.  What is a module and how does it relate to Node?  -->
Node's module system allows code written in a partiuclar file (or folder) to be exported, and then imported into other files

<!-- 5.  I need to install a node module before I can use it. How can I install a node module so that it is accessable in javascript? -->
npm install --save ejs

<!-- 6.  How would I import a module into node? -->
module.exports

<!-- 7.  When using require(), where is the module being pulled in from? -->
from your exports

<!-- 8.  List some common modules we have used in node. There are at least two. -->
ejs / JSON / http






## Section 2

#### Express Setup
<!-- 1.  What is Express and why would we want to use it? -->
It's a web framework that takes a URL pattern and a callback function.

<!-- 2.  How do we import express into our node application? -->
npm install --save express


<!-- 3.  After Express is imported, we need to initialize it. We can save this to a variable so that we can reuse it later. What would this line of code look like? -->
var express = require('express');
you make it available to use for your code.

<!-- 4. What is app.use()? What does it do?
 -->
is utilized to run a function on a pathway/address / uri (uniformed resource indicator - )


<!-- 5.  What are static files? Why would we want a static file? -->
static means unchanged or constant.  it contain the same prebuilt content each time the page is loaded


<!-- 6.  In contrast, what is the opposite of a static file? Why would we want a dynamic file being served? -->
You would need to use a dynamic page can contain client side scripting or service side scripting to generate the changing content.

<!-- 7.  What would we pass into app.use() to serve up static files? *Hint: This one-liner doesn't really change.* -->
app.use(express.static('static'));
// app.use(express.static(path.join(_dirname, 'static')));

<!-- 8.  What does the module body-parser do? -->
Body-parser is a piece of express middleware that reads a form’s input and stores it as a javascript object accessible through
“req.body”.

<!-- 9.  We need to tell express that we want to use body parser. Simplying requiring it isn't enough to activate it. How do we tell express we want to use body-parser? -->
var bodyParser = require('body-parser');

<!-- 10.  If we use body-parser, we can retreive data from a POST (RESTful routing). How would we access this data from the 'req' object? `app.get('/', function(req, res) {})` -->
/load body parser module
var bodyParser = require('body-parser');

//tell express to "use" it as a middleware
app.use(bodyParser.urlencoded({ extended: false }));






############ EJS & Setup#####################
<!-- 1.  What is an EJS file? -->
EJS is a simple templating language that lets you generate HTML markup with plain JavaScript.

<!-- 2.  Is a EJS a static or a dynamic file? -->
static

<!-- 3.  Why would we want to use an EJS? -->
to template your node application

<!-- 4.  Is EJS used by a templating engine? -->
yes

<!-- 5.  If so, how do we tell express to use the ejs templating engine? *hint: app.use()* -->

app.get('/', function(req, res)
<!-- 6.  Write out the syntax tags for using javascript in EJS. If it helps, add 2+2 in this div tag: `<div></div>` -->
<div> % 2+2 %</div>

<!-- 7.  We render ejs only when we are ready to send the page to the user. How do we render EJS for the browser? What is the function? *hint: this would be within the route (app.get(); )* -->



<!-- 8.  Following up on the last question, how do we pass data into EJS template? *hint: you will modify the previous answer* -->






## Section 3

#### Routes
<!-- 1.  req params vs req query -->


<!-- 2.  Write a route that utilizes req.params -->

app.get("/add/:x/:y", function(req, res) {
  res.send("The answer is: " + (parseInt(req.params.x) + parseInt(req.params.y)));
});
<!-- 3.  Adding onto the previous question: Inside the callback of the route, how can I access those parameters? *hint: thing back to /add/:x/:y/* -->
app.get("/add/:x/:y", function(req, res) {
  res.send("The answer is: " + (parseInt(req.params.x) + parseInt(req.params.y)));
});

<!-- 4.  Identify the parts of this url: `localhost:3000/results?search=star+wars` -->
localhost:3000 = port
results
?
search
star+wars

<!-- 5.  What part of the url above matches the express route? -->


<!-- 6.  What is the difference between using req.params and req.query -->


<!-- 7.  How can I access the query key/value pairs inside the route callback? -->



## Section 4

<!-- 1.  What is RESTful Routing? -->
The basic premise is, instead of relying exclusively on the URL to indicate what webpage you want to go to (and just using the one method), it's a combination of VERB and URL.

This way, the same URL, when used with a different verb (such as GET, PUT, POST, DELETE), will get you to a different page. This makes for cleaner, shorter URLs, and is particularly adapted to CRUD applications, which most web apps are.

<!-- 2.  What is CRUD? -->
create ready update delete

<!-- 3.  How to set your node/express app to stay open on a certain port? -->

#### Breakdowns
<!-- 4.  Identify the following parts:
`var express = require('express');` -->


<!-- `app.use(express.static(path.join(__dirname, 'static')));` -->

<!-- `app.get('/', function(req, res){});`  -->

<!-- `app.set('view engine', 'ejs');` -->

<!-- `app.use(bodyParser.urlencoded({ extended: false }));` -->

