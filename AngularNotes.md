#Angular Notes
-----------
##Angular Setup
###Steps (Simple):
- Create a folder
- Create an index.html and index.js files
- `Bower install jquery --save` or use a CDN

###Steps (Yeoman):
	npm install -g grunt-cli bower yo generator-karma generator-angular
    mkdir Week02-Angular
    cd Week02-Angular
    yo angular

##Main pieces:
###JavaScript Module Pattern
	(function(){//Place code here})();
Used to create self-contained modules in JavaScript. Allow data hiding and encapsulation.
###Angular Modules
	var app = angular.module('name', []);
>Place dependency module names in quotes in the []  
>The empty [] are required when creating new modules, but **must not** be used when referencing an existing module.


Modules can have factories and controllers.

	app.factory('Name', function(){return {prop: value}});
	
	app.controller('Name', function(){});
>If the module has dependencies, place the *unquoted*
> names of the dependencies in the function's () as parameters.
> `app.controller('Name', function(depend1, depend2){});`

Inside the controller, use either $scope or controllerAs to pass data to the view.

*$scope*  
In controller function:  

	$scope.property = value;

In the HTML:   

	<div ng-controller="Name as NameControl">
		<p> {{$scope.property}} </p>
	</div>
	
>$scope is going to be deprecated. Better to use controllerAs.

>When using $scope, must pass $scope in as a parameter of the controller function.


*ControllerAs*  
In controller function:  

	var NameControl = this;
	NameControl.property = value;  

In the HTML:  

	<div ng-controller="Name as NameControl">
		<p> {{NameControl.property}} </p>
	</div>


###Directives
>Directives appear in the HTML file, usually as attributes of HTML elements. Can also be used as custom element names. 
>
>Named as ng-*name* or data-ng-*name*.

**ng-app**  
**ng-app = "Name"**  
Place as attribute of the body tag.  
Identifies the module used as the app for the page.

**ng-controller = "ControllerName as contName"**  
Place as attribute of a div tag.  
Identifies controller for this div and give controller name to 
use with controllerAs pattern.  

**ng-repeat = "item in itemCollection"**
Place as attribute of list or other division to repeat.  
Makes the given list or division repeat for each *item* in *itemCollection*.

**ng-model**  
Place as attribute of input or output element.  
Gives name of model to which to bind.

**ng-submit**  
On a form as an attribute, specifies the function to run on submit.




###Expressions
Expressions can appear in attributes or where regular text would appear.

**Format:**  

	{{expression}}
	{{$scope.prop}}
	{{nameControl.prop}}
	{{model}}

>$scope can be omitted.  

**Examples:**  

	<p>{{bookControl.Title}}</p>
	<span class="done-{{item.done}}"/>




[Back to README.md](https://github.com/SamanthaHoke/Markdown-Documents/blob/master/README.md)