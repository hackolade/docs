# Overview

The Hackolade Enterprise Model Hub is a model-driven metadata collaboration platform providing a unified and central access to your Hackolade Studio data models stored in one or more Git repositories.&nbsp; It empowers business teams, governance teams, technical teams, and other stakeholders to collaborate efficiently and promote a shared understanding of the context and meaning of data across the organization.&nbsp; The Model Hub allows users to browse, search, drill down, then view and navigate lineage, descriptions, and details of data assets in your data models for SQL and NoSQL databases, APIs and other data exchanges, storage formats, reports, charts, and dashboards.

&nbsp;

The Model Hub is composed of a database, a replication mechanism from the Git repositories (where your Hackolade data models are stored), and a browser-based portal access. The Hub provides browsing, search, visualization in grid views, and lineage capabilities across all models replicated from the Git repository. &nbsp;

&nbsp;

The current capabilities will continue to be regularly enhanced as new features become available. Upcoming features may include graphical visualization of attribute lineage, categorization by domain,&nbsp; definition of one or more glossaries and assignment of terms to attributes, threaded conversations, possibility to assign user-defined tags to any asset, etc... Feel free to provide feedback and suggestions.

&nbsp;

The Model Hub is a separate product from Hackolade Studio, and complementing it.&nbsp; It requires an additional add-on license option.&nbsp; A demo playground of the Model Hub is available at [https://hub.hackolade.com/](<https://hub.hackolade.com/> "target=\"\_blank\"") &nbsp;

&nbsp;

![Model Hub metadata collaboration platform](<lib/Model Hub metadata collaboration platform.png>)

&nbsp;

&nbsp;

Data models authored with Hackolade Studio and pushed to the Git repository are automatically replicated into a secured instance of the Hub database dedicated to your organization, so they can be accessed in the Hub portal by authorized users.

&nbsp;

The Hub is read-only for portal users.&nbsp; But any modification of data models pushed to the Git repo's main branch is immediately replicated to the Hub database.

&nbsp;

The Hub greatly extends the capabilities of Hackolade Studio through a data model and metadata collaboration platform to turn data structure into insights, information, and knowledge across the organization.&nbsp; Data professionals achieve improved understanding and compliance through the use of this integrated platform for data models, metadata, and collaboration.

&nbsp;

![Hackolade Enterprise Model Hub overview](<lib/Hackolade Enterprise Model Hub overview.png>)

&nbsp;

## Collaborative Enterprise Metadata Hub

The Hackolade Enterprise Data Model Hub database and portal empowers organizations by streamlining the structure, the organization, and the sharing of data, creating a unified understanding of its semantic meaning and context across both business users and IT teams. It provides a solid foundation for effectively managing data throughout the organization.

&nbsp;

As enterprise data management evolves, it is essential to connect data with knowledge -- placing real-world concepts and relationships at the forefront, rather than relying on complex, opaque technical schemas. To use data accurately and effectively, users need to understand not only how the data is structured, but also its meaning. The primary barrier to generating accurate business insights is the lack of shared understanding regarding the meaning of data. This issue arises when data producers and consumers interpret terminology differently.

&nbsp;

At the core of conveying information is the concept of a data model, which defines how data is organized and how to interpret its meaning. In information systems, semantics refers to how data behaves and how it should be understood by humans and by machines.

&nbsp;

Data modelers, architects, and engineers possess the expertise to analyze, document, and must conveniently share critical models and metadata across the organization. They can establish consistency in business terminology and metadata for all data models, while business users can contribute to building a reliable reference.

&nbsp;

Complex concepts such as master data and transactional data, with multiple entities and relationships, can now be represented more clearly, fostering alignment between IT and business teams. This enables both technical and business users -- across any size of organization -- to make high-stakes decisions with confidence, knowing they share a consistent understanding of the corporate metadata. They can trust that data interpretations will remain consistent across various sources, including structured, semi-structured, and unstructured data.

&nbsp;

The Hackolade Enterprise Model Hub enables data professionals to document, interpret, and fully control the enterprise data environment. When organizations can interpret and share data accurately, and reuse it efficiently, the quality of business decision-making improves. Understanding the origins, targets, and transformations of enterprise data is a crucial step for achieving reliable data quality across the organization.

&nbsp;

The data models feeding the Model Hub may have been created from scratch in Hackolade Studio, migrated form legacy tools, or reverse-engineered from any of the technology targets supported by Hackolade Studio.

![Hub metadata harvesting](<lib/Hub metadata harvesting.png>)

&nbsp;

&nbsp;

## Key features

**\- Shift-Left and Design-First:** traditional data catalogs and metadata management solutions typically focus on harvesting metadata only after data assets are in production, which limits proactive collaboration and subject-matter experts involvement prior to deployments.&nbsp; In contrast, the Hackolade Model Hub is built around data models and schema designs that can be created from the ground up or evolved throughout the application lifecycle.

**\- Metadata harvesting**: while advocating a design-first approach, we also provide a searchable data assets inventory, leveraging the Hackolade Studio reverse-engineering of 40+ data sources: SQL and NoSQL databases, APIs, storage formats.&nbsp; On-demand and/or schedule-based data discovery is easily done with Hackolade Studio's Command-Line Interface, to simplify the aggregation and collection of metadata across diverse data ecosystems.

**\- Search and filter** across all models in your selected repo(s), whether polyglot models or physical target models, for all objects: containers, entities, and attributes.&nbsp; And see their respective properties.

**\- Browse and drill down** model objects in grid tables: business users may be less comfortable with entity-relationship diagrams, and prefer to explore models in grid views

**\- Single-click access** to selected ERD model: Model Hub Portal users can also open the corresponding model Entity-Relationship Diagram in the Hackolade Studio browser (provided that they have also a Studio license, and have been granted the rights to read the model in the Git repo.)

**\- Model lineage**: Hackolade Studio advocates a modular and [domain-driven data modeling approach](<https://hackolade.com/domain-driven-data-modeling.html>).&nbsp; As a result, you may have a complex chain of models derived from polyglot and/or using external references to a library of definitions.&nbsp; The Model Hub Portal includes a powerful, searchable, graphical view of the model dependencies

**\- Always run the latest version** of the application: no effort to always access the latest feature enhancements, as described in the [Model Hub Architecture](<ModelHubtechnicalarchitecture.md>) page

**\- Serverless architecture:** secure, scalable, and cloud-native, with no need for installation, maintenance, upgrade of an application and web server

**\- Remain in full control and ownership of your data and data models:** complete autonomy over the residency for your data models

\- Attribute-level vertical lineage, where-used, and impact analysis (TBA)

\- Threaded conversations (TBA)

\- Metadata curation (TBA)

\- Glossary of business terms (TBA)

\- Tags for annotations (TBA)

\- Reports (TBD)

&nbsp;

## Key Benefits

**\- Improve metadata collaboration across IT and business teams:** democratize the use of data through visualization and collaboration. Capture and share knowledge.&nbsp; Reduce the time required to identify and address costly data quality challenges.&nbsp; Understand data structure and relationships.&nbsp; Provide feedback and change requests to model authors

**\- Empower self-service business users:** provide convenient access to metadata with powerful and flexible search capabilities, plus a view of the data models, ERDs, and schema artifacts

**\- Gain a deeper understanding of your data:** let business users explore data structures and relationships within the organization at their own pace. They can analyze entities, attributes, and relationships, gaining valuable insights into how different data elements interact

**\- Strengthen data governance:** data modelers and domain experts collaborate to ensure that definitions align with business needs, while maintaining standardization, integrity, and quality

**\- Accelerate decision-making:** enable quick access to reliable data, reducing dependencies on IT, and minimizing delays caused by data quality issues or misalignment.

&nbsp;

&nbsp;

&nbsp;

## **Use Cases**

### **Data Discovery \& Business Glossary**

* Establish a shared understanding of data between IT and business teams.
* Quickly locate data across various sources, including databases, object storage, data lakes, warehouses, lakehouses, exchanges, and catalogs.
* Manage a business glossary alongside technical data to support data governance initiatives.

### **Target Personas**

* **Business Domain/Subject Matter Experts** – Access data models without requiring technical expertise, ensuring alignment between data insights and business objectives.
* **Data Stewards** – Oversee data quality, integrity, and compliance by managing and governing data assets.
* **Data Architects** – Understand data model relationships, maintain reusable definitions, and ensure security, scalability, and business alignment.
* **Data Modelers** – Identify available data assets to maintain consistency, integrity, and optimal structuring for efficient use and analysis.
* **Data Analysts** – Examine data to identify trends, generate insights, and support informed decision-making.
* **Data Scientists** – Work with complex data to extract predictive insights and develop AI/ML models.
* **Data Engineers/Developers** – Easily locate data models to generate schemas, maintain pipelines, and manage data infrastructure.

### **Why Organizations Need It**

#### **Enable Seamless Collaboration Between IT \& Business**

Organizations face challenges in managing and accessing data, including:

* **Difficulty in finding the right data for analytics**

  * Siloed data sources
  * Conflicting "single sources of truth"
  * Lack of a unified view of data assets
  * Troubleshooting data issues is cumbersome
  * Metadata and lineage for data lakes are insufficient

* **Lack of a standard data dictionary**

  * Manual schema definitions slow down workflows
  * No streamlined method to share data models across applications
  * Limited support for data governance

* **Challenges with data ownership and security**

  * Unclear accountability for data assets
  * Inconsistent business terminology
  * Limited collaboration on resolving data inconsistencies
  * Unchecked proliferation of sensitive data

### **Key Capabilities**

#### **Hackolade Studio Integration for Data Design \& Communication**

* Provides a **read-only** view of golden-source data models, ensuring integrity while allowing users to comment, flag warnings, and endorse assets.
* Supports **automated publishing** from Git repositories using pre-configured actions.

#### **Secure, Scalable, Cloud-Native Architecture**

* **Built for cloud security** – serverless, scalable, and optimized for enterprise use.
* **Data remains under user control** – users can bring their own storage, with no SaaS-based data retention.
* **Role-based access control** – supports LDAP/IAM-based policy enforcement.

#### **Metadata-Driven Virtual Data Catalog**

* **Vendor-neutral** solution compatible with diverse databases and data-in-motion frameworks.
* **Automatically generated metadata** from existing data models for improved discoverability.
* **Intuitive search \& browsing** with filters based on technical names, business terms, glossary entries, and tags.

#### **Metadata Curation \& Enrichment**

* Define and maintain **business glossaries** with categorized business terms.
* Use **tags** to annotate and classify data assets.
* Establish relationships between assets, business definitions, and metadata.

&nbsp;

