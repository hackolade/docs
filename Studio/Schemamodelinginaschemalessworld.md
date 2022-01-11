# Schema design in a schemaless world

The JSON-based dynamic-schema nature (aka schema-less nature) of document NoSQL databases (MongoDB, DynamoDB, Couchbase, etc...) is a fantastic opportunity for application developers: ability to start storing and accessing data with minimal effort and setup, flexibility, fast and easy evolution.

&nbsp;

Some difficulties start appearing with increased complexity of the data and scale.&nbsp; Typically, the **data structure is tacitly described -- in the application code…**&nbsp; And examining the code is not the most productive way to engage in a fruitful dialog between analysts, architects, designers, developers, and DBAs.

&nbsp;

A data model describes the business.&nbsp; **A data model is the blueprint** of the application.&nbsp; Such a map helps evaluate design options beforehand, **think through the implications** of different alternatives, and recognize potential hurdles before committing sizable amounts of development effort.&nbsp; A data model helps plan ahead, in order to minimize later rework.&nbsp; In the end, **the modeling process accelerates development, increases quality of the application, and reduces execution risks.** &nbsp;

&nbsp;

With the convergence of traditional RDBMS (introducing support for JSON documents) and NoSQL (i.e. DBRefs and $lookup for left-outer joins appeared in MongoDB with v3.2), mainstream CIOs may need some convincing that MongoDB can be accepted by enterprise architects and large teams of analysts and designers, as well as operations.&nbsp; A MongoDB schema modeling tool contributes to such acceptance, in addition to being a **best practice**.

&nbsp;

But the traditional methods and tools of the old ‘relational’ world are no longer valid for NoSQL.&nbsp;

&nbsp;

&nbsp;

Hackolade was developed to be a **cross-platform** (Windows/Mac/Linux) NodeJS-based desktop Single Page Application (JavaScript/HTML 5/CSS) to help the design and documentation of physical models, leveraging the power of JSON and MongoDB.&nbsp; It is targeted at analysts, solution designers, architects, developers, and database administrators. &nbsp;

&nbsp;

The graphical interface lets the user **visualize and maintain a diagram of the collections** and their logical relationships, plus the **details and constraints of individual attributes and objects within each collection**.&nbsp; The application is **specifically designed around the powerful nature of nested sub-objects and denormalization**.&nbsp; The outputs of the model are:

* a detailed documentation of the model in HTML and PDF formats;
* scripts
  * MongoDB: validator script and Mongoose schema
  * DynamoDB: Create Table and Condition Expression scripts
  * Couchbase: Ottoman schema;&nbsp;
  * Cassandra: CQL scripts for CREATE or ALTER TABLE;
  * Hive: HQL scripts;
  * Neo4j: Cypher script by example;
  * Avro: Avro schema;
  * Parquet: Parquet schema;
  * DW and RDBMS: DDL scripts;
  * etc...
* sample JSON documents and JSON Schema compliant JSON models.&nbsp;

&nbsp;

A powerful reverse-engineering feature lets the user create the basis for a model, from an existing database, then lets edit and enrich the physical model.

&nbsp;

Particular emphasis has been given to making the application **intuitive and simple to use, yet powerful and rigorous**.

&nbsp;

The business benefits are as follows:

* increase **projects legitimacy and credibility** with mainstream CIOs, by showing that MongoDB applications can also be planned, designed, and fully thought-through, thereby reducing risks.
* leverage the **power of visual modeling**: data structures and relationships don't have to be buried in application code.&nbsp; They can also be available to the various teams for a 360° view of the system landscape, for better collaboration and smooth operations.
* facilitate data governance by **generating scripts** to easily configure MongoDB 3.2’s validator&nbsp;

