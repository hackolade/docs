# Versioning

In the advanced [Compare and Merge Models](<Compareandmergemodels.md>) feature, the application offers a side-by-side comparison of 2 models, with the ability to resolve and merge differences. This feature can be used in several use cases described below.

&nbsp;

Some users may have thought that Hackolade did not include a built-in versioning mechanism.&nbsp; But we think that our approach of leveraging [Git](<https://en.wikipedia.org/wiki/Git> "target=\"\_blank\"") is actually much more powerful and flexible, without re-inventing the wheel.&nbsp; The concepts and technology of Git are not only mature, but are very much applicable to the lifecycle of data models as well as to distributed collaboration on their evolution.

&nbsp;

## Model lifecycle

It is often the case, in particular in an Agile environment, that models diverge in multiple parallel paths before they have to converge.&nbsp; The old approach of check-out/check-in of a data model, to lock it from being modified by others while we're making changes, is not flexible enough for today's non-linear application schema evolution or for the fast pace of agile sprints.

&nbsp;

While still quite simple, a scenario like the one shown below represents a common situation.&nbsp; After version 1.0 has been released, a team is preparing the evolution towards version 2.0.&nbsp; But in the meantime, version 1.0 requires several adjustments to fix minor issues.

&nbsp;

By the time we want to promote version 2.0 to production, we want to make sure not to lose the minor fixes to version 1.x.&nbsp;

&nbsp;

![Image](<lib/Versioning%20-%20model%20lifecycle.png>)

&nbsp;

This kind of situation is common in code development, and has been successfully resolved at scale thanks to Git, as an alternative to more traditional source code control solutions, in order to support non-linear programming in a distributed environment.&nbsp; And the simple example above can quickly evolve into a much more complex situation, with multiple branches and sub-branches.&nbsp; Yet Git helps keep it under control.

&nbsp;

It was a design choice from the very beginning for the architecture of Hackolale to persist data models in JSON documents, not only so they could be stored in NoSQL document database repositories, but also so we could leverage Git for versioning and collaboration.

&nbsp;

With our feature Compare and Merge Models, we want to facilitate merging 2 data models and help resolve potential conflicts.&nbsp; For the example above, it means facilitating merging v1.2 and v2.0 beta+ into a v2.0 Release Candidate, prior to safely promoting v2.0 to production without risk of regressions.

&nbsp;

![Image](<lib/Versioning%20Model%20lifecycle%20merge.png>)

&nbsp;

Learn how how to handle resolution in the page [Compare and Merge Models](<Compareandmergemodels.md>).

&nbsp;

## Validating schemas in production

Another typical use case in enterprises is to make sure that the Data Governance department has an accurate view of the schemas used in production databases.&nbsp; This is particularly relevant in the context of schemaless NoSQL when there is no DDL in source code control.&nbsp; The process of auditing a production database may become a nightly process (automated with our [Command-Line Interface](<CommandLineInterface.md>)) to reveal structures being used without prior validation.

&nbsp;

In the example below for an existing production database instance (in yellow), Hackolade is used to infer the schema to create version 1.0 of the data model.&nbsp; The model is enriched with descriptions and constraints to generate documentation.&nbsp; In the meantime, the schema in the production database has evolved again with the delivery of new agile sprints.&nbsp; And at the same time a new feature development initiative is taking place to make the data model evolve.&nbsp;

&nbsp;

![Image](<lib/Versioning%20-%20validating%20schemas%20in%20production.png>)

&nbsp;

A couple of successive merge operations become necessary.&nbsp; First, the reverse-engineering of the production database into a new model to be merged with model v1.1 into v1.2:

![Image](<lib/Versioning%20-%20validating%20schemas%20-%20step%201.png>)

&nbsp;

Followed by the the merging of the resulting v1.2 with 2.0 beta into v2.0 release Candidate:

&nbsp;

![Image](<lib/Versioning%20-%20validating%20schemas%20step%202.png>)

&nbsp;

**Note:** the model compare feature assumes 2 model files saved on the file system.  Hence the process requires a prior step to reverse-engineer and save the result.  Then compare with a baseline.  Note also that when comparing, because models are of different sources which by definition will have different object IDs, it is required to compare based on object names.  This may require some preperation of the models so objects are comparable, e.g. identical container names and entity names.

&nbsp;

Learn how how to handle the successive merge operations and the resolution of merge conflicts in the page [Compare and Merge Models](<Compareandmergemodels.md>).

&nbsp;

&nbsp;

## Model-driven API generation

When you use the Hackolade feature to [generate Swagger/OpenAPI documentation](<APIModel.md>) based on an underlying data model, you may have to adjust many details of the API model, including metadata or requests/responses that were not initially foreseen in the template used to generate the API model. &nbsp; So, when entities and attributes in the underlying data model evolve and you want to generate a new version of the API model, you want to be able to easily merge the changes in both tracks.

&nbsp;

![Image](<lib/Versioning%20-%20APIs.png>)

&nbsp;

&nbsp;

The original API model 1.0 was generated automatically from the combination of the underlying data model and the API creation template.&nbsp; The API model evolves into v1.1 with the addition of metadata and other functional adjustments.&nbsp; When the schema evolves in the underlying data model, ti becomes necessary to merge the 2 branches.

![Image](<lib/Versioning%20-%20APIs%20merging.png>)

&nbsp;

&nbsp;

Learn how how to handle the merge operation and the resolution of merge conflicts in the page [Compare and Merge Models](<Compareandmergemodels.md>).

&nbsp;

