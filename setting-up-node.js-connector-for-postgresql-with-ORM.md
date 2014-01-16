# Postgresql & node.js #



<br/>**install ubuntu pg driver**

	apt-get install libpq-dev



<br/>**npm install node.js pg driver**

	npm install pg


<br/>**Install PG ORM Module**

	npm install orm


## Testing ##

<br/> **(1) Test that the pg drivers works OK**


	var pg = require('pg'); 
	//or native libpq bindings
	//var pg = require('pg').native
	
	//var conString = "tcp://postgres:1234@localhost/postgres";
	
	var conString= "tcp://opengeo:opengeo@localhost/bmrg";
	
	
	var client = new pg.Client(conString);
	client.connect(function(err) {
	  if(err) {
	    return console.error('could not connect to postgres', err);
	  }
	  client.query('SELECT NOW() AS "theTime"', function(err, result) {
	    if(err) {
	      return console.error('error running query', err);
	    }
	    console.log(result.rows[0].theTime);
	    //output: Tue Jan 15 2013 19:12:47 GMT-600 (CST)
	    client.end();
	  });
	});


Result should be like:

	Mon Jul 15 2013 08:22:01 GMT+0000 (UTC)



<br/> **(1) Test that the node 'orm' module works OK**