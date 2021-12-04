# Schema versioning

The subjects of schema versioning, document polymorphism, and possibly schema migration, are a vast and sometimes controversial subject...\
\
When it comes to displaying the schema for a MongoDB collection, there are several features that come into play:

&nbsp;

***Required property***\
When fields are required to appear in every document, we have a visual in the ERD (a star \* when a field is required) and a property in the properties pane. When we reverse-engineer a collection to infer the schema, we will mark as "required" any field that appears in 100% of the documents sampled.  If a field appears in strictly less than 100% of the sampled documents, it will not be marked as required.

&nbsp;

***Multiple data types***\
A given field name can have multiple data types.  We support this too.  Not only for scalar data types, but also for complex data types (objects and arrays.)  Their representation differs depending on whether all the multiple data types are scalar (we simply display the word "multiple" in the ERD and show the details in the properties pane)

&nbsp;

![Multiple data type - select](<lib/Multiple%20data%20types%20-%20select.png>)​

![Image](<lib/Multiple%20data%20types.png>)​\
\
or at least one of them is a complex data type.  In this case, we have to represent them using a oneOf choice, for example:

![Image](<lib/Polymorphism%20simple.png>)​\
\
In the ERD, the representation is as follows:

![Polymorphism ERD](<lib/Polymorphism%20ERD.png>)​

\
We detect this polymorphism during reverse-engineering.

\
&nbsp;

**Schema versioning**\
Schema versioning can be tricky to auto-detect during reverse-engineering.  That's because we can't tell whether missing fields are on purpose, or as a result of a schema evolution (or worse, as a result of lax development...)  But you may for example specify a query for a particular version to be used during reverse-engineering, then repeat the operation for another schema version, then merge the version using a oneOf choice as mentioned above.  

&nbsp;

## Schema migration

Document databases are quite permissive.&nbsp; Used properly, this is a huge advantage.&nbsp; But it also has some drawbacks:

* if too many versions must be maintained, it can quickly lead to diminishing returns and extraneous CPU cycles.&nbsp; Use with moderation.
* if multiple applications read the data, all must be aware of each schema evolution for coherence and integrity.&nbsp; If too many applications are unable to synchronize their lifecycles, this situation becomes rapidly unmanageable.

&nbsp;

Of course, one of the great benefits of NoSQL databases is the ability to evolve schemas without downtime.&nbsp; But contrary to popular belief, we observe that best practices, at major organizations having successfully used NoSQL databases for a long time, include systematic schema migration to counter-balance the caveats mentioned above. &nbsp;

&nbsp;

There are several schema migration strategies:

* eager migration: all documents are migrated at the introduction of a new schema version (sort of like we used to do with RDBMS, but without downtime...) &nbsp;
* lazy migrations: when reading a document of an old schema version, it is written back with the latest schema version.
* predictive migration: leveraging low system load times, documents can be migrated based on a forecast of near-future need.
* incremental migration: after predictive migration is mostly completed, the remaining documents can be migrated in blocks until full completion is reached.
* no migration: multiple schema versions are maintained.

&nbsp;

Each strategy has its pros and cons, and an associated cost.&nbsp; You should evaluate the strategy best suited for each use case.&nbsp; The context of a specific collection might warrant its specific strategy.&nbsp; Hackolade does not currently provide migration features or services.

