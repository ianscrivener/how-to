# How-To Setup Ubuntu Server #


### 1) Install Ubuntu 13.04 Server ###

> Previously you need to have setup Ubuntu 13.04 Server on your VMWare or Rackspace/OpenStack platform.


<br/>**switch to root user**

	sudo su


<br/>**update Ubuntu**

    sudo apt-get update


<br/>**(VMWare only) install SSH server**

	apt-get install openssh-server -y


<br/>**install git**

	apt-get install git -y




<br/>
## 2) Make sure gdal is not already installed ##


**look for gdal**

	dpkg --list | grep gdal
	
A previous gdal install will very likely cause problem for opengeo. If it is previously installed then remove it, though with a virgin Ubuntu install gdal should not be installed.


<br/>
## 3) Add Ubuntu extras & partner repositories ##

	echo "deb http://extras.ubuntu.com/ubuntu raring main" >> /etc/apt/sources.list
	echo "deb-src http://extras.ubuntu.com/ubuntu raring main" >> /etc/apt/sources.list
	echo "deb http://archive.canonical.com/ubuntu raring partner" >> /etc/apt/sources.list
	echo "deb-src http://archive.canonical.com/ubuntu raring partner" >> /etc/apt/sources.list
 	apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 16126D3A3E5C1192
 

<br/>
## 4) Install opengeo (geoserver) ##

Note: opengeo is really helpful in that it install a bunch of related spatial stuff.. including postgresql & postgis :-)


<br/>**add the opengeo apt key;**

	wget -qO- http://apt.opengeo.org/gpg.key | apt-key add -


<br/>**add opengeo to the apt repository list & update apt;**

    echo "deb http://apt.opengeo.org/suite/v3/ubuntu lucid main" >> /etc/apt/sources.list && apt-get update

<br/>**check that all the above has worled ok**

	apt-cache search opengeo

This should show a number of opengeo packages and NO error messages... if not, repeat above steps & troubleshoot until you get a happy response.


<br/>**install opengeo suite:**

	apt-get install opengeo-suite -y

use defaults for all questions and provide a sensible/safe geoserver password.  
Watch carefully for errors, especially gdal & postgis... these are fatal to opengeo working :-(  
Some psql errors should be OK.. such as creating test databases, schemas etc



<br/>
## 5) Test Geoserver is working OK##

**test it in a web browser**

**[http://xxx.xxx.xxx.xxx:8080/geoserver/](http://xxx.xxx.xxx.xxx:8080/geoserver/)**

<br/>
## 6) Install mongodb ##

**add apt repository key**

	apt-key adv --keyserver keyserver.ubuntu.com --recv 7F0CEB10

<br/>**add mongo sources to apt rep list and update apt**

	echo 'deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen' | sudo tee /etc/apt/sources.list.d/10gen.list && apt-get update

<br/>**install mongodb**
	
	apt-get install mongodb-10gen -y

<br/>**check that mongo is running OK**
	
	status mongodb	

This will return the process id (pid) eg;

	> mongodb start/running, process 10477


<br/>
## 7) Install node.js ##

**install prerequisites**

	apt-get install python-software-properties python g++ make software-properties-common -y

<br/>**add sources to apt rep list and update apt**

	add-apt-repository ppa:chris-lea/node.js && apt-get update

<br/>**install node.js**

	apt-get install nodejs -y


<br/>**check that node.js & npm are working OK**

	node -v && npm -v

these will return the version numbers for both node.js and npm (node package manager)

We'll cover setting up the node.js application(s) in other documents.


<br/>



----------

----------

Note: likely we won't use nginx webserver, instead node.js with Rackspace CDN... so this next chapter is for reference only.


## 8) Install nginx webserver ##


**add nginx to the apt repository list**

	echo "deb http://nginx.org/packages/ubuntu/ lucid nginx" >> /etc/apt/sources.list && echo "deb-src http://nginx.org/packages/ubuntu/ lucid nginx" >> /etc/apt/sources.list
 

<br/>**set a variable for the nginx version to be installed**

	nginx=stable 


<br/>**add the nginx apt key & update apt**

	add-apt-repository ppa:nginx/$nginx && 	apt-key adv --recv-keys --keyserver keyserver.ubuntu.com ABF5BD827BD9BF62 && apt-get update

note: we force the update keyserver as it is sometimes problematic

<br/>**install nginx**

	apt-get install nginx -y

<br/>**make sure nginx installed ok**

	nginx -v

this should return something like

	nginx version: nginx/1.4.1



<br/>
----------
**Version 1.0  
Ian Scrivener  
10/07/2013**







