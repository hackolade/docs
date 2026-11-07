---
description: Import schemas from .parquet files on your file system, AWS S3, Azure Blob Storage or Google Cloud Storage into Hackolade Studio.
seoTitle: Reverse-engineer Parquet files
image: lib/Cloud Storage - AWS S3 connection.png
---
# Parquet schema

Hackolade easily imports the schema from .parquet files, located on your local file system or on a shared directory, to represent the corresponding Entity Relationship Diagram and schema structure. When multiple files are selected, you have the choice to either combine the schemas of the selected files (default), or to create a separate schema in the model for each selected file.

![Parquet Cloud Selection - combine schemas](<lib/Cloud Selection - combine schemas.png>)

Parquet files can also be reverse-engineered from AWS S3, Azure Blob Storage/ADLS, and Google Cloud Storage.

## AWS S3

Give a meaningful name to the connection to identify it for later, and provide proper URI to your S3 bucket, and optional folder path.

![Parquet Cloud Storage - AWS S3 connection](<lib/Cloud Storage - AWS S3 connection.png>)

If the S3 bucket is private, you must also provide authentication parameters (Access key id and Secret access key):\
![parquet Cloud Storage - AWS S3 authentication](<lib/Cloud Storage - AWS S3 authentication.png>)

If you wish to handle AWS authentication through the [credentials file](<https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html> "target=\"_blank\""), you may leave blank the Access Key ID and Secret Access Key fields, knowing that Hackolade Studio supplies credentials following the recommendations described [here](<https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/setting-credentials-node.html> "target=\"_blank\"").

## Azure Blob Storage and ADLS

Give a meaningful name to the connection to identify it for later, and provide proper Container name and Storage account name.

> [!NOTE]
> Be careful to only mention the storage account name, i.e. NOT a full URL or anything other than the storage account name.

![Cloud Storage - Azure connection avro schema](<lib/Cloud Storage - Azure connection.png>)

If you wish to filter files, you may enter a file name prefix:\
![Cloud Storage - Azure prefix blob name avro schema](<lib/Cloud Storage - Azure prefix.png>)

### Anonymous Authentication

If the storage is public, you may choose the anonymous method:\
![Cloud Storage - Azure anonymous auth](<lib/Cloud Storage - Azure anonymous auth.png>)

If the storage account is private, Azure provides a choice of 3 methods with different levels of granularity depending on your security requirements:

### Storage Access Key

The [storage access key](<https://docs.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal> "target=\"_blank\"") is similar to a root password for your storage account. Always be careful to protect your access keys. Microsoft recommends that you use Azure Key Vault to manage your access keys, and that you regularly rotate and regenerate your keys.

![Cloud Storage - Azure Storage Access Key conf](<lib/Cloud Storage - Azure Storage Access Key conf.png>)

Select the authentication method and paste the key into the Storage Access Key field:\
![Cloud Storage - Azure Storage Access Key auth](<lib/Cloud Storage - Azure Storage Access Key auth.png>)

### Shared Access Signature

A [shared access signature (SAS)](<https://docs.microsoft.com/en-us/azure/storage/common/storage-sas-overview> "target=\"_blank\"") provides secure delegated access to resources in your storage account, with granular control over how a client can access your data: user delegation, service or account.

For Hackolade to be able to reverse-engineer, the minimum rights are as shown here:\
![Cloud Storage - Azure Shared Access Sign conf](<lib/Cloud Storage - Azure Shared Access Sign conf.png>)

![Cloud Storage - Azure Shared Access Sign gen](<lib/Cloud Storage - Azure Shared Access Sign gen.png>)

After clicking the button to generate, copy the SAS token from the Azure portal, and paste it in the SAS Token field:\
![Cloud Storage - Azure SAS Token auth](<lib/Cloud Storage - Azure SAS Token auth.png>)

### Shared Access Token per container

It is possible to generate [tokens for specific containers](<https://docs.microsoft.com/en-us/azure/cognitive-services/translator/document-translation/create-sas-tokens?tabs=Containers> "target=\"_blank\"") in the "Shared access tokens" menu option of the container:\
![Cloud Storage - Azure Blob SAS Token conf](<lib/Cloud Storage - Azure Blob SAS Token conf.png>)

The minimum required rights for our reverse-engineering process to succeed are: read and list.

![Cloud Storage - Azure Blob SAS Token gen](<lib/Cloud Storage - Azure Blob SAS Token gen.png>)

After clicking the button to generate, copy the Blob SAS token from the Azure portal, and paste it in the SAS Token field:

![Cloud Storage - Azure Blob SAS Token auth](<lib/Cloud Storage - Azure Blob SAS Token auth.png>)

## Google Cloud Storage

Give a meaningful name to the connection to identify it for later, and provide proper URI to your GCS bucket, and optional folder path.\
![Parquet Cloud Storage - Google connection](<lib/Cloud Storage - Google connection.png>)

If the bucket is private, you must also access to the Private key:\
![Parquet Cloud Storage - Google authentication](<lib/Cloud Storage - Google authentication.png>)
