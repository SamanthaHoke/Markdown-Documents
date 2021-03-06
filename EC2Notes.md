#EC2 Notes
#Setup
###Creating an Instance
 - Go to [AWS management console](https://www.amazon.com/ap/signin?openid.assoc_handle=aws&openid.return_to=https%3A%2F%2Fsignin.aws.amazon.com%2Foauth%3Fresponse_type%3Dcode%26client_id%3Darn%253Aaws%253Aiam%253A%253A015428540659%253Auser%252Fhomepage%26redirect_uri%3Dhttps%253A%252F%252Fus-west-2.console.aws.amazon.com%252Fconsole%252Fhome%253Fregion%253Dus-west-2%2526state%253DhashArgs%252523%2526isauthcode%253Dtrue%26noAuthCookie%3Dtrue&openid.mode=checkid_setup&openid.ns=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0&openid.identity=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0%2Fidentifier_select&openid.claimed_id=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0%2Fidentifier_select&action=&disableCorpSignUp=&clientContext=&marketPlaceId=&poolName=&authCookies=&pageId=aws.ssop&siteState=registered%2Cen_us&accountStatusPolicy=P1&sso=&openid.pape.preferred_auth_policies=MultifactorPhysical&openid.pape.max_auth_age=120&openid.ns.pape=http%3A%2F%2Fspecs.openid.net%2Fextensions%2Fpape%2F1.0&server=%2Fap%2Fsignin%3Fie%3DUTF8&accountPoolAlias=&forceMobileApp=0&forceMobileLayout=0) and login.
 - Choose the **EC2** option from the upper left corner.
 - Check your running instances. If you have one running and want to create a new one, first stop the running instance.
 - Click **launch instance**.
 - Choose instance type (eg. Linux or Windows)
	 - For this class use the **Ubuntu Server 14.04 LTS (HVM), SSD Volume Type** option
 - Choose micro type
 - Choose defaults for next two screens
 - Create a tag "Name" with the name of your instance as the value
 - Configure a new security group and choose ports to open
	 - or use an existing security group
 - Review and launch your instance.
 - Download the key pair

##Set up elastic IP Address
 - Go to **elastic IP** from the main EC2 dashboard. 
 - If you have not already created an elastic IP, create one and associate it with your instance
 - If you have already created one, you will have to disassociate it first and then re-associate it with your new instance.

##Set up keys
When you create an instance, you are given a **pem** file. To use this with Windows, you must convert it to a PuTTY **.ppk** file.  

 - Open puttyGen
 - Choose **Conversions** from  the top menu
 - Choose import key
 - Import your key and save your new **.ppk** file


>If you use a dosalias command such as **sshadd** to load your keys, add this new key to your dosalias file's command definition for **sshadd**.


##Set up PuTTY access
 - Run PuTTY
 - Enter your elastic IP and a session name on the main screen.
 - Save
 - Go to Connection > Data and enter "ubuntu" as the saved username
 - Return to **Session** and click save
 - **Optional:** go to **Appearance** to change font size and **Colours** to change font and background colors. Return to **session** to save
 - Click open to start a session

When returning to PuTTY, you can select a saved session and click load to reload it.


>**VERY IMPORTANT**  Do not click "save" instead of "load" when selecting a saved session or it will erase the saved session.


##Provision
Open a session to your EC2 instance with PuTTY  

###Update and upgrade the system:  

	
	sudo apt-get update
	sudo apt-get upgrade 

###Setup SSH: 
Return to the home directory:  

	cd

Create an ssh key:  

	ssh-keygen -t rsa -P '' -f ~/.ssh/id_rsa 
	cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys

Go to the .ssh folder in the home directory and cat the public key:  

	cd .ssh
	cat id_rsa.pub
Select the whole public key and add it to your BitBucket account.

Edit the **.bashrc** file in your home directory:  
Open in nano editor:  

	nano .bashrc

Add the following code to the bottom of **.bashrc**:  

	if [ -z "$SSH_AUTH_SOCK" ] ; then
    eval `ssh-agent` 
	fi

	export PATH="$PATH:$HOME/npm/bin"

Rerun the **.bashrc** file:  

	source ~/.bashrc

Make the private key accessible only to you: 

	chmod 400 ~/.ssh/id_rsa

Load the key:  

	cd .ssh
	ssh-add id_rsa


###Install Git: 
>Run in the home directory 

	sudo apt-get install git

	mkdir Git
	cd Git
	git clone git://github.com/charliecalvert/JsObjects.git
Also clone your repository.

###Install LAMP:  

	sudo apt-get install tasksel
	sudo tasksel install lamp-server

###Set up .bash_aliases
Copy from JsObjects to the home directory:  

	cd
	cp ~/Git/JsObjects/Utilities/SetupLinuxBox/.bash_aliases .

Open in nano. Change your **sshadd** command to use your key name (probably id_rsa). Reload file from the home directory:  

	source .bash_aliases
###Set up Node  
Run these files from JsObjects:  

	cd Git/JsObjects/Utilities/NodeInstall
	./NodeInstall.sh
	./InstallNodePackages.sh


>Shell scripts are run with `./scriptName.sh`

##Upstart
Upstart is a tool to keep our applications running even after we close the PuTTY session to our EC2 instance.

####Create a bin directory on your EC2 instance


	if [ ! -d "~/bin" ]; then
    mkdir ~/bin
	fi
####Create symbolic link to project in the bin directory

	ln -s /home/ubuntu/Git/repositoryName/projectName ~/bin/linkName

####Create .conf file
Place in project folder.

		# This is an upstart script: http://upstart.ubuntu.com/index.html
	description "a script to keep a node.js application in memory even after rebooting"
	author      "Charle Calvert - http://www.elvenware.com/charlie"

	# Start after all drives mounted
	start on started mountall
	stop on shutdown

	# Automatically Respawn:
	respawn
	respawn limit 99 5

	script
    	export HOME="/home/ubuntu"

	# The following assumes nodejs is in /usr/bin
    	exec /usr/bin/nodejs /home/ubuntu/bin/midterm/bin/www >> /var/log/midterm.log 2>&1

	end script

	post-start script
   	# Optionally put a script here that will notifiy you node has (re)started
  	 # /root/bin/hoptoad.sh "node.js has started!"
   	echo "node.sj has started running BridgeReader"
	end script

Copy this file to etc/init/ folder:  

	sudo cp midterm.conf /etc/init/midterm.conf

Start and stop with:
	
	sudo start midterm
	sudo stop midterm

You can view the log of action on the running process by using:

	cat ~/var/log/midterm.log


###Resources
 - Charlie Calvert's [NodeJs page](http://www.elvenware.com/charlie/development/web/JavaScript/NodeJs.html#upstart)
 - Charlie Calvert's [project notes](http://www.ccalvert.net/books/CloudNotes/Prog219/Prog219-Week08-2015.html)

##Important notes
 - Never have more than one running instance when using the free AWS account or you can be charged.
 - Don't create multiple elastic IP addresses: this would incur a fee.
 - Do not click "save" instead of "load" when selecting a saved session or it will erase the saved session when using PuTTY.

#Resources
 - [Set up on Elvenware](http://www.ccalvert.net/books/CloudNotes/Assignments/Ec2GetStarted.html)
 - [Charlie Calvert's slide deck](http://bit.ly/ec2-aws)
 - [Provision on Elvenware](http://www.ccalvert.net/books/CloudNotes/Assignments/Ec2Provision.html)

-------------
[Back to README.md](https://github.com/SamanthaHoke/Markdown-Documents/blob/master/README.md)