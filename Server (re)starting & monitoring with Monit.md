# Server (re)starting & monitoring with Monit #


<br/>
**Install monit**

	apt-get install monit -y



<br/>
**add mail config to monit**

	nano /etc/monit/monitrc

add this is in the appropriate place

	set mailserver smtp.gmail.com port 587 username "bmrg.promap@domain.com" password "Bundaberg1" using tlsv1 with timeout 30 seconds
	set mail-format { from: bmrg.promap@gmail.com }
	set alert bmrg@zilogy.asia


also this

	set httpd port 2812 and
	use address localhost
	allow localhost

<br/>
**Config Monit for node.js**

Create a monit config file for the node Upstart service

	nano /etc/monit/conf.d/node.monit.conf


Append the following 


	check process node-app with pidfile /var/run/node.pid
	    start program = "/sbin/start node" with timeout 5 seconds
	    stop program  = "/sbin/stop node"
	    if failed port 80 protocol HTTP
	        request /
	        with timeout 3 seconds
	        then restart
	    if cpu > 80% for 10 cycles then restart
	    if 3 restarts within 10 cycles then timeout
	    group server

<br/>
**Config Monit for postgresql**

Create a monit config file for the postgresql init.d service

	nano /etc/monit/conf.d/postgrsql.monit.conf


Append the following 

	check process postgres with pidfile /var/run/postgresql/9.2-main.pid
	    start program = "/etc/init.d/postgresql start"
	    stop program = "/etc/init.d/postgresql stop"


<br/>
**Config Monit for tomcat6**

Create a monit config file for the tomcat6 init.d service

	nano /etc/monit/conf.d/tomcat6.monit.conf


Append the following 


	check process tomcat with pidfile /var/run/tomcat6.pid
	    start program = "/etc/init.d/tomcat6 start"
	    stop program = "/etc/init.d/tomcat6 stop"


	check host tomcat6 with address localhost 
		stop program = "/etc/init.d/tomcat6 stop" 
		start program = "/etc/init.d/tomcat6 restart" 
		if failed port 8080 and protocol http           
			then start


<br/>
**Config Monit for SSHD**

Create a monit config file for the SSHD Upstart service

	nano /etc/monit/conf.d/sshd.monit.conf


Append the following 

	check process sshd with pidfile /var/run/sshd.pid
	   start program  "/sbin/start sshd"      
	   stop program  "/sbin/stop sshd"         
	   if failed port 22 protocol ssh then restart
	   if 5 restarts within 5 cycles then timeout





<br/>
**Check monit config syntax**

	monit -t


<br/>


**Restart monit to effect changes**

	service monit restart


<br/>
**Check monit**

	monit status


<br/>
**View Monit log files**

	tail -n 50 /var/log/monit.log

