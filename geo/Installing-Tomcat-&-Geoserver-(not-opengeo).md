# Installing Tomcat & Geoserver (not opengeo) #


**Install Tomcat6**

	apt-get install update
	apt-get install upgrade
	apt-get install tomcat6
	chown tomcat6 /var/lib/tomcat6/ -R
	chown tomcat6 /usr/share/tomcat6/ -R

**Fix some things the install probably missed**

	mkdir /usr/share/tomcat6-admin
	mkdir /usr/share/tomcat6-admin/host-manager
	mkdir /usr/share/tomcat6-admin/manager
	chown tomcat6 /usr/share/tomcat6-admin -R
	chmod 777 /usr/share/tomcat6-admin -R
	mkdir /usr/share/tomcat6/server
	mkdir /usr/share/tomcat6/server/classes
	mkdir /usr/share/tomcat6/shared
	mkdir /usr/share/tomcat6/shared/classes
	chown tomcat6 /usr/share/tomcat6 -R

**Make Tomcat temp directory writeable**

	mkdir /tmp/tomcat6-tomcat6-tmp
	chown tomcat6 /tmp/tomcat6-tomcat6-tmp/
	chmod 666 /tmp/tomcat6-tomcat6-tmp/
	

**Stop tomcat6, delete logs, start**

	/etc/init.d/tomcat6 restart 
	/etc/init.d/tomcat6 stop 
	rm /var/log/tomcat6/* 
	/etc/init.d/tomcat6 start


**Check that Tomcat6 is running OK**

	cd /var/log/tomcat6
	# read the logs looking for issues & fix
	nano xxx
	nano yyy


**Install geoserver**
	cd /var/lib/tomcat6/webapps
	wget http://sourceforge.net/projects/geoserver/files/GeoServer/2.3.4/geoserver-2.3.4-war.zip

	unzip *.zip
	rm *.txt
	rm *.zip

Some geoserver cleanup
	rm /var/lib/tomcat6/webapps/geoserver/data/security/masterpw.info
	rm /var/lib/tomcat6/webapps/geoserver/data/security/users.properties.old

Restart tomcat & check logs for any isssues
	/etc/init.d/tomcat6 stop && rm /var/log/tomcat6/* && /etc/init.d/tomcat6 start
	cd /var/log/tomcat6
	nano xxx



----------
**Start/stop Tomcat6**
	
	/etc/init.d/tomcat6 restart
	/etc/init.d/tomcat6 start
	/etc/init.d/tomcat6 stop

	#clear logs
	/etc/init.d/tomcat6 stop && rm /var/log/tomcat6/* && /etc/init.d/tomcat6 start

**Log Locations**

	/var/lib/tomcat6/webapps/geoserver/data/logs/geoserver.log
	/var/log/tomcat6/

**Tomcat users**

	/etc/tomcat6/tomcat-users.xml
