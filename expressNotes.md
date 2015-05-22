#Express
##Creating express projects
###Create express project
	npm install -g express-generator
	express MyProject
	cd MyProject
	npm install

###Create express with Mongo
Follow same steps as for a simple express project and then:
  
 - Create a `.bowerrc` file with   
	`{
	"directory": "public/components"
	}`
 - Install packages  
 - Add links in `index.jade` to jQuery, Bootstrap, Angular
 - Setup MongoLab
 - Create `resource.js` file in *Javascripts* folder.
 - Add your API key

> [See my MongoDB page](https://github.com/SamanthaHoke/Markdown-Documents/blob/master/mongoDB.md) for packages, links, and resource.js code.  

##Routes
Adding a route involves editing `routes/index.js` file the the project. 

**Sample route:**

	var express = require('express');
	var router = express.Router();

	/* GET home page. */
	router.get('/', function(req, res) {
 	res.render('index', { title: 'Test Live' });
	});

The first parameter to `router.get()` is the pattern of the route given, such as the default `'/'` or `'/:id'`.
The `req` object includes information about the request, including parameters from the query string. The `res` object sends a response or renders a file such as a jade file.

