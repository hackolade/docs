# JSON Schema

## From the file system

If you open a JSON Schema from the file system, Hackolade will detect its nature and will execute the reverse-engineering of that JSON Schema.&nbsp; You will need to choose a database target for your model.

&nbsp;

If you wish to include the schema for a JSON Schema file in an existing model, the process is slightly different.&nbsp; With your model already opened, choose Tools \> Reverse-Engineer \> JSON Schema. &nbsp;

&nbsp;

![Tools - Reverse-Engineer - JSON Schema](<lib/Tools%20-%20Reverse-Engineer%20-%20JSON%20Schema.png>)

&nbsp;

&nbsp;

&nbsp;

The structure of a JSON Schema can be imported either as an entity in the Entity Relationship Diagram, or alternatively as a model definition so it could be re-used in the model:

![JSON Schema reverse-engineering dialog](<lib/JSON%20Schema%20RE%20dialog.png>)

&nbsp;

If you wish to force the destination of the reverse-engineering operation, you may specify the container in which the entities should be inserted.

&nbsp;

For RDBMS targets, an additional option appears, that allows automatic normalization of complex data types:

&nbsp;

![JSON Schema reverse-engineering dialog - normalization](<lib/JSON%20Schema%20RE%20dialog%20-%20normalization.png>)

&nbsp;

&nbsp;

## From cloud storage and schema registries

JSON files and schemas can also be reverse-engineered from AWS S3, Azure Blob Storage/ADLS, and Google Cloud Storage.

![Cloud Selection - combine Avro schemas](<lib/Cloud%20Selection%20-%20combine%20schemas.png>)

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

## Azure Blob Storage and ADLS

Give a meaningful name to the connection to identify it for later, and provide proper Container name and Storage account name.

&nbsp;

**Note:** be careful to only mention the storage account name, i.e. NOT a full URL or anything other than the storage account name.

&nbsp;

![Cloud Storage - Azure connection avro schema](<lib/Cloud%20Storage%20-%20Azure%20connection.png>)

&nbsp;

If you wish to filter files, you may enter a file name prefix:

![Cloud Storage - Azure prefix blob name avro schema](<lib/Cloud%20Storage%20-%20Azure%20prefix.png>)

&nbsp;

### Anonymous Authentication

If the storage is public, you may choose the anonymous method:

![Cloud Storage - Azure anonymous auth](<lib/Cloud%20Storage%20-%20Azure%20anonymous%20auth.png>)

&nbsp;

If the storage account is private, Azure provides a choice of 3 methods with different levels of granularity depending on your security requirements:

### Storage Access Key

The [storage access key](<https://docs.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal> "target=\"\_blank\"") is similar to a root password for your storage account. Always be careful to protect your access keys. Microsoft recommends that you use Azure Key Vault to manage your access keys, and that you regularly rotate and regenerate your keys.

&nbsp;

![Cloud Storage - Azure Storage Access Key conf](<lib/Cloud%20Storage%20-%20Azure%20Storage%20Access%20Key%20conf.png>)

&nbsp;

&nbsp;

Select the authentication method and paste the key into the Storage Access Key field:

![Cloud Storage - Azure Storage Access Key auth](<lib/Cloud%20Storage%20-%20Azure%20Storage%20Access%20Key%20auth.png>)

&nbsp;

### Shared Access Signature

A [shared access signature (SAS)](<https://docs.microsoft.com/en-us/azure/storage/common/storage-sas-overview> "target=\"\_blank\"") provides secure delegated access to resources in your storage account, with granular control over how a client can access your data: user delegation, service or account.

&nbsp;

For Hackolade to be able to reverse-engineer, the minimum rights are as shown here:

![Cloud Storage - Azure Shared Access Sign conf](<lib/Cloud%20Storage%20-%20Azure%20Shared%20Access%20Sign%20conf.png>)

&nbsp;

&nbsp;

![Cloud Storage - Azure Shared Access Sign gen](<lib/Cloud%20Storage%20-%20Azure%20Shared%20Access%20Sign%20gen.png>)

&nbsp;

After clicking the button to generate, copy the SAS token from the Azure portal, and paste it in the SAS Token field:

![Cloud Storage - Azure SAS Token auth](<lib/Cloud%20Storage%20-%20Azure%20SAS%20Token%20auth.png>)

### Shared Access Token per container

It is possible to generate [tokens for specific containers](<https://docs.microsoft.com/en-us/azure/cognitive-services/translator/document-translation/create-sas-tokens?tabs=Containers> "target=\"\_blank\"") in the "Shared access tokens" menu option of the container:

![Cloud Storage - Azure Blob SAS Token conf](<lib/Cloud%20Storage%20-%20Azure%20Blob%20SAS%20Token%20conf.png>)

&nbsp;

&nbsp;

The minimum required rights for our reverse-engineering process to succeed are: read and list.

&nbsp;

![Cloud Storage - Azure Blob SAS Token gen](<lib/Cloud%20Storage%20-%20Azure%20Blob%20SAS%20Token%20gen.png>)

&nbsp;

&nbsp;

After clicking the button to generate, copy the Blob SAS token from the Azure portal, and paste it in the SAS Token field:

&nbsp;

![Cloud Storage - Azure Blob SAS Token auth](<lib/Cloud%20Storage%20-%20Azure%20Blob%20SAS%20Token%20auth.png>)

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

To connect to your schema registry instance in the cloud you first must obtain both an API key and API secret for it.&nbsp; They are found in the Schema Registry tab, in the API endpoint section:

![Confluent Schema Registry - API endpoint key](<lib/Confluent%20Schema%20Registry%20-%20API%20endpoint%20key.png>)

&nbsp;

&nbsp;

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
