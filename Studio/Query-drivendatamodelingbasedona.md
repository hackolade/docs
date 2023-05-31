# Query-driven data modeling based on access patterns

Data modeling for relational databases is performed according to the rules of normalization, so larger tables are divided into smaller ones linked together with relationships.&nbsp; The purpose is to eliminate redundant or duplicate data. &nbsp;

&nbsp;

![JSON order normalized structure](<lib/JSON%20order%20normalized%20structure.png>)

&nbsp;

But NoSQL databases are completely different.&nbsp; They require a mindshift in schema design in order to leverage their capabilities, as well as a data modeling tool built specially for this new breed of state-of-the art technology.

&nbsp;

## Query-driven schema design

To leverage the performance of NoSQL databases and the flexibility of JSON, it is important to unlearn the rules of normalization.&nbsp; JSON allows to aggregate information that belongs together so it is ready to be used, instead of splitting data across separate tables, as normalization rules would dictate.&nbsp; In other words, there’s an opportunity to join the data “on write”, instead of the traditional joins “on read” of relational databases which negatively impact performance. &nbsp;

&nbsp;

![JSON order denormalized structure](<lib/JSON%20order%20denormalized%20structure.png>)

&nbsp;

This difference is decisively important nowadays when real-time web applications and big data require high scalability and high availability.&nbsp; Note that this capability is not limited to JSON, as other types of NoSQL databases achieve the same result in different ways.

![Image](<lib/Query-Driven%20schema%20design.png>)

&nbsp;

&nbsp;

&nbsp;

In NoSQL, you first define the queries for the application, then you store the data according to the query needs.&nbsp; It is said that data modeling for NoSQL should be “query-driven.”&nbsp; This aspect is critical to the success of NoSQL projects. &nbsp; A query-driven design of the JSON document schema means that, ideally for every time that the application needs to retrieve data from the database, all of the necessary data should be found with a single access to the database, without having to join it with data coming from other places.

&nbsp;

This approach is called [embedding](<https://hackolade.com/help/OverviewofJSONandJSONSchema.html#JSON%20in%20databases>), whereby the data, that would be in separate tables if normalized, is assembled and stored in a single atomic document, so it can be easily retrieved.&nbsp; Embedding is often opposed to referencing, which leverages foreign key relationships to the data stored elsewhere.&nbsp; While referencing is clearly more efficient in terms of storage costs, embedding provides much higher access performance and is easier for developers to manipulate.

&nbsp;

For queries returning multiple results, the idea is to retrieve all of the documents from ideally a single partition, so as to avoid having to gather information from multiple places.

&nbsp;

## Factors to take into consideration

JSON seems to liberate users from the constraints of normalization.&nbsp; But you should exercise caution when it comes to deep nesting and unbounded arrays.

&nbsp;

### Document size and transaction volume

When embedding into a single document, you must make sure to understand how the document will grow in size.&nbsp; While storage is cheap, you should also take into consideration the transmission impacts.&nbsp; To illustrate the point, if the document will be used on a mobile phone using a 4G network, does it make sense to transmit a 1 megabyte document if only a small portion of it is really necessary?&nbsp; Plus, your cloud provider may be charging for input/output traffic, so you may want to evaluate document size and transaction volume.

&nbsp;

### Cardinality of relationships

Some document designs lead to a situation where data elements are constantly added to arrays.&nbsp; An unbounded array, i.e. an array with no limit to the number and size of array items being added, may grow to an unpredictable document size, with potentially negative impacts on performance and transmission costs.&nbsp; In some extremes you may even run into limits set by database providers, generally 16MB. &nbsp;

&nbsp;

When looking at embedding of one-to-many relationships, it is important to estimate the cardinality: are we talking about one-to-few, one-to-zillions, or somewhere in-between?&nbsp; Also, is the cardinality following a normal distribution, or do we have extreme outliers that require special treatment?

&nbsp;

### Referential integrity

Detractors keep saying that NoSQL databases are not [ACID-compliant](<https://en.wikipedia.org/wiki/ACID> "target=\"\_blank\"") and would therefore not be usable in a transactional use case.&nbsp; Such criticism, often driven by bias or lack of knowledge, does not take into account several arguments, mainly that atomicity, integrity and consistency can be naturally achieved through embedding.&nbsp; Another factor, particularly in our modern connected world, is the fact that ACID is only possible when the system owns the full transaction end-to-end.&nbsp; Nowadays, resilience must be built into API processing more than database enforcement.

&nbsp;

Nevertheless, data quality and integrity should be a concern when designing application and schemas.&nbsp; And it is possible that some enforcement must be built at the application level.

&nbsp;

### Indexing impacts

Indexes have their costs, and they're tempting features reminding us of the days of normalization.&nbsp; Some document designs, for example with a fully polymorphic model, lead to an undesirable proliferation of indexes.&nbsp; Whereas generic key-value pairs, while reducing the number of indexes, may lead to a loss of semantics with low integrity enforcement.&nbsp; Indexes are not free, so alternative access patterns must be evaluated and discussed.&nbsp; Maybe more data duplication is more effective than indexing?

&nbsp;

## Schema versioning and schema migration

One of the huge benefits of flexible structures in JSON, is the ability to evolve schemas without interruption of database operations.&nbsp; But this feature should not be abused to the point that dozens of schema versions of the same document are supported by the application.&nbsp; As a matter of fact, if more than a single application is reading the data, it quickly becomes a nightmare to synchronize schema handling across multiple applications, let alone reporting and analytics tools.&nbsp; Besides, endless conditional branches in the application code unnecessarily burn CPU cycles.

&nbsp;

Best practices at major companies leverage schema versioning for transition periods, but are rigorous in quickly migrating old schema structures to the latest version before chaos occurs.&nbsp; Several strategies are used:&nbsp;

* eager migration: like in the old days... convert the data prior to launching a new version of the software.&nbsp; This strategy does not leverage the flexible evolution capabilities of JSON;
* lazy migration: update the schema of a document only after it has been used.&nbsp; A potential issue is that some documents will never be accessed, hence the migration will never end;
* incremental migration: arbitrary chuncks of data are migrated, ideally at times when database loads are lower;
* predictive migration: heuristics and probabilistic judgments are used to migrate documents before they are used;
* combination of predictive migration first, followed by incremental to finish off the migration;
* endless versioning: not desirable, particularly if constant evolution of the schema.

&nbsp;

### Backward- and forward-compatibility

No database is an island.&nbsp; There may be many systems interacting with it.&nbsp; It is critically important to avoid the introduction of breaking changes. Even when planned and communicated, they have huge impacts on agility and costs.&nbsp; By thinking through each evolution, it is possible to leverage features in schema standards (JSON Schema, Avro, etc.) to ensure the full compatibility of schemas.&nbsp; That way consumers and producers can upgrade at their own pace.

&nbsp;

### Choice of partition or sharding keys

Another great advantage of NoSQL databases is their horizontal scaling capability, which is achieved through the distribution of data across servers, data centers, and geography.&nbsp; But efficiently leveraging this capability requires careful design.&nbsp; It is a balancing act between spreading evenly storage and load across the different partitions/shards, and the efficient retrieval of information when serving queries, so the information can be retrieved from a minimal number of partitions/shards - ideally just one.&nbsp;

polymorphis

&nbsp;

## Facilitating communication and collaboration

Hackolade Studio is a graphical tool for entity-relationship diagrams, extended to represent nested objects found in popular technologies for databases and data exchanges.&nbsp; Developers might tell you that, if you want to see the schema, you should just look at the code...&nbsp; Probably not the best way to promote collaboration, particularly with non-programmers.

&nbsp;

Good practices teach us that schema design for NoSQL databases is even more important than for relational databases where rules of normalization provide some guardrails.&nbsp; JSON is so flexible and powerful that it can be dangerous in the hands of inexperienced developers or with ignorance of all the factors described above.

&nbsp;

An ERD picture is worth a thousand words.&nbsp; It fosters communication and helps think through the different ways to denormalize information and balance the different constraints.&nbsp; It also lets non-developers easily visualize and understand data structures that are the foundation of applications and data exchanges.&nbsp; If business users don't understand the context and meaning of the data, it becomes difficult to deploy self-service analytics or make accurate business decisions.

