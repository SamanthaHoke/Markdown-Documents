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

###Jasmine syntax
All tests are contained in *suites*. Suites are created with the **describe()** function. The describe function takes as parameters a string name for the suite and an anonymous function. Variables declared in the **describe()** function's anonymous function are available to all specs within it.  

	describe("Suite name", function(){});

In the anonymous function, separate tests are created for different functions and functionality using the **it()** function. The it function takes as parameters a string describing what the test will prove and another anonymous function. Tests defined by the **it()** function are called *specs*.  

	it("proves true is true", function(){});

Inside the **it()** function's anonymous function are placed your actual tests.
The main function for testing is the **expect()** function. It takes as a parameter the actual result or value to be tested. Chained onto the **expect()** function are various methods which test various conditions. These methods take as a parameter the expected value or result desired.  

	expect(true).toBe(true);

These chained methods are called *matchers*.
**Examples:**  
	
	toBe()
Acts like a strict equals (`===`)  

	toEqual()
Works for simple variables, literals, and objects.  

	toMatch()
Used with regular expressions  

	toBeDefined()
	toBeUndefined()
Used to check if a variable is undefined.  

	toBeNull()
Checks for nulls.  

	toBeTruthy()
	toBeFalsy()
Checks if a variable or object would be cast to true or false.  
[More information on truthy and falsy values](http://www.sitepoint.com/javascript-truthy-falsy)  

	toContain()
Checks an array for a value.  

	toBeLessThan()
	toBeGreaterThan()
Compares numeric values.  

	toBeCloseTo()
Checks numeric values are approximately the same. (Good for testing the results of floating point math.)  

	toThrow()
Used to check that any type of error is thrown. Used with no parameters.  

	toThrowError()
Used to check that a specific error is thrown. Used with the name of the type of error.  

------------
Jasmine also provides functions which can execute before each test is run, ensuring each test is run with the same set up, or run just once before all the tests are run.  
	
	beforeEach()
	beforeAll()
There are also their post-execution counterparts:  

	afterEach()
	afterAll()

**Example:**  

	var scope, localController;
	beforeEach(module('moduleName'));

        // Initialize the controller and a mock scope
        beforeEach(inject(function($controller, $rootScope) {
            scope = $rootScope.$new();
            localController = $controller('controllerName', {
                $scope: scope
            });
        }));
This code ensures that the module being tested is injected into each test and initializes a mock scope. This allows the tests to interact with the controller and scope.
This code would be placed at the top of the **describe()** function's anonymous function.



[Full documentation](http://jasmine.github.io/2.3/introduction.html)
-----------------------
[Back to README.md](https://github.com/SamanthaHoke/Markdown-Documents/blob/master/README.md)