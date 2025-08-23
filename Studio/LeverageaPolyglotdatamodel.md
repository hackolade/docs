# Leverage a Polyglot data model

In the previous tutorial, we reviewed how to create a model for REST APIs using Swagger or OpenAPI specification.&nbsp; By the end of this tutorial, you will master how to perform data modeling for polyglot storage and transmission, using our Polyglot Data Modeling capabilities.

&nbsp;

You may also [view this tutorial](<https://youtu.be/Bv0bzJP6CZ0> "target=\"\_blank\"") on YouTube.&nbsp; Summary slides can be found [here](<https://www.slideshare.net/PascalDesmarets1/hackolade-tutorial-part-13-leverage-a-polyglot-data-model> "target=\"\_blank\"").

&nbsp;

A polyglot data model can be viewed as a logical model in the sense that it is technology-independent.&nbsp; And if your physical models will be strictly relational, a polyglot model can be logical, just like you've been used to with traditional legacy data modeling tools.

&nbsp;

But a POlyglot model can be much more than that.&nbsp; It is a common physical model, where denormalization and complex data types are encouraged.&nbsp; While some people like to compare our polyglot model to a logical model because both are technology-agnostic, you should read [this article](<https://hackolade.com/polyglot-data-modeling.html>) where we emphasize the differences.&nbsp; We&nbsp; advise against creating normalized logical models when using the polyglot functionality.&nbsp; You should instead use this functionality to create denormalized models with complex data types and, if needed, rely on the built-in functionality that will automatically normalize nested objects in RDBMS targets.

&nbsp;

With a polyglot data model, you can define data structures once, then easily instantiate them in data models for any of the technologies Hackolade supports:

&nbsp;

&nbsp;

![Polyglot data modeling concept](<lib/Polyglot data modeling concept.png>)

&nbsp;

The polyglot and target models are separate models.&nbsp; But they are related to ensure consistency.&nbsp; In other words, the behavior is similar to references to external definitions, but at the model level.&nbsp; The polyglot data model is the master, while target models are derived, and remain dependent on the polyglot model.&nbsp; If changes are required to an object, they must be done in the polyglot model, then the target models inherit these changes.

&nbsp;

Exceptions are possible, as described further down.

&nbsp;

You may be used to the traditional 3-step process - conceptual-logical-physical - to successively capture scope and language, business rules, and target-specific implementation details. To facilitate the process, we provide, as part of our Polyglot capabilities, a Graph Diagram view of common business language with its entities and their relationships. The graph view is friendlier to business users than Entity-Relationship or UML diagrams.

![Polyglot Cocenptual Graph View](<lib/Polyglot Conceptual Graph View.png>)

&nbsp;

The behavior of this view is similar to that of [graph targets](<Graphshapes.md>)..

&nbsp;

We strongly suggest to avoid using our Polyglot like a traditional logical model.&nbsp; Please don't, as you might be disappointed by the result.&nbsp; It would be the same as wanting to use MongoDB with a normalized data model.

&nbsp;

Again, while our Polyglot model is technology-agnostic like logical models, it is really a **common physical schema** with the following features:

* allows denormalization, if desired, given access patterns;
* allows complex data types;
* generates schemas for a variety of technologies, with automatic mapping to the specific data types of the respective target technologies.

&nbsp;

Typically in logical models, you will have normalized entities, and you may denormalize in the physical model for performance.&nbsp; With a Polyglot model, it is advised to do things the other way around.&nbsp; You should use query-driven access patterns to define Polyglot structures with complex data types, including denormalization and polymorphism.&nbsp; When you derive to an RDBMS target, you will want to let our process normalize the structure, while you will want to keep the hierarchical structure for technology targets that allow it.

&nbsp;

An example is provided [here](<https://hackolade.com/help/PolyglotDataModeling.html#Logical%20modeling>).

&nbsp;

## Create a polyglot data model

A polyglot data model is just another Hackolade data model.&nbsp; You can create entities with attributes and relationships like you would with a specific Hackolade plugin.&nbsp; It has a more generic terminology and a superset of all data types found in the different technology targets.

&nbsp;

To create a new polyglot data model, simply choose Polyglot as your target, and follow the instructions in [this tutorial](<Createyourfirstdatamodel.md>).

![Image](<lib/Target selection polyglot.png>)

&nbsp;

Alternatively, if you have an existing target data model, you can convert it to a polyglot model so the polyglot model becomes the "master" from which other target models can be derived. &nbsp;

&nbsp;

## Derive a target data model

**Important:** from a polyglot model, you cannot directly forward-engineer DDLs, scripts, schemas, etc for technology targets.&nbsp; You must first create a target data model for the technology of your choice, then pull (or derive) from the polyglot model.&nbsp; Then you're able to forward-engineer the artifacts from the target model.

&nbsp;

Once you're ready to create a physical data model for a given technology, the process starts with the creation of a new model for the target of your choice.&nbsp; Then, from the target model, you derive your physical model from the polyglot data model by selecting the menu Tools \> Polyglot \> Derive from Polyglot Model:

&nbsp;

![Polyglot - derive from](<lib/Polyglot - derive from.png>)

&nbsp;

You may then choose the polyglot data model file:

![Polyglot - choose file](<lib/Polyglot - choose file.png>)

&nbsp;

You are then presented with a dialog where you can narrow down the selection of entities to reference in the target model.&nbsp; By default, all objects are selected.&nbsp; Using multi-select (ctrl-click or shift+click) , you may change the selection of containers, entities, and definitions to derive in the target model.

&nbsp;

![Polyglot - entity selection](<lib/Polyglot - entity selection.png>)&nbsp;

Attributes of entities cannot be individually deselected in the above screen. But 2 options are available, depending on the use case:

&#49;) in the polyglot model, each object, including attributes can be marked as "Polyglot only", meaning that they will not be included in any target models.

![Polyglot only property](<lib/Polyglot only property.png>)

&#50;) in a target model you can deselect the IsActivated property, which will cause the attribute to remain in the model, but be filtered out (or commented if the target syntax allows it) in the forward-engineering script.

![Polyglot isActivated property](<lib/Polyglot isActivated property.png>)

&nbsp;

&nbsp;

If your target is a relational database, the process to derive from polyglot will automatically convert complex structures into normalized tables with foreign key relationships.

&nbsp;

## Adjust the target model to the specific needs of the target

You may supplement the target model with metadata, index and partitioning information specific to the target technology, then forward-engineer artifacts according to your use case.

&nbsp;

Once a target model has been created and derived from a polyglot model, it contains all the derived objects.&nbsp; Several adjustments to the target model are possible:

\- changes the properties of entities and attributes without changing them in the polyglot model.&nbsp; This is used if you need minor deviations;

\- add new entities and views that are specific to the physical target model, for example based on access patterns;

\- remove entities from the target model.&nbsp; This action does not delete the entity in the polyglot model.

&nbsp;

You may also join entities from multiple polyglot models by repeating the operation to derive from polyglot.

![Polyglot reference property](<lib/Polyglot reference property.png>)

&nbsp;

## Update target model with changes in polyglot model

When you make changes to a polyglot model and save it, these changes can be reflected in the target models derived from that polyglot model.&nbsp; If the target model is already open, you may refresh the derived objects by clicking the update button which can be found in the model-level Properties Pane:

&nbsp;

An impact analysis dialog is displayed to let you decide which objects to include as part of this refresh operation.&nbsp; Maybe these objects were not selected originally, or they could have been added to the polyglot model since the previous refresh or derive operation, or they could have been deleted in the target model. &nbsp;

&nbsp;

![Polyglot Impact Analysis](<lib/Polyglot Impact Analysis.png>)

&nbsp;

When opening a target model with a reference to one or more polyglot models, you are presented with the option to update the objects. &nbsp;

&nbsp;

You may also permanently break the connection to the polyglot model.&nbsp; This operation should be done with care of course, as it cannot be re-established afterwards without restarting all the steps from scratch.&nbsp; The operation replaces all references to the objects of the polyglot model by the objects themselves.&nbsp; But further modifications in the polyglot model will no longer have any effect in the target model.

&nbsp;

&nbsp;

**Note:** when converting a target model to polyglot, a link is created for the original target model to become dependent on the polyglot. &nbsp;

&nbsp;

**Tip:** if you need to convert a data model from a given technology to another one (example: from MongoDB to Avro, or Parquet, etc.), it is 2-step process: first you convert your original model to polyglot, then you create a new model in the other technology plugin and you derive from the polyglot model.&nbsp; You can optionally break the link with the polyglot model.

&nbsp;

&nbsp;

In this tutorial, we reviewed how to perform data modeling for polyglot storage and transmission, using our Polyglot Data Modeling capabilities.&nbsp; This concludes for now our tutorial series.&nbsp; Next, we will develop a series of How-To Guides, goal-oriented recipes taking you through the steps to solve real-world situations.

