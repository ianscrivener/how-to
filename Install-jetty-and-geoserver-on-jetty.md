# Install jetty and geoserver on jetty #


**install & setup openJDK**

	apt-get install openjdk-7-jdk
	mkdir /usr/java
	# setup a symbolic link from your openJDK to the java path that jetty looks for 
	ln -s /usr/lib/jvm/java-7-openjdk-amd64 /usr/java/default

**install jetty**

	cd /opt
	wget http://mirrors.ustc.edu.cn/eclipse/jetty/stable-9/dist/jetty-distribution-9.0.4.v20130625.zip
	unzip *.zip
	rm *.zip
	mv jetty-distribution-9.0.4.v20130625/ jetty
	useradd jetty -U -s /bin/false
	chown -R jetty:jetty /opt/jetty

**create the jetty service**

	
	cp /opt/jetty/bin/jetty.sh /etc/init.d/jetty
	nano /etc/default/jetty # and copy the content below


**add the following to /etc/init.d/jetty, save, close**

	JAVA_HOME=/usr/java/default
	NO_START=0
	JETTY_HOST=0.0.0.0
	JETTY_PORT=8000
	JETTY_USER=jetty


**register the startup service**

	update-rc.d jetty defaults


**start jetty**

	service jetty start


**check its OK with your browser**

[http://localhost:8000](http://localhost:8000 "http://localhost:8000")


## Install geoserver ##

if you already have installed geoserver on tomcat you can do this

	cp /var/lib/tomcat6/webapps/geoserver.war /opt/jetty/webapps/
	service jetty restart

or else, 
	cd /opt/jetty/webapps
	wget http://sourceforge.net/projects/geoserver/files/GeoServer/2.3.4/geoserver-2.3.4-war.zip

	unzip *.zip
	rm *.txt
	rm *.zip

