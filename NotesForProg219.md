#General Notes for Prog 219
-------------
##Set up PuTTY
  

 - Install PuTTY
	 - If you are the admin on your computer, use the installer. Otherwise, use the zip file.
	 - [Download the zip or installer](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)
 - Create SSH variable as the location of plink.exe
 - Run **puttygen**
 - Create a new key pair.
	 - *It's a good idea to have a folder in your home directory to store data like this.*
 - Load public key to **BitBucket**
 - Change **.gitconfig** file to use SSH URL
 - `plink bitbucket.org`
 - `git config --global push.default simple`
 - Run Pageant and load private key *each time you start the computer.*


##Global Packages to Install
General packages:  

	npm install -g bower
	npm install -g jshint
	npm install -g nodemon

Express:  


	npm install -g express-generator
Angular:  

	npm install -g yo
	npm install -g grunt-cli
	npm install -g generator-angular 
	npm install -g generator-karma 


	
##$PATH 
The **$PATH** variable should include:

- Git cmd
- Text editor like Geany or Notepad++
- npm
- Your dosalias file's folder
- Node
- PuTTY
- Pageant

##GIT_SSH
The GIT_SSH variable should be set to the folder of plink.exe on your machine.