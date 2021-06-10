# Authentication Failed Error Message

The "authentication failed" error message is often the result of one of five conditions.

* Password is missing after copying connection string from the Atlas web page.  This is a security precaution, so you should enter the password manually in the Hackolade connection window.
* Username and password mismatch
* No user account exists in a new **Atlas** project under [Clusters: Security: MongoDB Users](<https://docs.atlas.mongodb.com/security-add-mongodb-users/>) or in your instance
* Not specifying any or the correct "Authentication Database", (aka authSource), usually "admin"
* Selecting an incorrect "Authentication" method

&nbsp;

&nbsp;

We recommend that you double-check the username and password, make sure the MongoDB user exists, verify the correct authentication database and make sure the authentication mechanism is supported by your MongoDB database.

For further troubleshooting:

* If you are using Atlas, please refer the instructions on the [Atlas Connect](<https://docs.atlas.mongodb.com/compass-connection/>).
- You may find the [Connect to MongoDB](<https://docs.mongodb.com/compass/current/connect/>) documentation a helpful resource.
* Are you able to successfully connect to the server using the [mongo shell](<https://docs.mongodb.com/manual/mongo/>)? If not, this suggests a potential problem with your database credentials.  In that case, please contact your database administrator.  If you are able to connect via the [mongo shell](<https://docs.mongodb.com/manual/mongo/>), please provide the relevant shell connection settings and a screenshot of the error in the Compass connection dialog.

&nbsp;

