# Hub FAQs

The Hackolade Data Model Hub is a model-driven metadata management platform.&nbsp; It is a separate but complementary product of the Studio application.&nbsp; The Frequently Asked Questions below may help you better understand the Hub characteristics and added value.

&nbsp;

## Competitive positioning

### Compared to server-based legacy data modeling tools (e.g., Erwin Mart, ER/Studio Team Server, PowerDesigner Portal)?

While traditional modeling server products rely on proprietary, on-premises architectures, Hackolade takes a modern, open approach. The Hackolade repository is Git-native, storing models in transparent, portable JSON format and integrating seamlessly with GitHub, GitLab, Bitbucket, or Azure DevOps. This enables versioning, branching, audit trails, and collaborative workflows, a functionality typically managed manually or rigidly in legacy tools.

&nbsp;

The Hub further enhances collaboration with advanced search, filtering, browsing, lineage, and impact analysis within a browser-friendly, DevOps-aligned environment.

&nbsp;

Compared to SaaS-only tools like SqlDBM or Vertabelo, Hackolade offers a hybrid model. You retain full control over your models and data, without being locked into a vendor’s cloud or constrained by limited customization options.

&nbsp;

Hackolade's schema design support across relational, dimensional, NoSQL and semi-structured databases is more extensive than that of any legacy tool, offering flexibility for modern data architectures.

&nbsp;

### Compared to business-facing metadata management platforms like Collibra or Acryl DataHub?

Hackolade doesn’t aim to replace these enterprise-grade data governance tools but complements them by addressing critical blind spots both upstream and downstream.

&nbsp;

**Upstream**, Hackolade empowers teams to be proactive. Rather than just retroactively harvesting metadata from systems already in production, metadata which are often flawed or outdated, Hackolade Studio allows you to design models collaboratively *before* deployment. This prevents costly design mistakes and ensures early stakeholder alignment.

&nbsp;

**Downstream**, Hackolade serves the needs of technical teams where business-facing platforms fall short. Hackolade Studio produces machine-readable artifacts like DDLs and schema definitions, enabling direct deployment.&nbsp; Something most governance tools simply can’t do.

&nbsp;

Through integrations with major metadata platforms, Hackolade bridges business and technical silos, ensuring consistency and traceability across the full data lifecycle.

&nbsp;

The Hub offers mid-market organizations an accessible entry point into structured metadata collaboration, without the overhead of a full-blown enterprise data governance solution.

&nbsp;

### Compared to technical catalogs (Databricks, AWS Glue, Iceberg, Snowflake) and schema registries (Confluent, EventBridge, EventHub) or API repositories (Swagger, Apollo)?

Technology-specific catalogs and registries serve their native platforms well, but that’s precisely their limitation. In today’s polyglot data environments, each becomes a silo, making metadata governance fragmented and inconsistent.

&nbsp;

Hackolade bridges those silos. It aggregates metadata across diverse technologies - databases, schemas, APIs, and registries - into a unified, model-driven collaboration hub. Rather than replacing these technical catalogs, Hackolade enhances them by centralizing visibility, standardizing documentation, and enabling cross-platform lineage and impact analysis.

&nbsp;

Hackolade also facilitates API-first and schema-first design workflows, ensuring alignment between upstream data modeling and downstream system implementations.

&nbsp;

### Compared to semantic metrics layer tools or the integrated catalogs in BI platforms like Qlik, Looker, Tableau, Power BI, Cube.dev, or AtScale?

Semantic layers and BI tool catalogs are designed to serve business analysts by abstracting complex data into user-friendly terms, metrics, and dimensions for reporting and visualization. They are optimized for *consumption* of data, not *design* or *governance* of data structures themselves.

&nbsp;

Hackolade addresses an earlier stage in the data lifecycle. It provides a **model-driven foundation** for defining, documenting, and evolving data structures -- before they are consumed by BI tools. Rather than focusing on metric definitions or visualization metadata, Hackolade ensures that the underlying data models are well-structured, version-controlled, and aligned with both technical and business requirements.

&nbsp;

Where semantic layers operate on top of existing datasets, Hackolade helps shape those datasets from the beginning, supporting proactive data design, stakeholder collaboration, and integration with source systems, APIs, and schema registries.

&nbsp;

Hackolade complements semantic layers by upstreaming data governance and enabling a consistent, technically sound foundation for downstream analytics and reporting tools.

&nbsp;

&nbsp;

## Technical concerns

### Is the Hub a SaaS product?

Not in the traditionally understood sense of the term.&nbsp; Software-as-a-Service is a popular solution deployment approach.&nbsp; Users don't need to install anything on their machines to access the service - it all runs in the browser.&nbsp; No need to upgrade either.&nbsp; The application always runs the latest version. &nbsp;

&nbsp;

This may be seen as a huge improvement over the previous setup of on-premises applications, or applications run in a cloud Infrastructure-as-a-Service setup.&nbsp; SaaS applications shift the responsibility to install, monitor, upgrade, backup, and operate the application from the customer to the provider.

&nbsp;

But for most SaaS solutions, this means that the provider stores all the data.&nbsp; The main drawbacks include vendor lock-in due to the data residency, confidentiality, security, and integration complexity.&nbsp; Most SaaS solutions store your data in the provider's database and process it on their servers.&nbsp; While there are standards, certifications, and insurance coverage for SaaS operations, how can customers be 100% sure that their data is in the right hands?&nbsp; That the provider treats it with the same care that you would?

&nbsp;

It seems that there would be no perfect solution - just a choice of the least bad compromise, according to each organization's priorities.

&nbsp;

Instead, Hackolade provides an innovative architecture that combines the advantages of both on-premises and SaaS solutions.&nbsp; The Data Model Hub always runs the latest version of our software in your browser (so you don't need to install, maintain or upgrade it) but you keep 100% percent control of your data.&nbsp; The only traffic coming out of your network is when users validate the license key.

&nbsp;

![Hub Studio Desktop Browser Architecture](<lib/Hub Studio Desktop Browser Architecture.png>)

&nbsp;

Hackolade has always developed solutions taking into account a security-first principle and constraint: no data should ever come out of the customer network.&nbsp; Processing is done strictly client-side in your browser.&nbsp; At Hackolade, we do not operate any database.&nbsp; We don't collect, process, or store any data from any customers.

&nbsp;

Your data models never leave your control.&nbsp; They are maintained and saved in your Git repository.&nbsp; If you use the Hub, they are replicated into your Hub database, entirely operated by you, but in a low-maintenance autonomous manner.&nbsp; Consult this [Model Hub architecture page](<ModelHubtechnicalarchitecture.md>) for more details.

&nbsp;

### Is there an on-premises version of the Hub?

No.&nbsp; An on-premises version of the Hackolade Data Model Hub would defeat the purpose of saving customers the hassles of running the application on their own hardware.&nbsp; Expensive, inconvenient, and always functionally behind.

&nbsp;

The database version required is Oracle 23ai Autonomous JSON, currently only available on Oracle Cloud Infrastructure.&nbsp; OCI is highly secure, and available in a public, hybrid, or private cloud configuration.&nbsp; Oracle 23ai is autonomous and serverless, meaning that it does not require special care or the constant attention of DBAs.

&nbsp;

Since the OCI account is the customer's account and is never shared with Hackolade, there is no concern of confidentiality or security.

&nbsp;

### Is it possible to run the Hub on other databases than Oracle?&nbsp; For example: Couchbase, ElasticSearch, MongoDB, PostgreSQL, or SQL Server?

The technical requirements for the Hub are numerous, ambitious, and strict.&nbsp; A thorough evaluation of all the database vendors was conducted prior to development of the Hub. &nbsp;

&nbsp;

No offense to the excellent vendors (which we support in many ways), but only Oracle 23ai Autonomous JSON running on OCI checked all the boxes of our requirements.&nbsp; No other vendor provided all the pieces of the puzzle to achieve our vision and architecture, while satisfying the security-first architecture constraints. &nbsp;

&nbsp;

To be transparent, this was not an easy choice, given perceptions in the market.&nbsp; It also encountered internal resistance.&nbsp; At first...&nbsp;

&nbsp;

We suggest to every customer to evaluate, with an open mind, the benefits of the latest Oracle 23ai Autonomous JSON database on OCI.&nbsp; The experience and pricing are quite different than running older versions on-premises.

&nbsp;

All that is required is an OCI account, and follow our installation instructions in this page (link TBA), and you are up and running in minutes.

&nbsp;

### Are there concerns of version compatibility between the Studio and the Hub?

No.&nbsp; Hackolade Studio has ensured backward-and forward compatibility since v1.&nbsp; Our persistence of models in JSON files ensures that a user with an older version of the software can open a model saved with a more recent version of the software.&nbsp; And vice-versa.&nbsp; The same is true for the Hub.&nbsp; The models are stored in a document database in their original JSON format.&nbsp; It does not matter with which version each model was saved, it is ingested as-is in the database, and indexed according to its content so it is easily browsable and searchable in the Hub.

&nbsp;

### What is the update process of the Hub browser application?

No action is necessary by users.&nbsp; As Hackolade releases enhancements to the Hub software, they are immediately deployed worldwide to the edge of the Azure Content Delivery Network (Azure Front Door.)&nbsp; Each time the user opens a tab for the Hub, the latest version is downloaded to the user's browser.&nbsp; If the user kept the tab opened with the Hub, it may be required to reload it. &nbsp;

&nbsp;

### Are the Oracle functions and APIs ever updated?

The functions and APIs on your instance on OCI might need to be updated from time to time. The code for these functions is openly available for scrutiny in our repository and packaged in a container.&nbsp; If a new container version is released, the OCI functions will be updated after confirmation by the customer administrator of the Hub.

&nbsp;

## Functional concerns

### Is the Hub database able to handle data models for other targets than RDBMS?

All data models are persisted in JSON format for all targets supported by Hackolade Studio: SQL and NoSQL databases, REST and GraphQL APIs, storage and data exchange formats.&nbsp; In the Hub database, data models are stored as raw JSON documents, leveraging the Oracle 23ai capability to natively handle the JSON format.&nbsp; You may see examples in the demo playground at [https://hub.hackolade.com](<https://hub.hackolade.com> "target=\"\_blank\"")

&nbsp;

### Is it possible to view the ERD for a model or part of it?

This is a function where Hackolade Studio excels.&nbsp; On each screen of the Hub, a button (blue, up top) allows to open the model in Studio (browser or desktop, according to the user preference.)&nbsp; Whether the model opens up in Studio in read-only or editable mode depends on the type of license (viewer or workgroup.) Saving changes depends also on the user's rights on the repo.&nbsp; For changes to be committed and pushed to the repo (then be visible in the Hub), it may be required to create a branch and submit a change request.

&nbsp;

### Can users make changes to models in the Hub database?

Not directly in the Hub, but easily in the Studio.&nbsp; The philosophy and architecture of the Hub is to be model-driven.&nbsp; The Hub is entirely in read-only mode for users.&nbsp; The "master" for your data models is your Git repository.&nbsp; The Hub database is only a replication of the selected repository or repositories.&nbsp; This also means, from a data integrity point of view, that there is zero risk of conflicting information or of destroying the database.&nbsp; The database can be reconstructed at any time based on your repo(s).

&nbsp;

If the user wants to change information in the Hub, the change must be executed in the data model using Studio, then committed/pushed to the repository.&nbsp; This also ensures traceability and history of changes.

&nbsp;

### What if a model changes in the Git repository?

When setting the Hub, the administrator points it to one ore more Git repositories and a single branch, typically main/master but it can also be develop or another one.&nbsp; Any time a model is merged into the main branch, a webhook alerts the Hub to replicate the model in its database.&nbsp; In seconds, the Hub database is updated with the latest version of the data model in that branch.&nbsp; The information is immediately accessible in the Hub.

&nbsp;

### The Hub does not seem to be up-to-date with the latest changes to the repository?

In the unlikely event that the hub database missed a webhook notification from the repository, an administrator can press a button to catch up and replicate the Hub database.

&nbsp;

### Is it possible to view in the Hub an intermediary or in-progress version of a model?

This is done by leveraging a Studio feature: from any branch of commit, you can [share a model link URL](<SharemodellinkURL.md>). Note that this viewing capability is limited to the Studio application.&nbsp; In other words, a model version is not replicated or visible into the Hub until merged in the main/master branch (or the branch selected by the administrator as the source for the Hub.)

&nbsp;

### Is it possible to prevent a model and/or folder of models from being replicated into the Hub?

Yes.&nbsp; If no longer needed, you could of course delete the model from the repo.&nbsp; You may also want to retain a model, but not publish it to the Hub.&nbsp; It is super simple to create a .hubignore text file in the root of the root of repo, listing the model(s) and/or folders. &nbsp;

&nbsp;

### I want to harvest metadata from a new source.&nbsp; Can I do that from the Hub?

Harvesting metadata from a source is an action called [reverse-engineering](<Reverseengineeranexistinginstanc.md>) in Hackolade Studio.&nbsp; The resulting model must be saved and pushed to the repo before it can be seen in the Hub through the automatic replication. Different terms are used, all more or less describing the same process: harvest, extract, discover, crawl, ingest, infer, reverse-engineer...

&nbsp;

**Note** that in Hub terminology, "replication" is the word used to describe the copying of data models into the Hub database, while the word "harvesting" may be used in other products.

### I want to regularly harvest metadata from a source.&nbsp; How should I proceed?

Again, this is a function of Hackolade Studio.&nbsp; With the [Command-Line Interface](<CommandLineInterface.md>) and [orchestration of CLI commands](<IntegratetheCLIwithDevOpsCICDpip.md>), it is possible to reverse-engineer a source based on a schedule or trigger, then compare-and-merge into a model.&nbsp; When that model is committed and pushed to the repo, the automatic replication is triggered, and the model becomes available for viewing in the Hub.

&nbsp;

### Is it possible to view or forward-engineer from the Hub: DDLs, scripts, schemas and other artifacts?

These functions are just one click away, by opening the model in Studio, from any screen of the Hub for any part of the model.

&nbsp;

### Do user-defined properties, configured and used in Studio models, appear in the Hub?

Yes, absolutely.&nbsp; All properties of objects in Hackolade Studio models do appear in the Hub, whether out-of-the-box or custom properties.&nbsp; Out-of-the-box properties include business and technical names.&nbsp; Notifications via badges and/or pop-ups may be part of this feature.

&nbsp;

### Can assets in the Hub be tagged with user-defined tags?

This feature is foreseen but has not yet been developed.&nbsp; It is TBA.

&nbsp;

### Does the Hub include a glossary?

A glossary feature is currently being developed in Studio.&nbsp; As soon as it becomes available in Studio, it will be made visible in the Hub.

&nbsp;

### Is it possible for threaded conversations to take place around any object of a data model?

This feature is foreseen, to facilitate collaboration and conversations around any part of a data model.

&nbsp;

### Does the Hub send user notifications via email?

This is not currently foreseen.

&nbsp;

## Licensing concerns

### Why is it required to have a license key to access the Hub?

Hackolade Studio and the Data Model Hub are well integrated, each adding much value to users.&nbsp; They are complementary, and there is no functionality overlap.&nbsp; While you can use Studio without the Hub, the reverse is not possible.&nbsp; We made it easy to add a Hub option to the Viewer and Workgroup editions of Studio.&nbsp; For authors, only the Workgroup edition can be supplemented with the Hub option.&nbsp; The option is NOT available for the Community, Trial, Personal, or Professional editions.

&nbsp;

In addition to IP address restrictions (cfr below) and the Identity Provider integrations, the license key ensures that only authorized users are allowed to access the Hub.

&nbsp;

### Can I share my license key across the Studio and Hub applications?

Provided that you have the appropriate license - Viewer+Hub or Workgroup+Hub - the same license key is automatically used across both products.&nbsp; If you have validated the license key in either Studio Browser or Hub, you are automatically validated for the other.

&nbsp;

If you have originally validated your license key in the Desktop, a small manipulation is required, due to web browser security.&nbsp; The process is described in detail in [this page](<https://hackolade.com/help/Softwareregistration.html#Reuse%20in%20the%20Browser%20your%20license%20key%20already%20validated%20in%20the%20Desktop> "target=\"\_blank\"").

&nbsp;

### Our license key is concurrent.&nbsp; Will it also work with the Hub?

Yes, concurrent (a.k.a. floating) license keys also function with the Hub.&nbsp; Just remember that tabs of either the Studio or the Hub all count for the reservation of a seat.&nbsp; To release your seat so it can be used by someone else in your organization, you must exit all tabs of both the Hub and Studio.&nbsp; The order in which you close the tabs does not matter.&nbsp; Only the last one being closed releases the seat.

&nbsp;

&nbsp;

## Authentication and authorization concerns

### What profiles or roles are possible?

The Hub is read-only for all users, as per the architecture detailed above.&nbsp; To start, it is necessary to distinguish 2 main roles: an administrator role to perform technical instance actions, and a general access role.

&nbsp;

The administrator role allows one or more designated users to be able to carry technical tasks, as described in this page (link TBA).&nbsp; Other users, whether with a Viewer or Workgroup edition license, have general access to the Hub, provided that they have the proper license key and have been given access by an administrator.

&nbsp;

### Can the Hub integrate with LDAP, Microsoft Entra ID, Okta, or an other Identity Provider?

Currently, the only authentication mechanism is Oracle OCI IAM.&nbsp; The documentation for the integration of SSO is work-in-progress.

&nbsp;

### Does the Hub support Multiple Factor Authentication?

Multi-Factor Authentication (2FA or MFA) functionality is in the scope of the Identity Provider.&nbsp; If enabled there for the IdP integrated with the Hub, then indeed the Hub will support MFA.

&nbsp;

### Can the Hub be configured so it is only accessible from specific IP addresses?

This functionality is foreseen.

&nbsp;

### Is it possible to provide further access granularity?

It is foreseen to allow license key-enforced access control.

&nbsp;

&nbsp;

## Reporting

TBA
