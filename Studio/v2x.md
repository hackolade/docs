# v2.x

New features with v2.5.8:

\- MongoDB: added support for LDAP roles

\- MongoDB: added handling of replica read preference

\- Elasticsearch: added handling of default index options

\- Cassandra: fixed generation of CQL script for only selected tables

\- Neo4j: fixed actions menu for graph view tab

&nbsp;

New features with v2.5.7:

\- Allow upgrade to v3

&nbsp;

New features with v2.5.6:

\- Added set zoom toolbar choice for ERD and hierarchical schema view

\- Improved zoom speed for ERD and hierarchical schema view

\- Added focus on ERD object when selected in Object Browser

\- Added user-friendly message when corrupted plugin zip

\- Added error-handling for loading of plugin configurations

&nbsp;

New features with v2.5.5:

\- Added ability to collapse container list

\- Elasticsearch: fixed denormalization when relationships stored inside container-level keys

\- Postgres DDL: detect UUID data type

&nbsp;

New features with v2.5.4:

\- Avro: added description and comments properties at choice level

\- Avro: added support for doc and default properties for choices

\- Avro: forward-engineering of complex types (enum, fixed) inside node when multiple data type

\- Avro: handling of undefined field after changing field alias

\- Avro: proper handling of naming convention technical name in forward-engineering

\- Command Line Interface: handled recursive creation of non-existent folders in forward-engineering

\- DynamoDB; fixed reverse-engineering uncaught error

\- Fixed Daylight Savings bug

\- Handled reverse-engineering of JSON Schema inside JSON document

\- Fixed JSON Schema validation error after reverse-engineering&nbsp;

&nbsp;

New features with v2.5.3:

\- Added error handling in CLI obfuscate command

\- Added forward- and reverse-engineering of Cassandra set, list, and map with UDT

&nbsp;

New features with v2.5.2:

\- CLI: added command to obfuscate technical and business names, and remove value of description, comments, and enums

\- CLI: added command to forward-engineer schema creation/alter scripts

\- Avro: reverse-engineering of doc and default properties in case of polymorphism

\- Avro: maintain field order when multiple oneOfs within an allOf choice

\- Cassandra: possibility to add a UDT as child of list, map or list data type

\- Fixed generation of JSON sample if an object accidentally contains an array item

&nbsp;

New features with v2.5.1:

\- Handled forbidden characters in filenames of container forward-engineering

\- Added "OR REPLACE" to forward-engineering of Cassandra UDA alter script

\- Fixed disappearing characters in business name property

\- Avro: added type name property to complex types, and added handling for it in reverse- and forward-engineering

&nbsp;

New features with v2.5.0:

\- Detection of pattern fields during reverse-engineering

\- Enabled pasting of model definitions

\- Avro: added technical name to the array items with complex types

\- Avro: allowed multiple union types at same level through JSON Schema allOf choice

\- Avro: allowed names for union types

\- Avro: fixed naming convention of records

\- Avro: fixed technical name of containers when business-to-technical naming conventions enabled

\- Avro: handling of union data type with logical types

\- Avro: handling of enum data type

\- Avro: resolution of referenced definitions in forward-engineering

\- Cassandra: added button to apply CQL script to db instance (provided user has proper rights)

\- Cassandra: added ALTER TABLE CQL script to Command-Line Interface model comparison

\- Changed saving path of an external reference model using RFC 3986 specification ([https://tools.ietf.org/html/rfc3986](<https://tools.ietf.org/html/rfc3986>))

\- Adjusted warning to take relative path of external references into account

\- Enhanced handling of reverse-engineering of gigantic schema with extremely deep nesting

\- Fixed resolving external references when opening model

\- Reverse-engineering of MySQL DDL: take time data type into account

\- Changed spinner to appear sooner during plugin installation

\- Preserve original ERD layout after reverse-engineering if model was previously not empty

\- Elasticsearch: set default container keys plus reverse-engineer JSON and JSON Schema under \_source

\- Added license re-validation attempt after maintenance expiration

\- Hive: suppressed forward slash in http transport mode path

&nbsp;

New features with v2.4.4:

\- Changed from backslash to forward slash in forward-engineering of path for external definition on Windows

\- Relaxed constraint of error message when opening a model which was created with a newer application version

\- Fixed creation of JSON Schema from a collection with extended MongoDB data types ( ISODate(), Timestamp(), ...)

\- Fixed reverse engineering of a sample for date data type

&nbsp;

New features with v2.4.3:

\- Proper handling of $ sign in Naming Convention's case conversion

\- Added&nbsp; period in front of the relative path of external definition

\- Added link to sample models page in to Welcome pane

\- Added support for nesting beyond 100 levels during Reverse-Engineering

\- Filtered GUIDs in standard view of JSON Schema preview and forward-engineering

\- Added reverse-engineering of MongoDB indexes on array items

\- Improved handling of multiple data types in Properties Pane

\- Fixed error message during CLI reverse-engineering if erroneous model path

&nbsp;

New features with v2.4.2:

\- Added validation and auto-fixing of ERD settings when opening model&nbsp;

\- Added target and plugin information to the uncaught error report

\- Fixed distribution of graph relationships

\- Fixed handling technical names for graph node labels

&nbsp;

New features with v2.4.1:

\- Added warning after Reverse-Engineering when Naming Conventions coupling set to Business-to-Technical, to avoid conflict in case of non-symmetric conversions

\- Added button to clear Technical Names if user inadvertently enabled Business-to-Technical coupling, and now wants it disabled.

\- Display real data type of attribute when appearing in a view

\- Added handling of Naming Conventions for views

\- Adjusted handling of indexes in DynamoDB Table Create Script after copy table

&nbsp;

New features with v2.4.0:

\- Introduction of Naming Conventions to maintain both a ‘business name’ and a ‘technical name’ for objects, and keep them synchronized and transformed based on a set of user-driven parameters, and optionally based on a conversion file maintained outside of the application.&nbsp; Name conversion can go both directions: Business-to-Technical, or Technical-to-Business. &nbsp;

\- Added handling access error when saving to root on Mac

\- Added default paths parameter options for new installations

\- Added tolerance for absent container complex type in XSD reverse-engineering

&nbsp;

New features with v2.3.7:

\- Mapped DateTime data type in MS SQL Server DDL reverse-engineering to Hive timestamp

\- Mapped BIT data type in MySQL DDL reverse-engineering to JSON boolean

\- Eliminated false positive document validation in JSON Preview for recursive external references

\- Clear search box of Object Browser when opening a new model

\- Restored full list of entities in JSON Schema forward-engineering

\- Fixed error in cancellation of MongoDB reverse-engineering

\- Fixed error in Command Line Interface documentation generation

\- Fixed in keeping order of attributes during Cassandra reverse-engineering

\- Fixed error in cancellation of Cassandra reverse-engineering

\- Fixed rendering of keys at the entity level

&nbsp;

New features with v2.3.6:

\- Support for proxy server in plugin installation

\- Support for proxy server in Command-Line Interface reverse-engineering

&nbsp;

New features with v2.3.5:

\- UUID change for concurrent licenses

\- Fixed section numbering in documentation when partial entity selection

\- Tolerance for empty complexType in XSD import

\- Hive: fixed forward-engineering when dependencies are present

\- various minor fixes

&nbsp;

New features with v2.3.4:

\- Avro: support for logical types

\- Couchbase: prompt user to choose document type if confusion by INFER or empty string

\- MongoDB: updated mongodb-core library

\- MongoDB: added timeout handling

\- MongoDB: moved enableSharding from model to database level and added to script if enabled

\- JSON: removed isRestfulApi in forward-engineering if disabled

\- fixed generating JSON sample for complex type in case of recursive definitions

\- fixed spinner if install plugin from zip is canceled

\- XSD reverse-engineering: added support for xsd: tags to xs:

\- Hive: keep order of JSON when inferring schema in reverse-engineering

&nbsp;

New features with v2.3.3:

\- Added option for manual network proxy parameters, for license key validation and software update check

\- Fixed so subscription licenses don't require re-validation when renewal has been paid

&nbsp;

New features with v2.3.2:

\- Kerberos authentication protocol support for HBase plugin

\- Better handling of deletion of a field that is a key in a MongoDB index

\- Warning dialog when an attribute is deleted

\- Fixed definition resolution when array contains null

\- DDL reverse-engineering: convert varchar to varchar instead of string if the target supports it

\- DDL reverse-engineering: convert decimal to double instead of integer if the target supports it

\- Oracle DDL reverse-engineering: be tolerant of non-official BIGINT, SMALLINT, TINYINT, and STRING and convert to equivalent if the target supports it

\- Hive HQL script forward-engineering: fix error when source is erwin model

\- XSD reverse-engineering: convert DateTime data type to timestamp instead of string if the target supports it

&nbsp;

New features with v2.3.1:

\- Disabled option in contextual menu of a model definition that allowed conversion of attributes into an internal reference

\- Allowed expanding a model definition with a reference to an external model

\- Fixed bug in some plugins when changing container for an entity

&nbsp;

New features with v2.3.0:

\- Support for Avro schema

\- Support for Apache Hive

\- Warning about Couchbase Community with missing schema service

\- Handling of missing Elasticsearch index type

\- Display warning if attempting to reverse-engineer CosmosDB w/ MongoDB API without corresponding plugin

&nbsp;

New features with v2.2.4:

\- Ability to use field list properties in plugin field-level config

\- Additional Elasticsearch mapping parameters for v6.4

\- Handling of PDF Print and Documentation Generation with Acrobat Reader version 2019

&nbsp;

New features with v2.2.3:

\- Normalization of file path in external definition with relative path

\- Default JSON Schema preview to referenced definitions

\- Fine-tuned JSON Schema definitions conversions with cascading references

\- Fixed HTML documentation opening of diagram in new tab for Chrome 69, plus link to container/database/bucket

\- Fixed CLI compMod merge container visual

\- Fixed reverse-engineering of XSD schema for Cassandra and Hive plugins

&nbsp;

New features with v2.2.2:

\- Added identifier in License Key Validation dialog for customers with multi-seat keys&nbsp;

\- Added automatic release of previous key when validating a new one

\- Added indentation for documentation titles

\- Elasticsearch: renamed container-level key from index to \_index and defaulted index property to true

\- XSD reverse-Engineering: added handling of types anyURI, boolean, double and float.&nbsp; And when possible: base64Binary and hexBinary

\- Added search capability in both field picker and external definition picker

\- Added possibility to load external models by relative path

\- Added prevention of combining scalar and complex types in multiple data types -- if involves complex types, must use Choice

\- Added generation of default data in case of references in an array

\- Added optional resolution of definitions in JSON Schema preview and reverse-engineering

\- Fixed handling of relationships when copy/paste between instances

\- Fine-tuned merge of models after CLI compMod when renaming a container, an entity, or an attribute

&nbsp;

New features with v2.2.1:

\- Graph zoom fine-tuning

\- Change of relationship line size

&nbsp;

New features with v2.2.0:

\- Graph view with familiar circular node labels in Neo4j plugin

\- Adjusted MongoDB reverse-engineering when specified database and SSH

\- Fixed reverse-engineering of Excel template for MongoDB target

\- Fixed installation on Windows when conflict between environment variables

&nbsp;

New features with v2.1.1:

\- removed caching of modal content

\- saving models of native targets

\- handling JSON in plugin reverse-engineering

\- fixed reverse-engineering for Cosmos DB if container-level key is named 'id'

&nbsp;

New features with v2.1.0:

\- forward- and reverse-engineering of Cassandra \& Datastax (requires plugin update), including inference of JSON structures if detected in text or blob

\- using getCollection instead of brackets in forward-engineering of MongoDB index for better encoding of special characters in collection names

\- suppressed extraneous warning when Saving As

\- fixed forward-engineering of MongoDB script after PostgreSQL DDL import

&nbsp;

New features with v2.0.8:

\- encoding of special characters in index names when forward-engineering of MongoDB script

\- fixed anomaly in Object Browser menu toggle

\- fixed check of Windows10 Registry if user has no rights

\- better handling of internal references in JSON Schema import

\- encryption/decryption of database connections

\- added mapping of date and time string types in XSD reverse-engineering

\- documentation list of types when multiple

&nbsp;

New features with v2.0.7:

\- enhanced instructions in uncaught exception dialog

\- added system info in email report of uncaught exception

\- fixed exception when MongoDB view uses field with an external reference

\- added filtering of property names in documentation when section is empty

\- added filtering of field properties (including hierarchies) when user option is 'none'

&nbsp;

New features with v2.0.6:

\- enhanced handling multiple types in JSON schema validator of MongoDB

\- enhanced merging validator of MongoDB and the JSON schema from the probabilistic schema

\- added handling uncaught error on main process

\- updated mongodb driver

&nbsp;

New features with v2.0.5:

\- fixed behavior of external definitions when references or fields containing references are deleted

\- fixed copying of external references

&nbsp;

New features with v2.0.4:

\- relaxed syntax restriction for regex pattern in string property and allow \^urn:uuid:

\- better handling of foreign key relationships on reference definitions

\- support for MongoDB 4.0 and SCRAM-SHA-256

\- improved display of uncaught error details

&nbsp;

New features with v2.0.3:

\- allow offline connection to local MongoDB instance on Windows

\- changed license message for expired maintenance&nbsp;

\- fixed v2 license validation when no maintenance plan

&nbsp;

New features with v2.0.2:

\- enhanced reverse-engineering of extremely large documents

\- added parsing of DDL table comments

\- fixed parsing of MySQL DDL composite foreign keys

\- added filters for some extraneous DDL fields

&nbsp;

New features with v2.0.1:

\- software key validation screen: added maintenance status and expiration

\- fixed regression when creating a foreign key from properties pane

\- added logging of schema validation during model opening

\- improved plugin installation when previous plugin already installed

&nbsp;

New features with v2.0.0:

\- support for Neo4j graph database

