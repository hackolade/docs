# Connect to Confluent Schema Registry

The Confluent Schema Registry is accessible from targets Avro, JSON, and Protobuf, the 3 file formats supports by the registry.

&nbsp;

You must specify a friendly name for the connection, plus the registry URL.

![Confluent Schema Registry connection](<lib/Confluent Schema Registry connection.png>)

&nbsp;

&nbsp;

To get the Schema Registry URL REST ENDPOINT, do one of the following:

* From the Confluent Cloud Console ([https://confluent.cloud/](<https://confluent.cloud/>)), navigate to an environment with a Schema Registry enabled to view the value given for “Endpoint” under “Stream Governance API” on the right panel.\
![Confluent Schema Registry endpoint URL](<lib/Confluent Schema Registry endpoint URL.png>)
* From the Confluent CLI, run [confluent schema-registry cluster describe](<https://docs.confluent.io/confluent-cli/current/command-reference/schema-registry/cluster/confluent\_schema-registry\_cluster\_describe.html>) to view the value given for Endpoint URL.

&nbsp;

&nbsp;

The Authentication info depends on whether your instance is on-premises or in the Cloud.&nbsp; If in Confluent Cloud, you need to enter the API key and secret, as created for the REST endpoint:

&nbsp;

![Confluent Schema Registry Cloud Auth](<lib/Confluent Schema Registry Cloud Auth.png>)

&nbsp;

If your instance is on premises, you must provide a username and password:

![Image](<lib/Confluent Schema Registry On-Prem Auth.png>)

&nbsp;

