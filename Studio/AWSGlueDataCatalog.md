# Glue Data Catalog

AWS Glue is a fully managed extract, transform, and load (ETL).&nbsp; AWS Glue discovers data and stores the associated metadata (e.g. table definition and schema) in the AWS Glue Data Catalog.&nbsp; Once cataloged,&nbsp; data is immediately searchable, queryable, and available for ETL.&nbsp; The AWS Glue Data Catalog is a fully managed, Apache Hive 2.x metadata repository for all data assets, regardless of where they are located. The Data Catalog contains table definitions, job definitions, and other control information to help manage a AWS Glue environment.&nbsp;

&nbsp;

To perform data modeling for the AWS Glue Data Catalog with Hackolade, you must first download the Glue [plugin](<https://hackolade.com/help/DownloadadditionalDBtargetplugin.html> "target=\"\_blank\"").  The plugin is based on the Hive plugin, but specifically tuned to interact with AWS Glue using the AWS CLI commands.

&nbsp;

Hackolade was specially adapted to support the data modeling of the the AWS Glue Data Catalog, including Glue metadata and Hive primitive and complex datatypes, and producing both AWS CLI commands and HQL Create Table syntax. The application closely follows the Hive terminology and storage structure.

&nbsp;

The data model in the picture below results from the modeling of an application described in [this AWS Blue tutorial](<https://docs.aws.amazon.com/glue/latest/dg/aws-glue-programming-python-samples-legislators.html> "target=\"\_blank\"").

&nbsp;

![AWS Glue Data Catalog workspace](<lib/Glue workspace.png>)

&nbsp;

&nbsp;

## Tables

Tables in in the Glue Data Catalog contain references to data that is used as sources and targets of&nbsp; extract, transform, and load (ETL) jobs in AWS Glue.&nbsp;

&nbsp;

### Standard tables

The table properties are based on Hive 2.x metadata structure.

&nbsp;

![AWS Glue Data Catalog table properties](<lib/Glue table properties.png>)&nbsp;

![AWS Glue Data Catalog table properties - part 2](<lib/Glue table properties - part 2.png>)

&nbsp;

&nbsp;

### Iceberg tables

AWS [announced S3 Tables](<https://aws.amazon.com/blogs/aws/new-amazon-s3-tables-storage-optimized-for-analytics-workloads/> "target=\"\_blank\""), which brings native support for [Apache Iceberg](<https://iceberg.apache.org/>) to S3.&nbsp; AWS Glue 3.0 and later supports the Apache [Iceberg framework](<https://aws.amazon.com/blogs/big-data/introducing-aws-glue-crawler-and-create-table-support-for-apache-iceberg-format/> "target=\"\_blank\"") for data lakes. Iceberg provides a high-performance table format that works just like a SQL table.&nbsp; This isn’t a separate service that sits on top of S3. Rather AWS has added a new type of bucket to the S3 service itself: a [table bucket](<https://docs.aws.amazon.com/AmazonS3/latest/userguide/s3-tables-buckets.html> "target=\"\_blank\"").&nbsp; Table buckets come with a host of [new APIs](<https://docs.aws.amazon.com/AmazonS3/latest/API/API\_Operations\_Amazon\_S3\_Tables.html>). It’s the stuff you’d expect for working with Iceberg tables. To name a few: [CreateNamespace](<https://docs.aws.amazon.com/AmazonS3/latest/API/API\_s3TableBuckets\_CreateNamespace.html> "target=\"\_blank\""), [CreateTable](<https://docs.aws.amazon.com/AmazonS3/latest/API/API\_s3TableBuckets\_CreateTable.html> "target=\"\_blank\""), [ListTables](<https://docs.aws.amazon.com/AmazonS3/latest/API/API\_s3TableBuckets\_ListTables.html> "target=\"\_blank\""), [RenameTable](<https://docs.aws.amazon.com/AmazonS3/latest/API/API\_s3TableBuckets\_RenameTable.html> "target=\"\_blank\""), [PutTableMaintenanceConfiguration](<https://docs.aws.amazon.com/AmazonS3/latest/API/API\_s3TableBuckets\_PutTableMaintenanceConfiguration.html> "target=\"\_blank\"").

&nbsp;

AWS Glue can be used to perform read and write operations on [Iceberg tables](<https://docs.aws.amazon.com/lake-formation/latest/dg/create-databases-tables-s3-catalog.html> "target=\"\_blank\"") in Amazon S3, or work with Iceberg tables using the AWS Glue Data Catalog.&nbsp; AWS Glue Data Catalog feature[1](<https://meltware.com/2024/12/04/s3-tables.html#fn:1>) that automatically mirrors the catalogs from the S3 table buckets in your account like this diagram provided from [this article](<https://meltware.com/2024/12/04/s3-tables.html> "target=\"\_blank\""), along with additional valuable insights:

&nbsp;

![Glue AWS S3 to Iceberg Glue Data Catalog map](<lib/Glue AWS S3 to Iceberg Glue Data Catalog map.png>)

&nbsp;

Hackolade Studio supports [Iceberg tables](<https://docs.aws.amazon.com/lake-formation/latest/dg/creating-iceberg-tables.html> "target=\"\_blank\"") in AWS Glue Data Catalog, including the ability to maintain the relevant properties, plus forward- and reverse-engineering.

![Glue Iceberg table properties](<lib/Glue Iceberg table properties.png>)

&nbsp;

&nbsp;

## Partition keys, buckets

The Glue Data Catalog organizes tables into partitions for grouping same type of data together based on a column or partition key. Each table can have one or more partition keys to identify a particular partition. Using partition we can also make it faster to do queries on slices of the data.&nbsp; Tables or partitions are subdivided into buckets based on the hash function of a column in the table to give extra structure to the data that may be used for more efficient queries.

&nbsp;

## Data types

The Glue Data Catalog supports different data types to be used in table columns. The data types supported can be broadly classified in Primitive and Complex data types.

&nbsp;

Hackolade was specially adapted to support the data types and attributes behavior of the AWS Glue Data Catalog, including arrays, maps and structs.

&nbsp;

![AWS data types](<lib/Hive data types.png>)

&nbsp;

## Forward-Engineering

Hackolade dynamically generates both the AWS CLI command and the HQL script to create tables, columns and their data types, and indexes for the structure created with the application.&nbsp; The AWS CLI command can be applied directly to the instance, provided that the user profile is granted sufficient rights.

&nbsp;

The script can also be exported to the file system via the menu Tools \> Forward-Engineering, or via the [Command-Line Interface](<CommandLineInterface.md>).

&nbsp;

![AWS Glue Data catalog Forward-Engineering](<lib/Glue Forward-Engineering.png>)

&nbsp;

As many people store JSON within text columns, Hackolade allows for the schema design of those documents.  That JSON structure is not forward-engineered, but is useful for developers, analysts and designers.

## Reverse-Engineering

The connection is established using a connection using AWS IAM credentials:

![AWS Glue Dta Catalog connection settings](<lib/Glue connection settings.png>)

&nbsp;

or through the [credentials file](<https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html> "target=\"\_blank\"") of the AWSCLI.

&nbsp;

The Hackolade process for reverse-engineering of Glue Data Catalog databases includes the execution of [AWS CLI glue](<https://docs.aws.amazon.com/cli/latest/reference/glue/index.html> "target=\"\_blank\"") statements to discover tables, columns and their types.  If JSON is detected in text columns, Hackolade performs statistical sampling of records followed by probabilistic inference of the JSON document schema.

&nbsp;

For more information on the AWS Glue Data Catalog in general, please consult the AWS [website](<https://docs.aws.amazon.com/glue/latest/dg/populate-data-catalog.html> "target=\"\_blank\"").

