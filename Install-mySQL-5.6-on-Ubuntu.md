# Install mySQL 5.6 on Ubuntu #

<br/>
**Ensure a thorough uninstall of old mySQL version**

	apt-get update
	apt-get remove --purge mysql-server

	#uninstall apparmour as it is known to argue with mysql
	apt-get remove apparmour
	
	# major apt spring clean
	apt-get autoremove
	apt-get clean
	apt-get purge

	# make sure there are no mySQL leftovers
	find / -iname mysql


<br/>

**Install mysql 5.6**

	apt-get install libaio-dev

	#get the deb
	cd /tmp
	wget http://dev.mysql.com/get/Downloads/MySQL-5.6/mysql-5.6.12-debian6.0-x86_64.deb/from/http://cdn.mysql.com/
	mv index.html mysql5.6.deb
	

	# install deb
	dpkg -i mysql5.6.deb
	
	# delete the install file
	rm mysql5.6.deb

	# add group & user
	groupadd mysql
	useradd -r -g mysql mysql
	

	# goto the install directory
	cd /opt/mysql/server-5.6
	
	# create directory for data & chown it msql
	mkdir data
	chown mysql:mysql data
	
	# run install script
	scripts/mysql_install_db --user=mysql

	# move the config files t the right places
	cp support-files/my-default.cnf /etc/my.cnf
	cp support-files/mysql.server /etc/init.d/mysql.server
	cp support-files/mysql-log-rotate /etc/logrotate.d/mysql.server

	# config PATH so you can run 'mysql' command in any path
	echo export PATH=$PATH:/opt/mysql/server-5.6/bin

	# you may need to restart you CLI client for path to take effect
	

	#Start mySQL 5.6
	service mysql.server start
	service mysql start

<br/>
**Setup root password**

	/opt/mysql/server-5.6/bin/mysql
	UPDATE mysql.user SET Password=PASSWORD('Bundaberg1') WHERE User='root';
	GRANT ALL ON *.* TO 'ian'@'localhost' IDENTIFIED BY 'sleepyman';
	GRANT ALL ON *.* TO 'fred'@'localhost' IDENTIFIED BY 'Bundaberg1';
	GRANT ALL ON *.* TO 'geoserver'@'localhost' IDENTIFIED BY 'Bundaberg1';
	FLUSH PRIVILEGES;

