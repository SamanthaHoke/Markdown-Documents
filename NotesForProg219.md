#Command line notes
-----------
##General Windows commands
**cd**  
Change directory

**dir /A**  
List files and subfolders in current folder, including hidden folders

**mkdir *name***  
Make directory with given name in current directory

**type**  
Prints the contents of a file

**notepad**  
**notepad++**  
Use a program name that is in your $PATH to open it in a different program

**echo "Text" > file.txt**  
Create or overwrite a file with the given text

**SET**  
Shows all environment variables

##General Git Bash commands
**ls -a**  
List files and folders in current folder, including hidden folders

**cd**  
Change directory

**mkdir**  
**echo**  
Work as in Windows


##Git
**git init**  
Makes a folder a git repository

**git clone**  
Pulls down a local copy of an existing repository

**git status**  
Check repository status

**git pull**  
Pulls down master copy of a repository

**git add --all .**  
Adds untracked files, including removed files

**git commit -m "message"**  
Commit files to the local repository

**git push**  
**git push -u remote origin**  
Push files up to the remote repository

**git config --global user.name "FIRST_NAME LAST_NAME"**  
**git config --global user.email MY_NAME@example.com**  
Set up configurations

**git revert**  
Undo a local commit

**git reset**   
Remove files added to track

**git branch**  
List branches

**git checkout -b *branch* *tag***  
Check out into a new branch. Remove -b to checkout existing branch

**git tag -a v00.01.00 -m "Week 01"**  
**git push origin v00.01.00**  
Add a tag and push it to the origin

**git config --global push.default simple**  
Set push default

##Node
**npm install -g express-generator**  
install express-generator globally

**npm install**  
Install node in a project

**npm start**   
Start an express project

**npm list -g --depth=0**  
List globally installed packages

##Express
**express MyProject**  
Create new express project

##Grunt
**grunt**  
Build project

**grunt test**  
Run unit tests

**grunt serve**  
Run project on localhost port


#Steps For Different Projects
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
 - Run with WebStorm or create Python server script with:
	 - `python -m http.server 30025`
 
##Create Angular with Yeoman

    npm install -g grunt-cli bower yo generator-karma generator-angular
    mkdir Week02-Angular
    cd Week02-Angular
    yo angular

>Don't use Sass and Compass option without installing Ruby and Compass

To run, use `grunt serve`
    
##Set up PuTTY
  

 - Install PuTTY
 - Create SSH variable as the location of plink.exe
 - Run puttygen
 - Create a new key pair
 - Load public key to bitbucket
 - Change .gitconfig file to use SSH URL
 - `plink bitbucket.org`
 - `git config --global push.default simple`
 - Run Pageant and load private key each time you start the computer


##Global Packages to Install
	npm install -g bower
	npm install -g express-generator
	npm install -g jshint
	npm install -g nodemon
	
##$PATH 
The $PATH variable should include:

- Git cmd
- Text editor like Geany or Notepad++
- npm
- Your dosalias file's folder
- Node
- PuTTY
- Pageant

##GIT_SSH
The GIT_SSH variable should be set to the folder of plink.exe on your machine.

   
    
    


