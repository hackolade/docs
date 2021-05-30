# Username/password

In MongoDB's authentication model, a username is scoped to a database, called Authentication Database. The user’s privileges are not necessarily limited to this database. The user can have privileges in additional databases.

&nbsp;

If the field is left blank, the default value admin is used.

&nbsp;

For authentication methods other than User/Password authentication (like Kerberos, LDAP, X.509) the Authentication Database is always set to $external and no user input is required.

&nbsp;

![Image](<lib/Rev-Eng%20-%20MongoDB%20Connection%20Settings.png>)

&nbsp;

### Example

Assuming a procedure as described [here](<https://docs.mongodb.com/manual/tutorial/enable-authentication/> "target=\"\_blank\"") but with 'readWrite' rights:

&nbsp;

use admin

db.createUser(

&nbsp; {

&nbsp; &nbsp; user: "myUserAdmin",

&nbsp; &nbsp; pwd: "abc123",

&nbsp; &nbsp; roles: \[ { role: "readWrite", db: "admin" } \]

&nbsp; }

)

&nbsp;

Restart the MongoDB instance with access control:&nbsp;

mongod --auth --port 27017 --dbpath /data/db1

&nbsp;

To connect to this instance with Hackolade, the settings could be created as follows:

Connection tab:

![Image](<lib/Rev-Eng-Mongo-user-pwd%20connection%20tab.png>)

&nbsp;

and Authentication tab:

![Image](<lib/Rev-Eng-Mongo-user-pwd%20authenticationtab.png>)

&nbsp;

