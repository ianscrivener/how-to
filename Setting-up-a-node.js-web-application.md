# Setting up a node.js web application #

<br/>**install the express & nodemon node.js modules**

	npm install express -g
	npm install nodemon -g


<br/>**make a Ubuntu for the webapp**

	useradd -m webapp -d /home/webapp

<br/>**make a directory & change to that directory**

	mkdir /home/webapp/node
	cd /home/webapp/node

<br/>**create an express node.js application**

	express testapp
	cd testapp
		
<br/>**start the node.js test web application**

	nodemon app.js

this should return something like.. indicating success

	10 Jul 06:48:03 - [nodemon] v0.7.8
	10 Jul 06:48:03 - [nodemon] to restart at any time, enter `rs`
	10 Jul 06:48:03 - [nodemon] watching: /home/webapp/node/test-app
	10 Jul 06:48:03 - [nodemon] starting `node app.js`
	Express server listening on port 3000

<br/>**check that it is running OK with web browser**

**[http://xxx.xxx.xxx.xxx:3000/](http://xxx.xxx.xxx.xxx:3000/)**

you should see the basic 'Welcome to Express' page.