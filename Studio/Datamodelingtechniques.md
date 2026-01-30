# Data modeling techniques

Hackolade Studio provides support for different techniques of data modeling for our different targets.&nbsp; Of course we support relational for RDBMS through Entity-Relationship Diagrams, complex data types for NoSQL and storage formats, graph diagrams for graph databases and conceptual modeling, etc.. &nbsp;

&nbsp;

For big data analytics, we also support 2 very popular methodologies: Dimensional, and Data Vault 2.0.&nbsp; The choice of data modeling technique is available for all Hackolade Studio targets in the category of big data analytics: BigQuery, Delta Lake/Databricks, Hive, Redshift, Snowflake, Synapse, and Teradata.

&nbsp;

For these targets, the choice of modeling technique is made at the model level:

![Modeling technique - choice](<lib/Modeling technique - choice.png>)

&nbsp;

&nbsp;

## Relational modeling

Relational data modeling is most effectively carried out using **Entity-Relationship Diagrams (ERDs)** because they provide a conceptual, implementation-independent way to describe the structure of data before it is translated into tables and constraints.&nbsp; ERDs make explicit the core elements of a relational schema: entities with identity, attributes that describe them, and relationships that define how they are connected.&nbsp; By separating semantic understanding from physical design, ERDs allow modelers to reason about correctness, cardinality, and integrity rules without prematurely committing to storage details.&nbsp; This clarity not only improves communication between business and technical stakeholders, but also leads naturally to well-structured, normalized relational schemas that can be implemented consistently across SQL databases.

&nbsp;

By default, Hackolade Studio uses ERDs to represent data structure, using Information Engineering (IE) notation. &nbsp;

&nbsp;

**Note:** IDEF1X notation is not currently supported, but could be, upon request.&nbsp; UML models can be imported, converted to ERD or JSON Schema, but we the tool does not forward-engineer UML.

&nbsp;

## Dimensional modeling

Dimensional modeling is a data modeling technique used in data warehousing and business intelligence (BI) systems. It is specifically designed to support analytical reporting and data analysis. Dimensional modeling organizes data into easily understandable and intuitive structures known as dimensional models, which consist of dimensions and facts.

&nbsp;

Dimensions represent the different perspectives or characteristics of the data being analyzed. They provide the context in which the facts are analyzed and include descriptive attributes. Examples of dimensions could be time, geography, product, customer, or any other aspect that adds meaningful information to the analysis.

&nbsp;

Facts, on the other hand, are the measurable, numerical data points that are being analyzed. They are often the focus of analysis and represent the metrics or key performance indicators (KPIs) of interest. Facts are typically numeric values that can be aggregated, such as sales revenue, quantity sold, or profit.

&nbsp;

In a dimensional model, dimensions and facts are organized into a star schema or a snowflake schema.&nbsp;

* In a star schema, the fact table is at the center, surrounded by dimension tables radiating outwards. Each dimension table is joined to the fact table through a foreign key relationship. This structure resembles a star, hence the name. The star schema is simpler and easier to understand and query, making it a popular choice in dimensional modeling.
* In a snowflake schema, dimension tables are normalized, meaning they are further divided into sub-dimension tables. This results in a more complex structure, resembling a snowflake. The snowflake schema can be useful in scenarios where dimensions have hierarchical relationships or when there is a need to reduce data redundancy.

&nbsp;

Dimensional modeling aims to optimize query performance and facilitate easy navigation and analysis of data. It provides a user-friendly structure that aligns with how users think about and analyze data, making it well-suited for reporting and ad-hoc analysis. By organizing data into dimensions and facts, dimensional modeling enables users to slice and dice data, drill down into details, and perform aggregations efficiently, leading to faster and more insightful decision-making.

&nbsp;

In dimensional modeling, the terms "outrigger" and "staging" are concepts that can be used in the context of dimensional models. The use of outrigger dimensions and staging tables is not mandatory in all dimensional modeling scenarios. They are optional components that can be utilized based on the specific requirements of the data integration and analysis processes.

* An outrigger dimension is an additional dimension table that is related to the main dimension table in a dimensional model. It provides additional descriptive attributes that are not directly associated with the fact table but have a relationship with a specific subset of dimension records. The outrigger dimension expands the information available for analysis by connecting to specific dimension records.&nbsp; For example, consider a sales dimensional model with a main dimension table for "Product" and an outrigger dimension table for "Product Category." The main dimension table would include attributes such as product ID, name, and price. The outrigger dimension table, in this case, could contain attributes like product category ID, name, and description. By connecting the outrigger dimension to specific product records, you can analyze sales performance based on product categories.
* A staging table is a temporary or intermediate table used in the data integration process. It is typically employed when loading data from various source systems into a data warehouse or data mart. The staging table acts as a temporary storage area where data from different sources is collected, cleansed, transformed, and validated before being loaded into the final dimensional model.&nbsp; Staging tables help ensure data quality and consistency by allowing data transformations, data type conversions, data validation, and error handling before the data is loaded into the main dimensional model.&nbsp;

&nbsp;

They provide a controlled environment for data preparation and allow for data cleansing operations like removing duplicates, handling missing values, and resolving data inconsistencies. Once the data in the staging table has been transformed and validated, it can be loaded into the appropriate dimensional tables in the data warehouse or data mart. Staging tables facilitate the ETL (Extract, Transform, Load) process and help maintain data integrity and accuracy in the final dimensional model.

&nbsp;

You may assign a role to each table in your dimensional model:

![Modeling technique - dimensional table role](<lib/Modeling technique - dimensional table role.png>)

&nbsp;

## Data Vault 2.0 modeling

Data Vault 2.0 is an advanced data modeling and data warehousing technique that provides a scalable, flexible, and resilient approach to storing and integrating enterprise data. It was developed by Dan Linstedt and is an evolution of the original Data Vault modeling technique.

&nbsp;

The key principles of Data Vault 2.0 include:

&nbsp;

* Hub, Link, and Satellite Modeling: Data Vault 2.0 organizes data into three primary components: Hubs, Links, and Satellites. Hubs represent the core business entities or concepts, Links capture the relationships between hubs, and Satellites store the descriptive attributes or metadata related to the hubs or links. This modeling approach allows for a highly flexible and extensible data structure.

&nbsp;

* Business Key Approach: Data Vault 2.0 emphasizes the use of business keys as unique identifiers for data entities. Business keys are non-intelligent, non-sequential values that uniquely identify a business entity across different source systems. This approach helps in data integration by enabling easy traceability and auditability of data across various systems.

&nbsp;

* Historical Tracking: Data Vault 2.0 incorporates historical tracking of data changes as a fundamental concept. Every record in a Data Vault model is assigned a unique identifier, load date, and load end date to track the evolution of data over time. This historical tracking enables a complete audit trail and supports temporal analysis and historical reporting.

&nbsp;

* Scalability and Flexibility: Data Vault 2.0 is designed to handle large volumes of data and accommodate changing business requirements. Its modular structure allows for incremental additions and modifications to the data model without requiring extensive changes to the existing structure. This scalability and flexibility make Data Vault 2.0 suitable for agile data warehousing and accommodating evolving business needs.

&nbsp;

* Automation and Integration: Data Vault 2.0 emphasizes the use of automation and tooling to streamline the development and maintenance of data vault solutions. Automated processes are employed for loading data into the data vault, generating business keys, managing metadata, and performing data transformations. Integration with ETL (Extract, Transform, Load) tools and data integration platforms is an essential aspect of Data Vault 2.0.

&nbsp;

By implementing Data Vault 2.0, organizations can achieve a comprehensive and adaptable data warehousing solution that enables data integration from diverse sources, maintains data lineage and auditability, supports historical analysis, and provides a foundation for analytics, reporting, and business intelligence. It is particularly suitable for complex and rapidly changing data environments.

&nbsp;

Additionally, let's explore the concepts of bridge, point in time, and reference:

* a bridge table is used to model a many-to-many relationship between two entities. It serves as an intermediary table that connects the hubs in a Data Vault model. The bridge table captures the associations or relationships between multiple instances of the hub entities
* the point in time concept refers to the practice of capturing and preserving historical changes to data at different points in time. It involves storing time-varying attributes in separate satellite tables to maintain a historical record of how data values evolve over time.
* the reference concept in Data Vault 2.0 refers to the practice of using reference tables or reference data to standardize and maintain consistency in the data model. Reference tables contain predefined, static data such as codes, classifications, or lookup values that provide context and meaning to the data in the hubs or links.

&nbsp;

You may assign a vault component to each table in your vault model:

![Modeling technique - data vault components](<lib/Modeling technique - data vault components.png>)

&nbsp;

&nbsp;

## Graph modeling

Graph modeling takes a fundamentally different approach by representing data as nodes and edges, each annotated with labels and properties, making relationships first-class citizens of the model rather than secondary constructs derived from joins.&nbsp;

&nbsp;

In Labeled Property Graph databases such as Neo4j or systems based on Apache TinkerPop (via Gremlin), node labels define the types of entities (for example, Person, Order, or Device), while edge labels define the semantics of relationships (PURCHASED, FRIENDS\_WITH, CONNECTED\_TO), with both nodes and edges carrying arbitrary key-value properties. This explicit labeling allows the structure of the domain to be expressed directly in the graph and queried through pattern matching rather than joins.&nbsp;

&nbsp;

In Semantic Knowledge Graph databases such as Ontotext GraphDB or Stardog, the same idea is taken further through formally defined vocabularies and ontologies, where node and edge labels correspond to RDF classes and predicates with well-defined meaning.&nbsp;

&nbsp;

In both cases, graph modeling excels at representing highly connected, evolving domains, where understanding and traversing relationships is more important than enforcing rigid tabular structure.

&nbsp;

Hackolade Studio provides graph diagrams: by default for graph targets, and also in Polyglot models for user-friendly conceptual modeling.

&nbsp;

## Hierarchical modeling

Hierarchical data modeling focuses on representing information as nested JSON document structures, where containment and structure directly reflect how data is stored and accessed, rather than being inferred through joins.&nbsp;

&nbsp;

Hackolade Studio was designed specifically for this paradigm to support document-oriented databases like MongoDB, Couchbase, Elasticsearch, MarkLogic, and Azure Cosmos DB, as well as storage/exchange formats such as Avro, Parquet, Protobuf, Swagger/OpenAPI.&nbsp;

&nbsp;

In hierarchical modeling, the primary concern is the shape of the document: nested objects express ownership and lifecycle dependency, arrays represent one-to-many containment, and optional fields or variant substructures accommodate schema evolution and polymorphism.&nbsp; Unlike relational or graph models, relationships are often implicit in the hierarchy itself, with embedding chosen deliberately to optimize locality, read performance, and alignment with application data structures.&nbsp;

&nbsp;

Hackolade Studio makes these design choices explicit by visually modeling JSON schemas, nested levels, and schema variants, enabling architects to reason about containment versus reference, denormalization, and evolution in systems where the document -- not the table or the edge -- is the fundamental unit of data.

&nbsp;

