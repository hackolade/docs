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

![Reverse-Engineering MongoDB Connection settings - Direct](<lib/Rev-Eng%20Connection%20settings%20-%20Direct.png>)

These parameters are assembled by Hackolade to create the full connection string when establishing the connection during the Reverse-Engineering process.

&nbsp;

***TIP***: if you have instances with a very large number of databases, you may wish to declare a particular database directly in the connection string by appending the address with: /\<name of the database you wish to access directly\>, for example: localhost/NBA

&nbsp;

&nbsp;

## Field-Level Encryption

Hackolade supports MongoDB's Field-Level Encryption framework.&nbsp; More details can be found [here](<MongoDBField-LevelEncryption.md>). &nbsp; To apply forward-engineering script with FLE parameters to a MongoDB instance or reverse-engineer the actual data types of encrypted fields, you need to pass additional information during the connection.

&nbsp;

We assume that your instance is set up according to this MongoDB [field-level encryption guide](<https://www.mongodb.com/docs/drivers/security/client-side-field-level-encryption-guide/> "target=\"\_blank\"") (here's another [useful guide](<https://betterprogramming.pub/the-guide-to-mongodb-field-level-encryption-55c5b0b90bf7> "target=\"\_blank\"").)&nbsp; You must also have installed the MongoDB [mongocryptd component ](<https://www.mongodb.com/docs/manual/reference/security-client-side-encryption-appendix/#installation> "target=\"\_blank\"")included in the MongoDB Enterprise Server package.

&nbsp;

![MongoDB field-level encryption connection](<lib/MongoDB%20field-level%20encryption%20connection.png>)

&nbsp;

The MongoDB driver stores the key in a key vault collection where FLE-enabled clients can access the key for automatic encryption and decryption.&nbsp; The key vault namespace (database and collection) must be specified separately:

**Key Vault Database:** specify the KV DB, for example encryption

**Key Vault Collection:** specify the KV collection, for example \_\_keyvault

&nbsp;

The client uses the KMS provider settings to discover the master key.

![MongoDB FLE KMS Providers](<lib/MongoDB%20FLE%20KMS%20Providers.png>)

&nbsp;

**KMS Provider:** select the provider of your choice.&nbsp; Depending on the KMS provider, additional parameters are required.

&nbsp;

&nbsp;

The MongoDB client communicates with a separate encryption application called mongocryptd which automates the client-side field level encryption. &nbsp;

&nbsp;

**Mongocryptd:** you must specify the location of this component, either a with a path and executable filename:

![MongoDB FLE mongocryptd path](<lib/MongoDB%20FLE%20mongocryptd%20path.png>)

&nbsp;

or URI and port:

![MongoDB FLE mongocryptd URI and port](<lib/MongoDB%20FLE%20mongocryptd%20URI%20and%20port.png>)

&nbsp;

&nbsp;

