#Creating Different Projects
------------------------
##Create express project
	npm install -g express-generator
	express MyProject
	cd MyProject
	npm install

##Create express with Mongo
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

##Create Angular from scratch

 - Create a folder
 - Create index.html and index.js files
 - `Bower init`
 - Link to Angular on a CDN or use `bower install angular --save`
 - Run with **WebStorm** or create Python server script with:
	 - `python -m http.server 30025`
 
##Create Angular with Yeoman
When creating your first Angular project:  

    npm install -g karma-cli grunt-cli bower yo generator-karma generator-angular
When creating a new Angular project after the first time:

    mkdir Week02-Angular
    cd Week02-Angular
    yo angular

>Don't use Sass and Compass option without installing Ruby and Compass.

To run project, use `grunt serve`.

To run tests, use `grunt test`.
    


-----------
[Back to README.md](https://github.com/SamanthaHoke/Markdown-Documents/blob/master/README.md)
   
    
    


