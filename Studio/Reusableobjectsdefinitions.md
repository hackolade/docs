# Re-usable objects definitions

**Note:** You may wish to view the [how-to video](<https://hackolade.com/videos.html#def> "target=\"\_blank\"") on this subject.

&nbsp;

To facilitate the work of data modelers, Hackolade has introduced a handy feature: the ability to create once object definitions that can be re-used in multiple places.&nbsp; A library of definitions standardizes content and insures consistency.&nbsp; This dictionary also simplifies the work of data modelers so maintenance can be performed in one place and be automatically propagated to all places where the definition is referenced.

&nbsp;

A good simple example of a re-usable definition is an address.&nbsp; This type of object may be used in many places inside a model, and in different models too.&nbsp; Even within one single entity, you may have, for example a billing address and a shipping address.

&nbsp;

Definitions can be maintained at 3 distinct levels: at the entity-level (called internal definitions), at the model-level, and external.&nbsp; Internal definitions have limited use because they can only be reused (or referenced) within the same entity (a collection or table). But internal definitions insure [JSON Schema compatibility](<https://cswr.github.io/JsonSchema/spec/definitions\_references/> "target=\"\_blank\"").&nbsp; Model definitions can be referenced in any entity of the same Hackolade model.&nbsp; Finally, external definitions are Hackolade models (or JSON Schema files) that can be referenced in whole or in part, by other models. In the ERD view and hierarchical schema view, the references are are noted:

\- (i) for internal

\- (m) for model

\- (e) for external

&nbsp;

**Note:** any entity (collection, table, ...) - or attribute herein - within a Hackolade can be an *external* definition for, and be referenced by, another Hackolade model.&nbsp; In other words, it does not have to be a definition within that model.

&nbsp;

**Note:** external model can be used to create a company-wide library of re-usable objects.&nbsp; You may ask yourself whether it is best to have one single model hold all of your company's re-usable definitions, or to have one model per object, or various degrees in-between.&nbsp; There are pros and cons to each approach. &nbsp; We would advise against putting all objects in a single model.  One model per domain, or even one model per sub-domain would make more sense from these perspectives:

\- maintenance responsibilities (maybe a department does not want its definitions be altered by another department)

\- ease of navigation (directory names and model names should be descriptive so modelers don't have to scan tons of objects to find the ones that they're interested in)

\- performance (not a huge factor, but smaller models are easier to navigate than bigger ones.)

Depending on size, you may even use sub-directories to help manage the library of definition models.  But do remember that, if you move referenced models around, you will break the path in the referencing models.

&nbsp;

**Note:** In order for changes to a *referenced* external model to be activated in a *referencing* model, the latter needs to be opened in the application.&nbsp; &nbsp;

&nbsp;

If a definition is created at the model level, it can be referenced in any entity of the same model, whereas it will be limited to its own entity if it is created internally.&nbsp; It is easy to create a re-usable definition from scratch, then reference it in a collection.&nbsp; Or by selecting an attribute in an existing collection, and converting it to a re-usable definition, so it can be referenced elsewhere.

&nbsp;

**Note:** Definitions are not carried over to the NoSQL database.&nbsp; They are only used in physical modeling in Hackolade.&nbsp; To make things easy for the data modeler, Object Browser, ERD, entity hierarchical schema views, and documentation all show the referenced attributes as if they had been defined directly in the collection(s).

&nbsp;

When displaying the JSON Schema preview or forward-engineering JSON Schema, the user may choose between the standard 'Referenced definitions'

![Image](<lib/JSON%20Schema%20preview%20Referenced%20definitions.png>) &nbsp;

&nbsp;

![Image](<lib/JSON%20Schema%20FE%20Referenced%20definitions.png>)

&nbsp;

&nbsp;

or 'Resolved definitions'

![Image](<lib/JSON%20Schema%20preview%20Resolved%20definitions.png>)

&nbsp;

![Image](<lib/JSON%20Schema%20FE%20Resolved%20definitions.png>)

&nbsp;

A good example of a useful re-usable object is an address.&nbsp; You may want to have a 'billing address' and a 'shipping address', both of which use the same structure.

&nbsp;

## &#49;) Reference to another Hackolade model or a JSON Schema file

If you have defined a separate model with the structure of an address, you may reference it in any other Hackolade model:

![Image](<lib/Definitions%20-%20contextual%20menu%20referencing%20ext.png>)

&nbsp;

next, you're prompted to choose the reference model, either from your file system or a URL:

&nbsp;

![Image](<lib/Defintions%20-%20Choose%20external%20dialog.png>)

&nbsp;

You then can choose an individual attribute, or an entire structure:

![Image](<lib/Definitions%20external%20choose.png>)

&nbsp;

&nbsp;

&nbsp;

**Note:** it is not intended to combine definition levels.&nbsp; In other words, if you have a Hackolade model with attribute structures intended to be re-used in other models, you should define these as simple attributes, not as internal or model definitions.

&nbsp;

External references are produced using the $ref implementation described [here](<https://swagger.io/docs/specification/using-ref/> "target=\"\_blank\"") and [RFC 3986](<https://tools.ietf.org/html/rfc3986> "target=\"\_blank\"").

&nbsp;

## &#50;) Initially create a definition

A definition can be created from scratch, just like any collection, either by selecting the Model Definitions lower tab at the model ERD level:

![Image](<lib/Definitions%20-%20Lower%20model%20tabs.png>)

&nbsp;

or by selecting the Internal Definitions lower tab at the collection level:

&nbsp;

![Image](<lib/Definitions%20-%20Lower%20collection%20tabs.png>)

&nbsp;

In our address example, the definition may look like this:

![Image](<lib/Definitions%20-%20Address%20example.png>)

&nbsp;

Once the definition is created, it can be referenced in a collection, via the contextual menu:

&nbsp;

![Image](<lib/Definitions%20-%20Contextual%20menu.png>)

As a result, a reference is created in the collection.&nbsp; The application displays all the elements of the definition, as if they were in the collection, but only a reference to the definition is actually stored in the collection:

&nbsp;

![Image](<lib/Definitions%20-%20billing%20and%20shipping%20references.png>)

The reference is marked with the middle line in the hierarchical schema box, showing the name of the referenced definition, followed by either (m) for model definitions, or (i) for internal definitions.

&nbsp;

At any point, it is possible, if desired, to replace a reference by the object definition structure:&nbsp;

![Image](<lib/Definitions%20-%20replace%20by%20attributes.png>)

&nbsp;

## &#51;) Convert an existing attribute into a definition

If you want to make an attribute available for use elsewhere in the same collection, or in another collection, you can convert it with just a few clicks:

![Image](<lib/Definitions%20-%20convert%20reference%20to%20def.png>)

This will create the internal or model definition, and replace the attribute (and its children if any) by a reference to the definition.

&nbsp;

## &#52;) Where-Used

For internal and model definitions, it may be useful to find all occurrences of definition references within a model.&nbsp; This where-used function (aka impact analysis, aka lineage) is available from the contextual menu (or the Ctrl+F11 shortcut key):

![Image](<lib/Definition%20Where-Used%20contextual%20menu.png>)

&nbsp;

&nbsp;

Choosing this option displays a dialog displaying all instances of references to the selected definition, and the path to those instances.

&nbsp;

![Image](<lib/Definition%20where-used%20dialog.png>)

You may select an instance and go to the hierarchical schema view of that reference. &nbsp; Lineage is enabled from the Object Browser and definition tab (model and internal.)&nbsp;

