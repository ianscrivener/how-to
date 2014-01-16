# Installing mySQL geoserver extension #

see [http://docs.geoserver.org/2.1.1/user/data/mysql.html](http://docs.geoserver.org/2.1.1/user/data/mysql.html "http://docs.geoserver.org/")


MAKE SURE YOU MATCH THE PLUGIN VERSION WITH GEOSERVER VERSION

**ie**
	
	sudo su
	cd /tmp
	mkdir mysql-ext
	cd /tmp/mysql-ext
	wget http://sourceforge.net/projects/geoserver/files/GeoServer%20Extensions/2.3.4/geoserver-2.3.4-mysql-plugin.zip
	unzip *.zip
	

	# for tomcat
	mv *.jar /var/lib/tomcat6/webapps/geoserver/WEB-INF/lib/

	# for jetty
	cp *mysql*.jar /opt/jetty/webapps/geoserver/WEB-INF/lib/
	
	# clean up
	cd ../
	rm -rf mysql-ext
	
		





