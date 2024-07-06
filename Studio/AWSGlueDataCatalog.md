# Glue Data Catalog

AWS Glue is a fully managed extract, transform, and load (ETL).&nbsp; AWS Glue discovers data and stores the associated metadata (e.g. table definition and schema) in the AWS Glue Data Catalog.&nbsp; Once cataloged,&nbsp; data is immediately searchable, queryable, and available for ETL.&nbsp; The AWS Glue Data Catalog is a fully managed, Apache Hive 2.x metadata repository for all data assets, regardless of where they are located. The Data Catalog contains table definitions, job definitions, and other control information to help manage a AWS Glue environment.&nbsp;

&nbsp;

To perform data modeling for the AWS Glue Data Catalog with Hackolade, you must first download the Glue [plugin](<https://hackolade.com/help/DownloadadditionalDBtargetplugin.html> "target=\"\_blank\"").  The plugin is based on the Hive plugin, but specifically tuned to interact with AWS Glue using the AWS CLI commands.

&nbsp;

Hackolade was specially adapted to support the data modeling of the the AWS Glue Data Catalog, including Glue metadata and Hive primitive and complex datatypes, and producing both AWS CLI commands and HQL Create Table syntax. The application closely follows the Hive terminology and storage structure.

&nbsp;

The data model in the picture below results from the modeling of an application described in [this AWS Blue tutorial](<https://docs.aws.amazon.com/glue/latest/dg/aws-glue-programming-python-samples-legislators.html> "target=\"\_blank\"").

&nbsp;

![AWS Glue Data Catalog workspace](<lib/Glue%20workspace.png>)

&nbsp;

&nbsp;

## Tables

Tables in in the Glue Data Catalog contain references to data that is used as sources and targets of&nbsp; extract, transform, and load (ETL) jobs in AWS Glue. The table properties are based on Hive 2.x metadata structure.

&nbsp;

![AWS Glue Data Catalog table properties](<lib/Glue%20table%20properties.png>)&nbsp;

![AWS Glue Data Catalog table properties - part 2](<lib/Glue%20table%20properties%20-%20part%202.png>)

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

![AWS Glue Data Catalog data types](<lib/Hive%20data%20types.png>)

&nbsp;

## Forward-Engineering

Hackolade dynamically generates both the AWS CLI command and the HQL script to create tables, columns and their data types, and indexes for the structure created with the application.&nbsp; The AWS CLI command can be applied directly to the instance, provided that the user profile is granted sufficient rights.

&nbsp;

The script can also be exported to the file system via the menu Tools \> Forward-Engineering, or via the [Command-Line Interface](<CommandLineInterface.md>).

&nbsp;

![AWS Glue Data catalog Forward-Engineering](<lib/Glue%20Forward-Engineering.png>)

&nbsp;

As many people store JSON within text columns, Hackolade allows for the schema design of those documents.  That JSON structure is not forward-engineered, but is useful for developers, analysts and designers.

## Reverse-Engineering

The connection is established using a connection using AWS IAM credentials:

![AWS Glue Dta Catalog connection settings](<lib/Glue%20connection%20settings.png>)

&nbsp;

or through the [credentials file](<https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html> "target=\"\_blank\"") of the AWSCLI.

&nbsp;

The Hackolade process for reverse-engineering of Glue Data Catalog databases includes the execution of [AWS CLI glue](<https://docs.aws.amazon.com/cli/latest/reference/glue/index.html> "target=\"\_blank\"") statements to discover tables, columns and their types.  If JSON is detected in text columns, Hackolade performs statistical sampling of records followed by probabilistic inference of the JSON document schema.

&nbsp;

For more information on the AWS Glue Data Catalog in general, please consult the AWS [website](<https://docs.aws.amazon.com/glue/latest/dg/populate-data-catalog.html> "target=\"\_blank\"").

