# Key-pair authentication

Snowflake supports using key pair authentication for enhanced authentication security as an alternative to basic authentication, such as username and password. This authentication method requires, as a minimum, a 2048-bit RSA key pair. You can generate the Privacy Enhanced Mail (PEM) private-public key pair using OpenSSL.

&nbsp;

The public key is assigned to the Snowflake user who uses the Snowflake client to connect and authenticate to Snowflake.

&nbsp;

Snowflake also supports rotating public keys in an effort to allow compliance with more robust security and governance postures.

&nbsp;

Below is a summary of the more [complete guide](<https://docs.snowflake.com/en/user-guide/key-pair-auth> "target=\"_blank\"") provided by Snowflake.

- **Step 1 create private key part:**

&nbsp;

To generate an unencrypted (without passphrase) key, execute the following command in terminal:

&nbsp;

```bash
openssl genrsa 2048 | openssl pkcs8 -topk8 -inform PEM -out rsa_key.p8 -nocrypt
```

&nbsp;

To generate an encrypted (with passphrase) key, use the following command, which omits -nocrypt:

&nbsp;

```bash
openssl genrsa 2048 | openssl pkcs8 -topk8 -v2 des3 -inform PEM -out rsa_key.p8
```

&nbsp;

***NOTE=*** *For encrypted key you will be forced to specify a passphrase right once the command is entered.*

&nbsp;

The commands generate a private key in PEM format.

- **Step 2 create public key part:**

&nbsp;

To generate the public key by referencing the private key execute the following command, which assumes the private key is stored in the file named rsa_key.p8:

&nbsp;

```bash
openssl rsa -in rsa_key.p8 -pubout -out rsa_key.pub
```

&nbsp;

- **Step 3 attach the generated key to the database user:**

&nbsp;

Login to the Snowflake instance with your credentials, create a new SQL worksheet (query data) and execute SQL command:

&nbsp;

```text
GRANT MODIFY PROGRAMMATIC AUTHENTICATION METHODS ON USER my_service_user
  TO ROLE my_service_owner_role;
```

&nbsp;

where my_service_user is your username you going to use in Hackolade in login window and my_service_owner_role the role name you want this user to have (PUBLIC, ACCOUNTADMIN etc.)

&nbsp;

Copy public key part from rsa_key.pub, everything in between:

&nbsp;

```text
-----BEGIN PUBLIC KEY-----
....
-----END PUBLIC KEY-----
```

&nbsp;

and attach the public part to the user by executing the following SQL command:

&nbsp;

```text
ALTER USER my_service_user SET RSA_PUBLIC_KEY='copied_public_key';
```

&nbsp;

where my_service_user is your username and copied_public_key is your copied public key.

&nbsp;

In order to confirm the correctness of public key attachment execute following commands:

&nbsp;

In Snowflake’s SQL worksheet:

&nbsp;

```text
DESC USER my_service_user
  ->> SELECT SUBSTR(
        (SELECT "value" FROM $1
           WHERE "property" = 'RSA_PUBLIC_KEY_FP'),
        LEN('SHA256:') + 1) AS key;
```

&nbsp;

In your OS terminal:

&nbsp;

```bash
openssl rsa -pubin -in rsa_key.pub -outform DER | openssl dgst -sha256 -binary | openssl enc -base64
```

&nbsp;

The output of the commands should be equal.

- **Step 4 connect using Hackolade Studio:**

&nbsp;

In order to connect using Key-Pair in Hackolade in Snowflake’s connection window switch to **Authentication** tab, select **Auth-type**: Key-Pair, specify your User name, Role name, path to Private key and Passphrase in case if you are using it.\
![Snowflake connection key-pair auth](<lib/Snowflake connection key-pair auth.png>)

&nbsp;

Click: Save → Connect and enjoy!
