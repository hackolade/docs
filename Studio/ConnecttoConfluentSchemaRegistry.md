---
description: Connect Hackolade Studio to Confluent Schema Registry on Confluent Cloud or Platform, to reverse-engineer Avro, JSON and Protobuf schemas.
seoTitle: Connect to Confluent Schema Registry
image: lib/Confluent Schema Registry connection.png
---
# Connect to Confluent Schema Registry

The Confluent Schema Registry is accessible from targets Avro, JSON, and Protobuf, the 3 file formats supports by the registry.

You must specify a friendly name for the connection, plus the registry URL.\
![Confluent Schema Registry connection](<lib/Confluent Schema Registry connection.png>)

To get the Schema Registry URL REST ENDPOINT, do one of the following:

- From the Confluent Cloud Console ([https://confluent.cloud/](https://confluent.cloud/)), navigate to an environment with a Schema Registry enabled to view the value given for “Endpoint” under “Stream Governance API” on the right panel.\
  ![Confluent Schema Registry endpoint URL](<lib/Confluent Schema Registry endpoint URL.png>)
- From the Confluent CLI, run [confluent schema-registry cluster describe](https://docs.confluent.io/confluent-cli/current/command-reference/schema-registry/cluster/confluent_schema-registry_cluster_describe.html) to view the value given for `Endpoint URL`.

The Authentication info depends on whether your instance is on-premises or in the Cloud. If in Confluent Cloud, you need to enter the API key and secret, as created for the REST endpoint:

![Confluent Schema Registry Cloud Auth](<lib/Confluent Schema Registry Cloud Auth.png>)

If your instance is on premises, you must provide a username and password:\
![Confluent Schema Registry On-Prem Auth](<lib/Confluent Schema Registry On-Prem Auth.png>)
