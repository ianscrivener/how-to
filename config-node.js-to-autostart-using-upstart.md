# Config node.js as an upstart service #

<br/>
**Create an upstart script;**

	nano /etc/init/node.conf

<br/>
**add code like this:**

	#!upstart
	description "node.js server"
	author      "Ian Scrivener"
	
	start on startup
	stop on shutdown
	
	# expect fork
	# use daemon
	
	script
	    export HOME=        "/root"
		echo 				$$ > /var/run/node.pid
	    cd                  /opt/promap/wwwroot
	    exec                /usr/bin/node /opt/promap/wwwroot/app.js 2>&1 >> /var/log/node.log
	end script
	
	
	pre-start script
	    # Date format same as (new Date()).toISOString() for consistency
	    echo "[`date -u +%Y-%m-%dT%T.%3AU`] (sys) Starting" >> /var/log/node.log
	end script
	
	post-start script
	   pgrep -f /usr/bin/node > /var/run/node.pid
	end script
	
	pre-stop script
	    rm /var/run/node.pid
	    echo "[`date -u +%Y-%m-%dT%T.%3AU`] (sys) Stopping" >> /var/log/node.log
	end script
	




<br/>
**Create & chmod the log file**

	touch /var/log/node.log
	chmod 666 /var/log/node.log


<br/>
**Usage**

	start node
	restart node
	stop node

<br/>
**View the upstart log**

	nano /var/log/upstart/node.log
