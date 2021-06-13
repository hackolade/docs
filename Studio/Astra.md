# Astra

DataStax Astra (previously called Apollo) is a cloud-native DataBase-as-a-Service built on the DataStax distribution of Cassandra.&nbsp; DataStax is a cloud data platform with smart data management services to reduce operational complexity of Cassandra clusters.&nbsp; The Astra service is available on AWS, Azure and Google Cloud.

&nbsp;

## Download a secure connect bundle

In the Astra console, select the database to which you would like to connect with Hackolade.&nbsp; Click on the Connect tab and select a driver, e.g. Node.js then click on the Download Bundle button&nbsp;

&nbsp;

![Image](<lib/DataStax%20Astra%20console%20-%20connect.png>)

&nbsp;

&nbsp;

In the Hackolade connection settings, choose the Installation option "DataStax Astra", then choose the downloaded secure-connect-\<database name\>.zip file for the bundle.

&nbsp;

![Image](<lib/DataStax%20Astra%20connection%20settings.png>)

&nbsp;

&nbsp;

There are two ways to authenticate:

## Authenticate with username and password

You must manually enter your username and password in the Authentication tab, as they are not part of the secure bundle:

&nbsp;

![Image](<lib/Cassandra%20authentication.png>)

&nbsp;

## Authenticate with an authorization token

To obtain a token in the Astra console, go to the Settings tab then click on the Organization settings link under Application tokens.&nbsp; In the token management page, select a role with sufficient rights so Hackolade can performer reverse-engineering and optionally forward-engineering, then click on the Generate Token button.

&nbsp;

![Image](<lib/DataStax%20Astra%20console%20-%20token%20request.png>)

&nbsp;

In the resulting screen, make sure to download the CSV:

&nbsp;

![Image](<lib/DataStax%20Astra%20-%20token%20request%20result.png>)

&nbsp;

In the Hackolade Authentication tab, select the token-based type, and paste the token from either the Astra screen or from the CSV file:

&nbsp;

![Image](<lib/Cassandra%20connection%20auth%20token.png>)

