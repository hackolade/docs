# Avro file or schema

Hackolade easily imports the schema from .avsc or .avro files, located on your local file system or on a shared directory, to represent the corresponding Entity Relationship Diagram and schema structure.&nbsp; When multiple files are selected, you have the choice to either combine the schemas of the selected files (default), or to create a separate schema in the model for each selected file.

&nbsp;

![Image](<lib/Cloud%20Selection%20-%20combine%20schemas.png>)

&nbsp;

Avro files and schemas can also be reverse-engineered from AWS S3, Azure Blob Storage, and Google Cloud Storage.

&nbsp;

## AWS S3

Give a meaningful name to the connection to identify it for later, and provide proper URI to your S3 bucket, and optional folder path.

&nbsp;

![Image](<lib/Cloud%20Storage%20-%20AWS%20S3%20connection.png>)

&nbsp;

&nbsp;

If the S3 bucket is private, you must also provide authentication parameters (Access key id and Secret access key):

![Image](<lib/Cloud%20Storage%20-%20AWS%20S3%20authentication.png>)

&nbsp;

If you wish to handle AWS authentication through the [credentials file](<https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html> "target=\"\_blank\""), you may leave blank the Access Key ID and Secret Access Key fields, knowing that Hackolade supplies credentials following the recommendations described [here](<https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/setting-credentials-node.html> "target=\"\_blank\"").

&nbsp;

&nbsp;

## Azure Blob Storage

Give a meaningful name to the connection to identify it for later, and provide proper Container name and Storage account name.

&nbsp;

![Image](<lib/Cloud%20Storage%20-%20Azure%20connection.png>)

&nbsp;

If the storage account is private, you must also provide your Storage access key:

![Image](<lib/Cloud%20Storage%20-%20Azure%20authentication.png>)

&nbsp;

&nbsp;

If you wish to filter files, you may enter a file name prefix:

![Image](<lib/Cloud%20Storage%20-%20Azure%20prefix.png>)

&nbsp;

## Google Cloud Storage

Give a meaningful name to the connection to identify it for later, and provide proper URI to your GCS bucket, and optional folder path.

![Image](<lib/Cloud%20Storage%20-%20Google%20connection.png>)

&nbsp;

If the&nbsp; bucket is private, you must also access to the Private key:

![Image](<lib/Cloud%20Storage%20-%20Google%20authentication.png>)

&nbsp;

&nbsp;

## Confluent Schema Registry on Confluence Cloud

Give a meaningful name to the connection to identify it for later, choose Cloud as a source, and provide the URL to your Schema Registry:

&nbsp;

![Image](<lib/Confluent%20Schema%20Registry%20-%20Cloud%20connection.png>)

&nbsp;

Then provide the API key and API secret:

![Image](<lib/Confluence%20Schema%20Registry%20-%20Cloud%20auth.png>)

&nbsp;

## Confluence Schema Registry on-premises

Give a meaningful name to the connection to identify it for later, choose on-premise as a source, and provide the URL to your Schema Registry:

![Image](<lib/Confluent%20Schema%20Registry%20-%20on-premconnection.png>)

&nbsp;

Then provide your username and password:

![Image](<lib/Confluent%20Schema%20Registry%20-%20on-prem%20auth.png>)

&nbsp;

&nbsp;

## Azure Schema Registry for Event Hubs

Give a meaningful name to the connection to identify it for later, choose Azure Schema Registry, and provide the URL to your Schema Registry:&nbsp; Currently, it is not possible to automatically retrieve the list of Schema Groups, so you should provide the Schema Group concerned.&nbsp; If you need to access more than one Schema Group, you may create one connection per Schema Group.

![Image](<lib/Azure%20Schema%20Registry%20connection%20settings.png>)

&nbsp;

Then you need to provide the authentication parameters:

![Image](<lib/NewItem2.png>)

&nbsp;

Hackolade communicates with the Azure Schema Registry via REST APIs.&nbsp; If you already use Hackolade for Cosmos DB, the following steps may have already been performed.&nbsp; Otherwise, please follow the instructions below:

&nbsp;

The Hackolade application must be registered so Azure accepts the REST API calls, as per these [instructions](<https://docs.microsoft.com/en-us/azure/active-directory/develop/howto-create-service-principal-portal> "target=\"\_blank\"").&nbsp; The **Application (client) ID** and the **Directory (tenant) ID** are retrieved are retrieved from the App registration Overview screen:

![Image](<lib/CosmosDB%20-%20Azure%20App%20registration%20overview.png>)

&nbsp;

**Note:** it is critical to assign the proper role to the application just registered.&nbsp; This is done following the steps outlined [here](<https://docs.microsoft.com/en-us/azure/role-based-access-control/role-assignments-portal> "target=\"\_blank\"").&nbsp;

![Image](<lib/CosmosDB%20-%20Azure%20IAM%20role%20assignment.png>)

&nbsp;

Finally, the **Application secret** is obtained from the Certificates \& secrets screen of the App registration:&nbsp;

![Image](<lib/CosmosDB%20-%20Azure%20App%20registration%20secrets%20scr.png>)

&nbsp;

If you don't know how to generate some of the above values, you may want to consult this [document](<https://github.com/Azure/azure-libraries-for-net/blob/master/AUTH.md> "target=\"\_blank\"").

&nbsp;

&nbsp;

&nbsp;

