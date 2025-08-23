# Key-pair authentication

Snowflake supports using key pair authentication for enhanced authentication security as an alternative to basic authentication, such as username and password.&nbsp; This authentication method requires, as a minimum, a 2048-bit RSA key pair. You can generate the Privacy Enhanced Mail (PEM) private-public key pair using OpenSSL.

&nbsp;

The public key is assigned to the Snowflake user who uses the Snowflake client to connect and authenticate to Snowflake.

&nbsp;

Snowflake also supports rotating public keys in an effort to allow compliance with more robust security and governance postures.

&nbsp;

Below is a summary of the more [complete guide](<https://docs.snowflake.com/en/user-guide/key-pair-auth> "target=\"\_blank\"") provided by Snowflake.

&nbsp;

* **Step 1 create private key part:**

To generate an unencrypted (without passphrase) key, execute the following command in terminal:

> &nbsp;

> openssl genrsa 2048 \| openssl pkcs8 -topk8 -inform PEM -out rsa\_key.p8 -nocrypt

&nbsp;

To generate an encrypted (with passphrase) key, use the following command, which omits -nocrypt:

&nbsp;

> openssl genrsa 2048 \| openssl pkcs8 -topk8 -v2 des3 -inform PEM -out rsa\_key.p8

&nbsp;

***NOTE=** For encrypted key you will be forced to specify a passphrase right once the command is entered.*

&nbsp;

The commands generate a private key in PEM format.

&nbsp;

* **Step 2 create public key part:**

To generate the public key by referencing the private key execute the following command, which assumes the private key is stored in the file named rsa\_key.p8:

&nbsp;

> openssl rsa -in rsa\_key.p8 -pubout -out rsa\_key.pub

> &nbsp;

* **Step 3 attach the generated key to the database user:**

Login to the Snowflake instance with your credentials, create a new SQL worksheet (query data) and execute SQL command:

&nbsp;

> GRANT MODIFY PROGRAMMATIC AUTHENTICATION METHODS ON USER my\_service\_user\
&nbsp; TO ROLE my\_service\_owner\_role;

> &nbsp;

where my\_service\_user is your username you going to use in Hackolade in login window and my\_service\_owner\_role the role name you want this user to have (PUBLIC, ACCOUNTADMIN etc.)

&nbsp;

Copy public key part from rsa\_key.pub, everything in between:

&nbsp;

> \-----BEGIN PUBLIC KEY-----\
....\
\-----END PUBLIC KEY-----

&nbsp;

and attach the public part to the user by executing the following SQL command:

&nbsp;

> ALTER USER my\_service\_user SET RSA\_PUBLIC\_KEY='copied\_public\_key';

&nbsp;

where my\_service\_user is your username and copied\_public\_key is your copied public key.

&nbsp;

In order to confirm the correctness of public key attachment execute following commands:

&nbsp;

In Snowflake’s SQL worksheet:

&nbsp;

> DESC USER my\_service\_user\
&nbsp; -\>\> SELECT SUBSTR(\
&nbsp;       (SELECT "value" FROM $1\
&nbsp;          WHERE "property" = 'RSA\_PUBLIC\_KEY\_FP'),\
&nbsp;       LEN('SHA256:') + 1) AS key;

&nbsp;

In your OS terminal:

&nbsp;

> openssl rsa -pubin -in rsa\_key.pub -outform DER \| openssl dgst -sha256 -binary \| openssl enc -base64

&nbsp;

The output of the commands should be equal.

&nbsp;

* **Step 4 connect using Hackolade Studio:**

In order to connect using Key-Pair in Hackolade in Snowflake’s connection window switch to **Authentication** tab, select **Auth-type**: Key-Pair, specify your User name, Role name, path to Private key and Passphrase in case if you are using it.

![Snowflake connection key-pair auth](<lib/Snowflake connection key-pair auth.png>)

&nbsp;

Click: Save → Connect and enjoy\!

&nbsp;

