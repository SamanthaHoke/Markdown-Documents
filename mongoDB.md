#MongoDB and NoSQL
-----------------
##NoSQL
NoSQL is a type of database design which instead of using a traditional relational structure uses some other variant of structure to store data. 
Usually open-source and distributed.  
[Full Definition](http://nosql-database.org/)

###Notes:
 - Alternate to relational SQL databases
	 - Isn't a replacement for SQL, has a different purpose and niche
 - Not relational
 - Based on documents instead of tables and rows.
	 - Often uses JSON
 - Good for things that do not usually work well in SQL:
	 - Working with large datasets with irregular shapes
	 - Fast performance when working with big data
	 - Scalable quickly
	 - Can be distributed
 

>Based on Charles Calvert's notes on [MongoDB](http://bit.ly/elf-mongo)

##MongoDB
Collections are like tables.  
Documents are like records.

Packages needed:  

	bower install angular --save
	bower install angular-mocks --save
	bower install angular-resource --save
	bower install bootstrap --save
	bower install jquery --save

Links to add:  

	 // Latest compiled and minified CSS
    link(rel='stylesheet', href='components/bootstrap/dist/css/bootstrap.min.css')

    // Optional theme
    link(rel='stylesheet', href='components/bootstrap/dist/css/bootstrap-theme.min.css')

    // JavaScript
    script(src='components/jquery/dist/jquery.js')
    script(src='components/bootstrap/dist/js/bootstrap.min.js')
    script(src='components/angular/angular.js')
    script(src='components/angular-resource/angular-resource.js')

Resource.js:  

	angular.module('<moduleName>', ['ngResource'])
    .constant('CONFIG', {
        DB_NAME: '<yourDBName>',
        COLLECTION: '<yourCollection>',
        API_KEY: '<yourAPIKey>'
    })
	
Retrieve the collection in the module's factory:  

	.factory('Name', function ($resource, CONFIG) {
        var localCollection = $resource(
            'https://api.mongolab.com/api/1/databases/' + CONFIG.DB_NAME +
            '/collections/' + CONFIG.COLLECTION + '/:id', {
                apiKey: CONFIG.API_KEY
            },
            {
                update: {method: 'PUT'}
            });
		//Normal Factory Code....

>Based on Charles Calvert's instructions on [creating an AngularMongoDBStarter](http://www.ccalvert.net/books/CloudNotes/Assignments/AngularMongoDbStarter.html)


##MongoLab
>MongoLab is a website to create and manage mongoDB databases.
[MongoLab](https://mongolab.com/)  


###Setup:
 - Create an account
 - Create new database
	 - Select Amazon
	 - Single node
	 - Sandbox
 - Click on database
 - Create user
	 - Click users
	 - Add user
	 - Give username and password
 - Add collection
 - Add document to collection


###Get an API Key
 - Go to account page
 - Click on user
 - Find "current key" near the bottom


[Back to README.md](https://github.com/SamanthaHoke/Markdown-Documents/blob/master/README.md)