#Command Line Notes
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

**git checkout *branch* *fileName(s)***  
Checkout specific files from one branch to add to your current branch

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

##Bower
>Bower is a front-end library helper


**npm install -g bower**  
Installs bower globally. Use only once.  

**bower init**  
Initializes bower in a project.
>Take the recommended settings to list dependencies and ignore common files.

**bower install jquery --save**  
**bower install angular --save**  
Installs a local copy of the requested framework. `--save` sets the framework in the dependencies list.

##Grunt
>Grunt is a task runner for JavaScript 

**grunt**  
Builds project

**grunt test**  
Runs unit tests

**grunt serve**  
Runs project on localhost port.  

> To set the port, go into the **GruntFile.js** in your project, find the connection options object where **port** is listed. Change the port number to any number you prefer.


##Karma
>Karma is a unit test runner which constantly runs the tests in the background.


[Back to README.md](https://github.com/SamanthaHoke/Markdown-Documents/blob/master/README.md)