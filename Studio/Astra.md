---
description: Connect Hackolade Studio to a DataStax Astra database with the secure connect bundle and a token, for Cassandra reverse-engineering.
seoTitle: Connect to DataStax Astra (Cassandra as a service)
image: lib/DataStax Astra console - connect.png
---
# Astra

DataStax Astra (previously called Apollo) is a cloud-native DataBase-as-a-Service built on the DataStax distribution of Cassandra. DataStax is a cloud data platform with smart data management services to reduce operational complexity of Cassandra clusters. The Astra service is available on AWS, Azure and Google Cloud.

## Download a secure connect bundle

In the Astra console, select the database to which you would like to connect with Hackolade. Click on the Connect tab and select a driver, e.g. Node.js then click on the Download Bundle button

![DataStax Astra console - connect](<lib/DataStax Astra console - connect.png>)

In the Hackolade connection settings, choose the Installation option "DataStax Astra", then choose the downloaded secure-connect-\<database name>.zip file for the bundle.

![DataStax Astra connection settings](<lib/DataStax Astra connection settings.png>)

There are two ways to authenticate:

## Authenticate with username and password

You must manually enter your username and password in the Authentication tab, as they are not part of the secure bundle:

![Cassandra authentication](<lib/Cassandra authentication.png>)

## Authenticate with an authorization token

To obtain a token in the Astra console, go to the Settings tab then click on the Organization settings link under Application tokens. In the token management page, select a role with sufficient rights so Hackolade can performer reverse-engineering and optionally forward-engineering, then click on the Generate Token button.

![DataStax Astra console - token request](<lib/DataStax Astra console - token request.png>)

In the resulting screen, make sure to download the CSV:

![DataStax Astra - token request result](<lib/DataStax Astra - token request result.png>)

In the Hackolade Authentication tab, select the token-based type, and paste the token from either the Astra screen or from the CSV file:

![Cassandra connection auth token](<lib/Cassandra connection auth token.png>)
