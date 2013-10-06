Spring Integration With Custom DB Connection Provider And MongoDB
=================================================================

This project provides spring integration with 
- Our own customized DataBase ConnectionProvider which is used by hibernate for DB connection.
- And MongoDB through JNDI using property file.

The dao objects of DB and MongoDB will be created during server startup. 
The spring is initialized by spring context loader during application server startup through web.xml.

applicationContext-springdao-config.xml - main spring application context.xml to load the db and mongodb objects.

++++ Our own customized DataBase ConnectionProvider

ConnectionProviderImpl.java, is a java class with implemented Connection provider to handle the db operations instead using the Apach DB Connection Source.
I only implemented getconnection and closeconnection.

In hibernate.properties, specify connection Provider class and other hibernate properties.

hibernate-config.xml  - read the hibernate properties and create session factory.


++++ MongoDB through JNDI using property file.

mongodb.properties - create this property with mongodb properties and place this file in webserver.

context.xml - create Jndi Env property having the location of mongodb properties

web.xml - create context load for spring initialization

mongodb-config.xml - read the mongodb properties file getting the file location from jndi.
					Pass it mongoBigDataFactory for creating the mongotemplate.
					
	
TestCustomDBAndMongoDB.java - test class shows to use both DB and MongoDB objects.



+++Contribution:
	
Thanks to Gopalakrishnan.P for support.				





