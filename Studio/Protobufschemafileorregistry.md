# Protobuf schema file or registry

Hackolade easily imports the schema from .proto files, version 2 and 3, located on your local file system or on a shared directory, to represent the corresponding Entity Relationship Diagram and schema structure.&nbsp; When multiple files are selected, you have the choice to either combine the schemas of the selected files (default), or to create a separate schema in the model for each selected file.

&nbsp;

![Cloud Selection - combine Avro schemas](<lib/Cloud%20Selection%20-%20combine%20schemas.png>)

&nbsp;

Protobuf files and schemas can also be reverse-engineered from AWS S3, Azure Blob Storage, and Google Cloud Storage.

&nbsp;

## AWS S3

Give a meaningful name to the connection to identify it for later, and provide proper URI to your S3 bucket, and optional folder path.

&nbsp;

![Cloud Storage - AWS S3 connection for Avro schema](<lib/Cloud%20Storage%20-%20AWS%20S3%20connection.png>)

&nbsp;

&nbsp;

If the S3 bucket is private, you must also provide authentication parameters (Access key id and Secret access key):

![Cloud Storage - AWS S3 authentication avro schema](<lib/Cloud%20Storage%20-%20AWS%20S3%20authentication.png>)

&nbsp;

If you wish to handle AWS authentication through the [credentials file](<https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html> "target=\"\_blank\""), you may leave blank the Access Key ID and Secret Access Key fields, knowing that Hackolade supplies credentials following the recommendations described [here](<https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/setting-credentials-node.html> "target=\"\_blank\"").

&nbsp;

&nbsp;

## Azure Blob Storage

Give a meaningful name to the connection to identify it for later, and provide proper Container name and Storage account name.

&nbsp;

![Cloud Storage - Azure connection avro schema](<lib/Cloud%20Storage%20-%20Azure%20connection.png>)

&nbsp;

If the storage account is private, you must also provide your Storage access key:

![Cloud Storage - Azure authentication avro schema](<lib/Cloud%20Storage%20-%20Azure%20authentication.png>)

&nbsp;

&nbsp;

If you wish to filter files, you may enter a file name prefix:

![Cloud Storage - Azure prefix blob name avro schema](<lib/Cloud%20Storage%20-%20Azure%20prefix.png>)

&nbsp;

## Google Cloud Storage

Give a meaningful name to the connection to identify it for later, and provide proper URI to your GCS bucket, and optional folder path.

![Cloud Storage - Google connection avro schema](<lib/Cloud%20Storage%20-%20Google%20connection.png>)

&nbsp;

If the&nbsp; bucket is private, you must also access to the Private key:

![Cloud Storage - Google authentication avro schema](<lib/Cloud%20Storage%20-%20Google%20authentication.png>)

&nbsp;

&nbsp;

## Confluent Schema Registry on Confluence Cloud

Give a meaningful name to the connection to identify it for later, choose Cloud as a source, and provide the URL to your Schema Registry:

&nbsp;

![Confluent Schema Registry - Cloud connection avro schema](<lib/Confluent%20Schema%20Registry%20-%20Cloud%20connection.png>)

&nbsp;

Then provide the API key and API secret:

![Confluence Schema Registry - Cloud auth avro schema](<lib/Confluence%20Schema%20Registry%20-%20Cloud%20auth.png>)

&nbsp;

## Confluence Schema Registry on-premises

Give a meaningful name to the connection to identify it for later, choose on-premise as a source, and provide the URL to your Schema Registry:

![Confluent Schema Registry - on-prem connection avro schema](<lib/Confluent%20Schema%20Registry%20-%20on-premconnection.png>)

&nbsp;

Then provide your username and password:

![Confluent Schema Registry - on-prem auth avro schema](<lib/Confluent%20Schema%20Registry%20-%20on-prem%20auth.png>)

&nbsp;

## Pulsar Schema Registry

Give a meaningful name to the connection to identify it for later, choose the Pulsar connection type, provide the URL to your Schema Registry

![Pulsar connection settings avro schema](<lib/Pulsar%20connection%20settings.png>)

