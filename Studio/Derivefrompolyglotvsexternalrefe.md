# Derive from polyglot vs external reference

Hackolade Studio is built on an architecture that allows a modular approach of reusable models and parts of models.&nbsp; This in support of breaking down giant monolithic models which are hard to understand and maintain, into more manageable models, potentially with separate lifecycles.&nbsp; This approach is not only more practical and easy to use, but it makes it easier to support data meshes, data products, and our [Domain-Driven Data Modeling](<https://hackolade.com/domain-driven-data-modeling.html> "target=\"\_blank\"").

&nbsp;

Functionally, this modular capability is supported by 2 features, which can be used separately or combined: [deriving from a polyglot](<PolyglotDataModel.md>), and [referencing an external definition](<https://hackolade.com/help/Reusableobjectsdefinitions.html#External%20definitions>).&nbsp; Both methods allow for higher consistency, quality, and governance.&nbsp; Both reuse a structure defined elsewhere.&nbsp; But each has its own behavior, and hence its pros and cons.

&nbsp;

You should experiment with both and determine which one to use for each of your use cases.&nbsp; And remember that it is also possible to combine them...

&nbsp;

**Important note:** remember that in both cases, the technical link between models relies on finding the source according to a path and filename.&nbsp; For this link to remain valid, it is necessary to be stable and portable at the same time.&nbsp; To be portable, you must always define the path as "relative" (as opposed to "absolute") so that, in a folder tree, the source and destination models always remain in the same place, relative to each other, no matter where your repository or folder tree might be stored.&nbsp; And in order to be stable, make sure to not change the model name or the folder name.

&nbsp;

## Derive from Polyglot

When a model is [derived from a polyglot](<PolyglotDataModel.md>), the derived model becomes dependent of the polyglot model. In other words, the properties of derived objects are to be maintained in the "parent" polyglot model, so that they are maintained in a single place, and all the derived models can inherit the properties.&nbsp; While it is also possible to convert a model into a polyglot model, the polyglot becomes the "master", and the derived model the depending model.&nbsp;

&nbsp;

The feature to derive from polyglot, in its most basic form can be used to generate a physical model from a logical model.&nbsp; It also allows you to convert a model from any target to any other target.

&nbsp;

![Polyglot data modeling concept](<lib/Polyglot data modeling concept.png>)

&nbsp;

&nbsp;

In more sophisticated scenarios, you can build a derived model (which itself can be polyglot model, or a physical model) from one or more polyglot models or parts of polyglot models.&nbsp; We try to illustrate this in the abstract picture below, where the derived models at the bottom are each composed of subsets from multiple polyglot models above.

## ![Polyglot multiple subsets](<lib/Polyglot multiple subsets.png>)

&nbsp;

When deriving from a polyglot model, you may of course derive all objects from that polyglot model.&nbsp; You may also individually select just a few entities, which will derive also the relationships between the selected entities. &nbsp;

&nbsp;

After derive, you may create additional entities specific to the derived model, or delete entities previously derived and no longer needed.&nbsp; Within an entity, you may also delete attributes no longer needed, or add new ones that are specific to the derived model.

&nbsp;

However you should limit the changes in the derived model, because it is considered that the "parent" polyglot model is the "master" of the metadata/properties of the derived object &nbsp;

&nbsp;

When refreshing polyglot references, an Impact Analysis screen displays the effects of the changes in the parent polyglot model(s) that would affect the derived model.

&nbsp;

One particular caveat to be aware of is that the source model must be a polyglot model.&nbsp; It cannot be a physical model.

&nbsp;

## Reference External Definitions

With [external references](<https://hackolade.com/help/Reusableobjectsdefinitions.html#External%20definitions>), you may create objects -- entities with their attributes, or individual attributes -- from existing objects existing in any model of any target. &nbsp;

&nbsp;

**Note:** there is no special preparation for an object to be referenced from elsewhere. Any model of any target can be reused elsewhere.

&nbsp;

We try to illustrate this in the abstract picture below, where the models on the right side are each composed of objects from other models, polyglot or physical.

![Image](<lib/Referencing reusable definitions.png>)

&nbsp;

&nbsp;

An illustration of this, although not limited to it, is in the context of dimensional modeling, where you could have common dimensions across the organization: date, time, countries, address, other ISO standardized structures,...&nbsp; You could also have dimensions specific to each domain of the organization.&nbsp; When you need to create a model, then you can assemble it with the exact object of your choice.

&nbsp;

![Referencing reusable definitions dimensional](<lib/Referencing reusable definitions dimensional.png>)

&nbsp;

&nbsp;

The caveat with references to external definitions, is that you cannot "deviate" from the source definition, like it is possible with models derived from polyglot.&nbsp; In other words, if you have an entity referencing another entity in an external model, then you must take all the attributes of that entity: you cannot suppress an attribute, or add a new one for that matter.&nbsp; You can however, do a multiple choice of attributes and create a reference for each.

&nbsp;

## Combining polyglot derive with references to external definitions

We strongly suggest to experiment with both approaches above to understand the behavior plus pros and cons of each.&nbsp; Very likely, each approach fits certain use cases better than others.&nbsp; You must decide which one applies in each case.&nbsp; You may also have a use case that warrants the combination of both approaches.

&nbsp;

