#Unit testing
##Main Points
 - Write test first, then write code, then refactor
	 - *Test Driven Design*
 - Test individual objects, smallest discrete pieces
 - Use mock objects to simulate dependencies
 - Supports refactoring code
 - Test boundary conditions 


Tests act as documentation and specification for a project. They make it easier to extend and refactor code and improve reusability.

If writing the test is too difficult or complex, the code itself is probably overly complex and not very reusable.  

>Encapsulation must be preserved to allow testable code. Objects should be as loosely-coupled as possible.

Public interfaces, not private methods should be tested.

>Based on Charles Calvert's [Unit Tests: Part 01](http://bit.ly/1dTjs8h)

##Jasmine
Jasmine is a Unit Test framework for JavaScript.

###Install
Installing Jasmine:  

	npm install -D jasmine
	npm install -g jasmine

Yeoman generator:  

	npm install -g generator-jasmine

Add jasmine to a project:  

	yo jasmine

Go to `test/bower.json` and change Jasmine version to 2.3.0  

Add chai to `bower`: Run `bower install chai --save`  
Run `bower install` *in the test folder!*


In `test/index.html` add these script tags:  

	<script src="bower_components/jasmine/lib/jasmine-core/boot.js"></script>

	<script src="bower_components/chai/chai.js"></script>

###Set up Grunt
Grunt is a task runner.  

	npm install -g generator-gruntfile
	npm install grunt --save-dev
	npm install grunt-contrib-qunit --save-dev
	npm install grunt-contrib-jshint --save-dev
	npm install grunt-contrib-watch --save-dev
	yo gruntfile

In `GruntFile.js`, modify the `jshint options` section to be:  

	browser: true,
	globals: { jQuery: true, chai: true, angular: true },
	boss: true,
	ignores: [
    	'**/components/**',
    	'**/bower_components/**',
    	'**/node_modules/**'
	],
	reporter: 'checkstyle',
	reporterOutput: 'result.xml'

Run with `grunt jshint`

-----------------------
[Back to README.md](https://github.com/SamanthaHoke/Markdown-Documents/blob/master/README.md)