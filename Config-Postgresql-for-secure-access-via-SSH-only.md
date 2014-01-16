# Config Postgresql for secure access via SSH only #


Edit the pg_hba.conf file

	nano /etc/postgresql/9.2/main/pg_hba.conf
		

Add a record to all IP connections form LOCALHOST only

	host all all 127.0.0.1/24 md5
	
Restart postgresql

	service postgresql restart