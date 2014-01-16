# Tomcat & OpenGeo Admin Notes #

**Tomcat homepage** (http://bmrg-test.zilogy.asia:8080/)

	/var/lib/tomcat6/webapps/ROOT/index.html

**Tomcat users**

	/etc/tomcat6/tomcat-users.xml

**Various paths**

	/usr/share/tomcat6/
	
	/usr/share/opengeo-suite

**Log Files**

	/var/log/geoserver
	/var/log/tomcat6


/logs/opengeosuite.log


**Start/stop Tomcat6**
	
	/etc/init.d/tomcat6 restart
	/etc/init.d/tomcat6 start
	/etc/init.d/tomcat6 stop

**Tomcat Temp Files** (must be writeable - chmod 666)

	/tmp/tomcat6-tomcat6-tmp/


**Geoserver logging properties**

	/usr/share/opengeo-suite/geoserver/data/log


Geoserver Auth 

/usr/share/opengeo-suite-data/geoserver_data/security/usergroup/default/users.xml
/usr/share/opengeo-suite-data/geoserver_data/security/role/default/roles.xml 

http://docs.geoserver.org/stable/en/user/security/usergrouprole/roleservices.html