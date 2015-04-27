#Creating Different Projects
------------------------
##Create express project
	npm install -g express-generator
	express MyProject
	cd MyProject
	npm install
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
    


   
    
    


