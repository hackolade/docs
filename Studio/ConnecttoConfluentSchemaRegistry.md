# Connect to Confluent Schema Registry

The Confluent Schema Registry is accessible from targets Avro, JSON, and Protobuf, the 3 file formats supports by the registry.

&nbsp;

You must specify a friendly name for the connection, plus the registry URL.

![Confluent Schema Registry connection](<lib/Confluent%20Schema%20Registry%20connection.png>)

&nbsp;

The Authentication info depends on whether your instance is on-premises or in the Cloud.&nbsp; If in Confluent Cloud, you need to enter the API key and secret:

&nbsp;

![Confluent Schema Registry Cloud Auth](<lib/Confluent%20Schema%20Registry%20Cloud%20Auth.png>)

&nbsp;

If your instance is on premises, you must provide a username and password:

![Image](<lib/Confluent%20Schema%20Registry%20On-Prem%20Auth.png>)

&nbsp;

