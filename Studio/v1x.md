# v1.x

New features with v1.12.20:

\- fixed anomaly in Object Browser menu toggle

\- fixed check of Windows10 Registry if user has no rights

\- using getCollection instead of brackets in forward-engineering of MongoDB index for better encoding of special characters in collection names

\- better handling of internal references in JSON Schema import

\- encryption/decryption for database connections

\- added mapping of date and time string types in XSD reverse-engineering

\- suppressed extraneous warning when Saving As

\- fixed forward-engineering of MongoDB script after PostgreSQL DDL import

&nbsp;

New features with v1.12.19:

\- enhanced instructions in uncaught exception dialog

\- added system info in email report of uncaught exception

\- fixed exception when MongoDB view uses field with an external reference

&nbsp;

New features with v1.12.18:

\- enhanced handling multiple types in JSON schema validator of MongoDB

\- enhanced merging validator of MongoDB and the JSON schema from the probabilistic schema

\- added handling uncaught error on main process

&nbsp;

New features with v1.12.17:

\- allow offline connection to local MongoDB instance on Windows

\- changed license message for expired maintenance&nbsp;

\- improved display of uncaught error details

\- better handling of foreign key relationships on reference definitions

\- fixed behavior of external definitions when references or fields containing references are deleted

\- fixed copying of external references

&nbsp;

New features with v1.12.16:

\- enhanced reverse-engineering of extremely large documents

\- added parsing of DDL table comments

\- fixed parsing of MySQL DDL composite foreign keys

\- added filters for some extraneous DDL fields

&nbsp;

New features with v1.12.15:

\- better handling of update download when expired or no maintenance

&nbsp;

New features with v1.12.14:

\- fixed handling of MongoDB collection options during reverse-engineering

\- fixed handling of DynamoDB indexes during reverse-engineering

&nbsp;

New features with v1.12.13:

\- enhanced MongoDB connections to support MONGODB-CR credentials for older versions (deprecated with v3.6)

\- fined-tuned parsing of MongoDB Atlas URI to suppress test database

\- added conversion of internal definition to attributes when pasting into a model definition

\- added Tools\> Options \> Documentation parameter to limit number of attribute hierarchical schema views with large models for documentation generation performance

\- prevented JSON Schema "id" attribute from being boolean

&nbsp;

New features with v1.12.12:

\- set default to 'Maintain field order' when reverse-engineering

\- fixed license check for AWS Marketplace Workspaces

\- fixed Bluebird module issue for Elasticsearch mappings preview

\- fixed rare issue with UUID generation not accessible

&nbsp;

New features with v1.12.11:

\- GDPR privacy policy consent

\- plugin for MarkLogic for data modeling only: No forward- or reverse-engineering yet

\- preserve field order during reverse-engineering of JSON file

&nbsp;

New features with v1.12.10:

\- optimized performance of Object Browser search

\- encoded collection names in MongoDB index script when using restricted characters&nbsp;

\- better handling of attribute type in documentation when set to multiple scalar types

\- fixed documentation handling of MongoDB indexes depending on collation flag

\- not displaying unselected sections in documentation

\- better tolerance in reverse-engineering of JSON Schema for ordering of fields and missing properties of choices

\- handling of v2 upgrade licensing

&nbsp;

New features with v1.12.9:

\- Elasticsearch: added properties number of shards, number of replicas, alias, and dynamic in Properties Pane, forward- and reverse-engineering

\- moved installation of node modules in plugin reverse-engineering to plugin installation

\- new user parameter to reduce documentation length by filtering attribute hierarchical schema view

\- added collapsible table of content pane in HTML documentation

\- fixed link generation in HTML documentation for some large models

\- 50% performance improvement in documentation generation

\- added toggle in JSON Schema preview for standard vs extended (internal) JSON Schema

\- added storageEngine property to collection creation script in MongoDB

\- fixed creation of new connection settings in DynamoDB

\- change default of pattern fields to "\^\[a-zA-Z0-9\_.-\]+$" throughout (plugins require installation of update)

\- fixed complex data type for some targets when referencing external definition

&nbsp;

New features with v1.12.8:

\- parsing of auth source from MongoDB Atlas and mlab URI

\- fixes case of empty Object Browser at startup after first install

\- persistence of unique array items in MongoDB

&nbsp;

New features with v1.12.7:

\- forward- and reverse-engineering for Elasticsearch and HBase

\- reverse-engineering of JSON file takes multiple documents into account

\- added date and time as JSON Schema string formats -- not in draft v4 but tolerated by validators then introduced in v6

\- fixed forward-engineering of JSON document when same name for model, group, and document

\- filter some extraneous properties in forward-engineering if false

\- performance improvements in Object Browser for large models by use of virtual lists

\- support of AWS Workspaces for Desktop Applications

&nbsp;

New features with v1.12.6:

\- ERD display of field subtype when present instead of field type

\- fine-tuning reverse-engineering of XSDs in case of substitutionGroup&nbsp;

\- fixed handling of embedded array items in CLI model comparison

&nbsp;

New features with v1.12.5:

\- skipped

&nbsp;

New features with v1.12.4:

\- reverse-engineering of XSD to import models from erwin, ER/Studio, PowerDesigner, and others

\- improved documentation generation performance

\- possibility to print diagram to PNG

\- display of nested fields in MongoDB views pipeline

\- enhanced handling of model opening when corresponding plugin is absent

\- ability to handle multiple oneOfs in reverse-engineering of JSON Schema&nbsp;

\- fixed handling of multiple types with Null and sub-docs

\- ability to handle probabilistic schema for large sets of documents&nbsp;

&nbsp;

New features with v1.12.3:

\- user-defined parameter for Couchbase reverse-engineering pagination

\- display field subtypes in ERD

\- display progress details during Couchbase reverse-engineering

&nbsp;

New features with v1.12.2:

\- allow A0, A1, A2, Ledger formats in Print Diagram&nbsp;

\- more accurate entity box resizing in ERD after reverse-engineering

\- allow reverse-engineering of MongoDB NULL type fields

\- allow opening of model file corrupted with a prior version

\- workaround for Couchbase error: "An unknown N1QL error occured. This is usually related to an out-of-memory condition"

&nbsp;

New features with v1.12.1:

\- reverse-engineering of PostgreSQL DDLs

\- improved reverse-engineering of Oracle DDLs for processing of alternate syntax

\- increased logging for reverse-engineering process

&nbsp;

New features with v1.12.0:

\- plugins for Google RealTime Firebase and Google Cloud Firestore for data modeling only: NO forward- or reverse-engineering yet

\- enhanced support for MongoDB v3.6, including generation of $jsonschema validator, plus reverse-engineering of $jsonschema validator when present

\- added MongoDB Replica set and Sharded cluster connection type, including choice of Read Preference

\- added MongoDB X.509 authentication protocol

\- fixed conversion of probabilistic schema inference when multiple simple types

&nbsp;

New features with v1.11.1:

\- fixed mishandling in CLI compMod when combination of --ignoreGUIDs and array items with no name

\- fixed when creating a MongoDB index key on a field that is part of the reference to a definition

\- fixed when deleting a field that is also a MongoDB index key

&nbsp;

New features with v1.11.0:

\- complete tech refresh of dependent libraries

\- performance improvements in UI navigation

\- possibility to view and maintain attributes' properties pane from within ERD

\- map DynamoDB field types to JSON Schema compatible types during JSON Schema forward-engineering

&nbsp;

New features with v1.10.4:

\- removed filter of default Couchbase bucket&nbsp;

\- fine-tuning Cassandra plugin

\- fixed encoding of regex expression in MongoDB validator script

&nbsp;

New features with v1.10.3:

\- updated Couchbase reverse-engineering connection

&nbsp;

New features with v1.10.2:

\- fixed message when releasing floating license

\- fixed issue with registration on new instances

&nbsp;

New features with v1.10.1:

\- offline license validation in case of no internet connection

\- reverse-engineering of DB2 DDLs

\- batch forward-engineering of JSON documents and JSON Schema with selection dialog

\- fixed bug of disappearing Object browser pane

\- fixed JSON Schema validation of MongoDB data types in Cosmos DB

\- minor adjustments in Elastisearch and Cassandra plugins

&nbsp;

New features with v1.10.0:

\- support for Microsoft Azure Cosmos DB with MongoDB API

\- latest version of the Cosmos DB DocumentDB SDK version

\- next command in Command Line Interface: model comparison with option merge

\- enhanced toolbar to combine alignment icons and add reverse-engineering icon

\- plugins for Elasticsearch and Apache HBase for data modeling only: no forward- or reverse-engineering yet\!\!

&nbsp;

New features with v1.9.3:

\- enhanced DDL reverse-engineering to deal with optional syntax

\- fixed pasting objects into arrays and sets

&nbsp;

New features with v1.9.2:

\- fixed Object Browser issue with object type in JSON target

\- removed unnecessary properties in JSON integer data type

\- added Comments property column to documentation

\- close application when downloading update

&nbsp;

New features with v1.9.1:

\- proper handling of MongoDB indexing for deeply nested fields

\- handling of Cosmos DB reverse-engineering when multiple databases in same Azure Account ID

\- Command-Line Interface enabled for Cosmos DB

&nbsp;

New features with v1.9.0:

\- support for Microsoft Azure Cosmos DB with DocumentDB API

\- handling for MongoDB indexing of nested fields

&nbsp;

New features with v1.8.6:

\- fixed installer issue with some anti-virus programs

\- fixed duplicate browser objects in some DynamoDB models

\- fixed font size in documentation ERD for some wide models

&nbsp;

New features with v1.8.5:

\- allow polymorphism in reverse-engineering in case of arrays embedded in arrays

\- allow more than 100 tables in DynamoDB reverse-engineering

\- allow documentation generation when Model ER diagram option is OFF

\- allow up to 100k document in sampling via Command-Line Interface reverse-engineering

\- better handling in MongoDB collation strength&nbsp;

\- allow spaces in directory names for default file path

\- removed duplicate tables in DynamoDB Object Browser

&nbsp;

New features with v1.8.4:

\- reading of persistent schema

\- tooltip for drag-and-drop relationship creation for definitions

\- more improvements for handling of reference definitions

&nbsp;

New features with v1.8.3:

\- improved handling of reference definitions

\- improved handling of 2-way referencing in denormalization

\- more accurate numeric type handling in DDL reverse-enginerring in case of JSON target

\- proper rendering of changed custom attributes for JSON and native DB targets

&nbsp;

New features with v1.8.2:

\- documentation generation for attributes referencing definitions

\- CR/LF in forward-engineering of JSON document and JSON Schema on Windows platform

\- defect fix in node-ipc module log

&nbsp;

New features with v1.8.1:

\- enabled reverse-engineering of DDLs for plain JSON target

\- moved reverse-engineering from front-end to back-end to allow larger sampling size

\- relaxed sampling size for Command-Line Interface reverse-engineering to 100k documents

\- several new filtering options to configure/trim down documentation

&nbsp;

New features with v1.8.0:

\- Command Line Interface with: generation of documentation, and reverse-engineering. (comparison of models due in subsequent release)

\- user-defined custom properties for MongoDB, DynamoDB, and Couchbase objects via plugin

\- improved document kind field proposals for Couchbase without N1QL service

&nbsp;

New features with v1.7.2:

\- improved handling of bucket authentication via REST API for Couchbase 4.x

\- reverse-engineering of Mongoose schemas in plain JSON, plus handling of keywords "required" and "default"

\- improved handling of "required" property in forward-engineering of MongoDB scripts

&nbsp;

New features with v1.7.1:

\- fixed several minor anomalies

&nbsp;

New features with v1.7.0:

\- introduction of affordable Personal edition

\- copy/paste between multiple instances of Hackolade

\- ability to perform joins with $lookup in MongoDB read-only views

&nbsp;

New features with v1.6.2:

\- Fall back to all documents when Couchbase localRandomKey fails

\- Fixed licensing release when multiple consecutive trial keys

&nbsp;

New features with v1.6.1:

\- URI encoding of Couchbase non-N1QL REST call for Reverse-Engineering

\- new layout Software Registration

&nbsp;

New features with v1.6.0:

\- plugin extensions for additional database targets (no reverse-engineering yet - coming soon)

\- references to other Hackolade models via external definitions

\- reverse-engineering of Couchbase 3.x and other instances not running N1QL service

\- support for Couchbase 5.x security

\- significant performance improvements in ERD&nbsp;

&nbsp;

New features with v1.5.3:

\- Improved handling of collapsed nodes in hierarchical schema and Couchbase ramQuota

\- Display of password-protected Couchbase buckets in document selection dialog of Reverse-Engineering

&nbsp;

New features with v1.5.2:

\- Reverse-Engineering from MongoDB secondary (does not include validator rules as they are not replicated by MongoDB to secondaries)

&nbsp;

New features with v1.5.1:

\- fine-tuned Couchbase authentication

\- enhanced processing of MongoDB DBRefs when combined with other field types

&nbsp;

New features with v1.5.0:

\- MongoDB v3.4: read-only views (single collection only -- reference to multiple collections is coming soon), collation, improved indexing, sharding

\- connection to MongoDB Atlas

\- move fields via drag-and-drop in hierarchical schema view (only at same level with this release -- more flexibility to come later)

&nbsp;

New features with v1.4.2:

\- fixed installer issue with some anti-virus programs

&nbsp;

New features with v1.4.1:

\- drag-and-drop attributes in collection hierarchical schema view

\- undo/redo with Ctrl+Z/Ctrl+Y

&nbsp;

New features with v1.4.0:

\- support for Couchbase Server and Mobile, including specific terminology, forward-engineering scripts (Ottoman ODM) and reverse-engineering protocol for both local and hosted instances

\- MongoDB: possibility to maintain multiple databases in same model, and define different groups of collections

\- DynamoDB: possibility to maintain multiple regions in same model, and define different groups of tables

\- JSON: possibility to maintain multiple groups in same model&nbsp;

&nbsp;

New features with v1.3.2:

\- auto-detect type when opening a JSON file: JSON document, JSON Schema, or Hackolade model.&nbsp; The first 2 trigger reverse-engineering.

\- display error details when opening an invalid Hackolade model file

\- application overview presentation at startup

\- OS-specific shortcut keys

&nbsp;

New features with v1.3.1:

\- fix for licensing server change

&nbsp;

New features with v1.3.0:

\- library of re-usable definitions

\- reverse-engineering of MS SQL Server DDL

\- documentation logo personalization

&nbsp;

New features with v1.2.5:

\- additional controls for database/collection selection in Reverse-Engineering and documentation

\- refinements when using MongoDB validator in Reverse-Engineering

\- better use of field attributes and constraints in auto-generation of JSON samples

&nbsp;

New features with v1.2.4:

\- support for concurrent licensing

&nbsp;

New features with v1.2.3:

\- in contextual menu, ability to pick from list of previously created fields

\- fix for suggest denormalization

&nbsp;

New features with v1.2.2:

\- ability to import model and fields info from an Excel template

\- ability to create relationships with drag-and-drop

\- button to add timestamp to comments

\- leverage validator info in db.getCollectionInfos() during reverse-engineering (MongoDB v3.2+)

\- DynamoDB: support for composite fields in GSI primary key

&nbsp;

New features with v1.2.1:

\- support for MongoDB DRBrefs at model creation, and during reverse-engineering

\- detection of version of MongoDB during reverse-engineering

\- possibility to edit field name and type in field box of hierarchical schema view

\- possibility to (de)select objects in documentation generation

&nbsp;

New features with v1.2.0:

\- support for Amazon DynamoDB, including specific terminology, forward-engineering scripts and reverse-engineering protocol for both local and hosted instances

\- possibility to select objects to be included in documentation

&nbsp;

New features with v1.1.3:

\- more precise logging for reverse-engineering and license registration processes

\- improved reverse-engineering of multi-type fields when combining scalar and complex types

&nbsp;

New features with v1.1.2:

\- SSH connection to MongoDB instances (for example at cloud locations)

\- definition of composite indexes and forward-engineering of indexes

\- 2-way referencing in denormalization assistance

\- ERD collection box color-coding

\- extended host connection string format to directly access specific db

&nbsp;

New features with v1.1.1:

\- re-architecture to allow multiple 'targets', and support DB vendors other than just MongoDB

\- support for plain JSON, with pure JSON Schema draft v4 validation

\- collection hierarchical schema diagrams in HTML documentation can now be zoomed in when opened in separate browser tab

&nbsp;

New features with v1.0.12:

\- Fixed licensing issues for first-time users

&nbsp;

New features with v1.0.11:

\- Reverse-Engineering of MySQL Data Definition Language files

\- orthogonal distribution of ERD shapes

\- contextual menu in Object Browser

&nbsp;

New features with v1.0.10:

\- fine-tuning of DDL reverse-engineering and denormalization

&nbsp;

New features with v1.0.9:

\- Reverse-Engineering of Data Definition Language (DDL file from Oracle RDBMS)

\- Suggestion of denormalization

&nbsp;

New features with v1.0.8:

\- logging of Reverse-Engineering process steps

\- increased usability of relationship deletions and opening of collections

&nbsp;

New features with v1.0.7:

\- Kerberos connection to MongoDB

\- Tools \> Compare Models

\- HTML documentation

\- fixed PDF header and footer issues

\- many reports improvements

\- progress dialog in Reverse-Engineering of MongoDB

&nbsp;

New features with v1.0.6:

\- field order in reverse-engineering \> JSON Document, JSON Schema, and Mongoose schema

\- fixed several minor cosmetic issues

&nbsp;

New features with v1.0.5:

\- LDAP authentication

\- Tools \> Options for user parameters

\- field order in reverse-engineering \> MongoDB Collections

\- capped collection parameters for db.createCollection script

&nbsp;

New features with v1.0.4:

\- licensing: replaced MAC address with UUID for more stable desktop identification

\- added X.509 TLS/SSL connection to MongoDB, with options:

\-- none: do not use SSL for anything

\-- unvalidated: use SSL but do not perform any validation of the certificate chain

\-- server: the driver should validate the server certificate and fail to connect if validation fails

\-- all: the driver must present a valid certificate and validate the server certificate.

&nbsp;

New features with v1.0.3:

\- authentication to local and remote instances of MongoDB (without SSL, LDAP, Kerberos, X.509, or SSH)

\- fixed relationships in copy/paste of fields

\- added validationLevel and validationAction to MongoDB validator script

&nbsp;

New features with v1.0.2:

\- forward-engineering \> Mongoose schema

\- fixed documentation generation on Mac

\- finished documentation formatting

\- diagram print preview

\- letter and tabloid formats in diagram printing

\- lots of other improvements

