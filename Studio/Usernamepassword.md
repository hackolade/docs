# Username/password

In MongoDB's authentication model, a username is scoped to a database, called Authentication Database. The user’s privileges are not necessarily limited to this database. The user can have privileges in additional databases.

&nbsp;

If the field is left blank, the default value admin is used.

&nbsp;

For authentication methods other than User/Password authentication (like Kerberos, LDAP, X.509) the Authentication Database is always set to $external and no user input is required.

&nbsp;

![Reverse-Engineering - MongoDB Connection Settings](<lib/Rev-Eng - MongoDB Connection Settings.png>)

&nbsp;

## Example

Assuming a procedure as described [here](<https://docs.mongodb.com/manual/tutorial/enable-authentication/> "target=\"_blank\"") but with 'readWrite' rights:

&nbsp;

```json
use admin
db.createUser(
   {
      user: "myUserAdmin",
      pwd: "abc123",
      roles: [ 
         { 
            role: "readWrite", db: "admin" 
         } 
      ]
   }
)
```

&nbsp;

Restart the MongoDB instance with access control:\
`mongod --auth --port 27017 --dbpath /data/db1`

&nbsp;

To connect to this instance with Hackolade, the settings could be created as follows:\
Connection tab:\
![Reverse-engineering Mongo-username-password connection tab](<lib/Rev-Eng-Mongo-user-pwd connection tab.png>)

&nbsp;

and Authentication tab:\
![Reverse-engineering Mongo-username-password authentication tab](<lib/Rev-Eng-Mongo-user-pwd authenticationtab.png>)
