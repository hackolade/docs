# Containers in ER diagram

In Hackolade Studio, we use the generic name of "container" to designate a grouping of entities.&nbsp; In physical data models, this container bears a different name depending on the target technology: schema in relational and analytics databases, database in MongoDB, bucket (legacy) and now scope in Couchbase, index in Elasticsearch, namespace in Avro, keyspace in Cassandra, group in JSON, resource in REST APIs, operation in GraphQL, file in Parquet and Protobuf, graph in graph databases and RDF triple stores, etc.

&nbsp;

If necessary for your application, you can define multiple container in the same model, possibly with inter-container (cross-schema) relationships

&nbsp;

![Couchbase multi-bucket model](<lib/Couchbase multi-bucket model.png>)

&nbsp;

Containers are not mandatory in models, but recommended if you want DDLs to be complete. In Hackolade Studio, there are many ways to add a container to the central pane canvas:

\- menu : Action \> Add Container (added at default location)

\- keyboard shortcut (Ctrl/Cmd+B): added at location of mouse cursor

\- toolbar: Add Container icon: added at location of mouse cursor

\- Diagram Object pane: Add container via click (added to default location), or via drag-and-drop to the location of your choice

\- Object Browser pane: right-click on model name and use contextual menu (added at default location)

\- Central pane: right-click on model name and use contextual menu (added at default location)

&nbsp;

&nbsp;

