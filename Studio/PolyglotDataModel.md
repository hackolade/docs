# Polyglot Data Model

With version 5.2.0 of Hackolade Studio, users can now define structures once in a technology-agnostic polyglot data model, complete with with denormalization and complex data types, then represent these structures in a variety of physical data models respecting the specific aspects of each target technology.

&nbsp;

You may want to first read about the [background for our polyglot data model approach](<https://hackolade.com/polyglot-data-modeling.html> "target=\"\_blank\""), and as well as the definition of the [polyglot data modeling concept](<PolyglotDataModeling.md>).

&nbsp;

The polyglot and target models are separate models.&nbsp; But they are related to ensure consistency.&nbsp; In other words, the behavior is similar to references to external definitions, but at the model level.&nbsp; The polyglot data model is the master, and targets models are dependent on the polyglot model.&nbsp; If changes are required to an object, they must be done in the polyglot model, then the target models must be updated to reflect the changes.

&nbsp;

Exceptions are possible: some objects in a polyglot model can be flagged as polyglot-only so they do not appear in the target models.&nbsp; Conversely, you can add objects in the target models that are not reflected in the polyglot model.&nbsp; What is important, mostly, is that, if attributes or properties of an object change in the polyglot model, you may update dependent target models to automatically reflect those changes.

&nbsp;

## Push and Pull from the target model

Many customers having accumulated physical data models in Hackolade prior to the introduction of the new functionality will want to convert their target model into a polyglot model.&nbsp; This is done by opening the physical target model, selecting the menu Tools \> Polyglot \> Convert to Polyglot Model...

![Polyglot - convert to](<lib/Polyglot%20-%20convert%20to.png>)

&nbsp;

You may then choose the location where you want to store the polyglot model.&nbsp; You're now ready to maintain and update the polyglot data model.

&nbsp;

You may also create a polyglot data model from scratch and build it, as you would with physical models.&nbsp; Except that a polyglot data model cannot be forward-engineer to a database instance.

&nbsp;

Once you're ready to create a physical data model for a given target, the process is that a new model must be created for the target of your choice.&nbsp; then, from the target model, you derive your physical model from the polyglot data model by selecting the menu Tools \> Polyglot \> Derive from Polyglot Model:

&nbsp;

![Polyglot - derive from](<lib/Polyglot%20-%20derive%20from.png>)

&nbsp;

You may then choose the polyglot data model file:

![Polyglot - choose file](<lib/Polyglot%20-%20choose%20file.png>)

&nbsp;

You are then presented with a dialog where you can narrow down the selection of entities to reference in the target model.&nbsp; By default, all objects are selected.&nbsp; Using multi-select (ctrl-click or shift+click) , you may change the selection of containers, entities, and definitions to derive in the target model.

&nbsp;

![Polyglot - entity selection](<lib/Polyglot%20-%20entity%20selection.png>)

&nbsp;

Attributes of entities cannot be individually deselected. However, each object, including attributes can be marked as "Polyglot only", meaning that they will not be included in any target models.

![Polyglot only property](<lib/Polyglot%20only%20property.png>)

&nbsp;

&nbsp;

## Data type mapping

On the polyglot data model side, a long list of physical data types has been compiled across the different targets support by different Hackolade plugins.&nbsp; It was on purpose that this approach was decided instead of providing only a list of logical data types.&nbsp; That is so the most relevant level of granularity could be chosen at the polyglot level to be automatically mapped to the appropriate physical data type without minimal user intervention.

&nbsp;

A data type matrix mapping table is used to provide bi-directional transformation: when converting a target model to polyglot, and when deriving a target model from polyglot.

&nbsp;

## Naming conventions

Target-specific transformations rules are applied during the process of deriving from the polyglot model.

&nbsp;

## Maintain and update the target model

Once a target model has been created and derived from a polyglot model, it contains all the derived objects.&nbsp; You may not currently edit the attributes of an entity, but you may add new entities and views that are specific to the physical target model, for example based on access patterns. You may also remove entities from the target model.&nbsp; This action does not delete the entity in the polyglot model.

&nbsp;

You may also join entities from multiple polyglot models by repeating the operation to derive from polyglot.

&nbsp;

You may supplement the target model with metadata, index and partitioning information specific to the target technology, then forward-engineer artifacts according to your use case.

&nbsp;

If the polyglot model changes during the time you're editing the target model, you may refresh the derived objects by clicking the update button which can be found in the model-level Properties Pane:

![Polyglot reference property](<lib/Polyglot%20reference%20property.png>)

&nbsp;

If new objects have appeared in the polyglot model (or there are objects in the polyglot model that were not selected in an earlier step), a dialog appears to allow their selection so references could be added to the target model.

&nbsp;

You may also permanently break the connection to the polyglot model.&nbsp; This operation should be done with care of course, as it cannot be re-established afterwards without restarting all the steps from scratch.&nbsp; The operation replaces all references to the objects of the polyglot model by the objects themselves.&nbsp; But further modifications in the polyglot model will no longer have any effect in the target model.

&nbsp;

When opening a target model with a reference to one or mode polyglot models, you are presented with the option to update the objects.

&nbsp;

