# Parquet schema

Hackolade easily imports the schema from .parquet files, located on your local file system or on a shared directory, to represent the corresponding Entity Relationship Diagram and schema structure.&nbsp; When multiple files are selected, you have the choice to either combine the schemas of the selected files (default), or to create a separate schema in the model for each selected file.

&nbsp;

![Parquet Cloud Selection - combine schemas](<lib/Cloud%20Selection%20-%20combine%20schemas.png>)

&nbsp;

Parquet files can also be reverse-engineered from AWS S3, Azure Blob Storage, and Google Cloud Storage.

&nbsp;

&nbsp;

## &#49;) AWS S3

Give a meaningful name to the connection to identify it for later, and provide proper URI to your S3 bucket, and optional folder path.

&nbsp;

![Parquet Cloud Storage - AWS S3 connection](<lib/Cloud%20Storage%20-%20AWS%20S3%20connection.png>)

&nbsp;

&nbsp;

If the S3 bucket is private, you must also provide authentication parameters (Access key id and Secret access key):

![parquet Cloud Storage - AWS S3 authentication](<lib/Cloud%20Storage%20-%20AWS%20S3%20authentication.png>)

&nbsp;

If you wish to handle AWS authentication through the [credentials file](<https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html> "target=\"\_blank\""), you may leave blank the Access Key ID and Secret Access Key fields, knowing that Hackolade supplies credentials following the recommendations described [here](<https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/setting-credentials-node.html> "target=\"\_blank\"").

&nbsp;

&nbsp;

## &#50;) Azure Blob Storage

Give a meaningful name to the connection to identify it for later, and provide proper Container name and Storage account name.

&nbsp;

![Parquet Cloud Storage - Azure connection](<lib/Cloud%20Storage%20-%20Azure%20connection.png>)

&nbsp;

If the storage account is private, you must also provide your Storage access key:

![Parquet Cloud Storage - Azure authentication](<lib/Cloud%20Storage%20-%20Azure%20authentication.png>)

&nbsp;

&nbsp;

If you wish to filter files, you may enter a file name prefix:

![Parquet Cloud Storage - Azure prefix](<lib/Cloud%20Storage%20-%20Azure%20prefix.png>)

&nbsp;

## &#51;) Google Cloud Storage

Give a meaningful name to the connection to identify it for later, and provide proper URI to your GCS bucket, and optional folder path.

![Parquet Cloud Storage - Google connection](<lib/Cloud%20Storage%20-%20Google%20connection.png>)

&nbsp;

If the&nbsp; bucket is private, you must also access to the Private key:

![Parquet Cloud Storage - Google authentication](<lib/Cloud%20Storage%20-%20Google%20authentication.png>)

&nbsp;

&nbsp;

