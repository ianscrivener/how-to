# Setting up geoserver auth with mySQL #


1) add 2 roles to 'default' roles: '**bmrg\_user\_roles**', '**bmrg\_admin\_roles**'   
*(Note: this uses the xml file on the server)*

2) Add a new entry for **User Group Services** named '**mysql\_group\_service**' - JDBC connecting to **geoserver\_auth mySql** database

3) in '**mysql\_group\_service**' create 2 groups;  
3.1) '**bmrg\_user\_group**' with roles '**bmrg\_user\_role**'  
3.2) '**bmrg\_admin\_group**' with roles '**bmrg\_user\_role**' & 'bmrg\_admin\_role'  

4) create administrators with groups	'**bmrg\_user\_group**' & '**bmrg\_admin\_group**'	

5) create users with groups	'**bmrg\_user\_group**' only

6) Set **Data** & **Services** security access as required... suggest restricting all access to '**bmrg\_user\_roles**', '**bmrg\_admin\_roles**' only.

