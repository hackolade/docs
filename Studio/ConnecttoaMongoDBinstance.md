# Connect to a MongoDB instance

IMPORTANT NOTE: Reading from a secondary in a replica set:

While it may be tempting to read from a secondary for performance reasons, it should be noted that:

\- the sampling by Hackolade, unless set by the user to a very high number, should be insignificant in terms of load on the database

\- MongoDB Validator parameters are not replicated to secondaries.&nbsp; If you use this function, Hackolade will not have access to those parameter for the schema inference process, if you don't read from the primary.

&nbsp;

Authentication is the process of verifying the identity of a client. When access control, i.e. authorization, is enabled, MongoDB requires all clients to authenticate themselves in order to allow access.

&nbsp;

MongoDB supports a number of authentication mechanisms that clients can use to verify their identity. These mechanisms allow MongoDB to integrate into an existing authentication system:

&nbsp;

* SCRAM-SHA-1 or MONGODB-CR [username/password](<Usernamepassword.md>) authentication (SCRAM-SHA-256 will be supported when MongoDB v4.0 comes out)
* Cloud-based [MongoDB Atlas](<MongoDBAtlas.md>)
* [SSL](<SSL.md>) certificate authentication
* [X.509](<X509.md>) authentication
* [LDAP](<LDAP.md>) proxy authentication
* [Kerberos](<Kerberos.md>) authentication
* for access to a MongoDB instance in the Cloud, you may need [SSH tunneling](<SSH.md>).

&nbsp;

The Connection Settings dialog lets define the parameters in different tabs, as needed: &nbsp;

&nbsp;

![Image](<lib/Rev-Eng%20Connection%20settings%20-%20Direct.png>)

These parameters are assembled by Hackolade to create the full connection string when establishing the connection during the Reverse-Engineering process.

&nbsp;

***TIP***: if you have instances with a very large number of databases, you may wish to declare a particular database directly in the connection string by appending the address with: /\<name of the database you wish to access directly\>, for example: localhost/NBA

