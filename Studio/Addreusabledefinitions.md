# Add reusable definitions

The purpose of reusable definitions is to increase productivity/convenience and consistency to achieve higher data quality and governance.&nbsp; It is a handy feature of Hackolade Studio to facilitate the work of data modelers: it provides the ability to create and maintain object definitions that can be re-used in multiple places. 

&nbsp;

A simple example of a re-usable definition is an address, but many other domain concepts are candidates for this feature.&nbsp; A definition object may be used in many places inside a single data model, and in different models too.&nbsp; Definitions are created once, then referenced in many different places.&nbsp; In case the structure or properties of the object evolve, you only need to make the change in one place, and all the places where the object is referenced will evolve accordingly.

&nbsp;

Definitions can be maintained at 3 distinct levels: at the entity-level (called internal definitions), at the model-level, and external.&nbsp; Internal definitions may have limited use because they can only be reused (or referenced) within the same entity (a collection or table). But internal definitions ensure JSON Schema compatibility.  Model definitions, on the other hand, can be referenced in any entity of the same Hackolade data model.  Finally, external definitions are external files (Hackolade data models or JSON Schema) that can be referenced, in whole or in part, by any other Hackolade Studio data models.

&nbsp;

In the ERD view and hierarchical schema view, the references are are noted:

\- (i) for internal

\- (m) for model

\- (e) for external

&nbsp;

**Note:** in some targets such as RDBMS, "model definitions" are also known as "user-defined types" or UDTs.&nbsp; In Swagger, they are called "definitions" while in OpenAPI, they're called "components".&nbsp; Their behaviors throughout the application are identical.

&nbsp;

There are 2 simple ways to create a definition.&nbsp; Either it is created ahead of time, then referenced in different places.&nbsp; Or it is created from an existing instance of an object.&nbsp; Let's illustrate the second method. &nbsp;

&nbsp;

## Convert an object into a model definition

Let's create a simple JSON document structure with a sub-object for the address. &nbsp;

![How-to definitions address object](<lib/How-to%20definitions%20address%20object.png>)

&nbsp;

Let’s convert this object into a model definition by doing a right-click on the “address” object.&nbsp; In the contextual menu, choose Reference \> Convert to Definition \> Model. &nbsp; This action is not available through the menus or the toolbar.&nbsp; It is only possible via the contextual menus, in the Object Browser, the ERD or the hierarchical schema tree view of each entity tab.

![How-to definitions convert to model def](<lib/How-to%20definitions%20convert%20to%20model%20def.png>)

&nbsp;

Two things happened:

&#49;) in the ERD and also in the schema tree view, the attribute is replaced by a reference to the definition:

![How-to definitions schema view of reference](<lib/How-to%20definitions%20schema%20view%20of%20reference.png>)

&nbsp;

&#50;) and in the Model Definitions tab, there is now a definition.:

![How-to definitions model def tab](<lib/How-to%20definitions%20model%20def%20tab.png>)

&nbsp;

This is where definitions can be maintained.&nbsp; Any change made here is automatically reflected in all places referencing this definition.&nbsp; It is also possible to maintain many additional definitions here.&nbsp;

&nbsp;

&nbsp;

## Reference an existing definition

This action is not available through the menus or the toolbar.&nbsp; It is only possible via the contextual menus, in the Object Browser, the ERD or the hierarchical schema tree view of each entity tab.

&nbsp;

Right-click on an attribute of the entity where you want to add the reference.&nbsp; In the contextual menu, choose Append Attribute \> Reference \> Model:. &nbsp;

&nbsp;

![How-to definitions reference existing def](<lib/How-to%20definitions%20reference%20existing%20def.png>)

&nbsp;

&nbsp;

In the dialog, search and select the object or attribute of your choice:

![Image](<lib/How-to%20definitions%20add%20ref%20to%20a%20definition.png>)

then click the Apply button.

![How-to definitions mutiple refs](<lib/How-to%20definitions%20mutiple%20refs.png>)

&nbsp;

&nbsp;

## Maintain definitions

Go to the Model Definitions tab change the zip code to a string field, and add a country attribute.

![How-to definitions maintain](<lib/How-to%20definitions%20maintain.png>)

&nbsp;

We can see that the changes in the model definition are immediately reflected wherever referenced:

![How-to definitions maintain applied](<lib/How-to%20definitions%20maintain%20applied.png>)

&nbsp;

**Note:** you may assign to references a different name than in its master definition. You may also enter a reference description to supplement the description in the master definition.

&nbsp;

## JSON Schema preview

To see the JSON Schema representation of the person structure, let's open the entity in a separate tab, and got to the JSON/YAML Preview tab..&nbsp; We can see that the address object does not contain the structure -- it is only a pointer to the model definition, using JSON Schema's $ref syntax.

&nbsp;

![How-to defs JSON Schema preview referenced](<lib/How-to%20defs%20JSON%20Schema%20preview%20referenced.png>)

&nbsp;

There are 2 other interesting settings for definitions: Resolved and Internal:

![How-to defs JSON Schema preview choices](<lib/How-to%20defs%20JSON%20Schema%20preview%20choices.png>)

&nbsp;

If you choose Resolved, the $ref pointer is replaced by the actual structure of the definition:

![How-to defs JSON Schema preview resolved](<lib/How-to%20defs%20JSON%20Schema%20preview%20resolved.png>)

&nbsp;

Whereas, if you choose Internal, the model definition is converted into an internal definition for the entity, according to the JSON Schema standard:

![How-to defs JSON Schema preview internal](<lib/How-to%20defs%20JSON%20Schema%20preview%20internal.png>)

&nbsp;

&nbsp;

## Deviate from a definition

There is sometimes a need for the reference to have different attributes and properties than its "master" definition.&nbsp; But a reference to a definition is just a pointer to its definition.  As a result, it inherits ALL the content of the master definition, including all its attributes and their properties, with no possible deviation.&nbsp; This is NOT a restriction of the software.&nbsp; It is simple logic and is also dictated by the way references to definitions are implemented in general, and in JSON Schema in particular.  

 

There are 2 possible workarounds:\
&#49;) create another definition with a different schema and/or properties to match the new needs;\
&#50;) or disconnect from the original definition through the functionality "Replace by attributes".&nbsp; You can start with a reference to the definition, then break the reference and create your deviation.  Of course, there’s a catch: if the schema or properties of the definition change, these changes will only be reflected where the definition has been referenced, i.e. not in places where you have broken the reference.&nbsp; You cannot eat your cake and eat it too… You cannot break from the master definition, then still expect that, if the definition changes, this attribute will benefit from the changes.

&nbsp;

Right-click on the reference either in the ERD or in the hierarchical schema view, then choose Reference \> Replace by Attributes. 

&nbsp;

![Reference definitions - replace by attributes](<lib/Reference%20definitions%20-%20replace%20by%20attributes.png>)

&nbsp;

&nbsp;

## Display Where-Used

If your definitions are used in multiple places, you may find useful to see where.&nbsp; You can click on a definition in the Object Browser and also in the Model Definitions or Internal definitions tabs, then select Where-Used:

&nbsp;

![How-to definitions where-used menu](<lib/How-to%20definitions%20where-used%20menu.png>)

&nbsp;

A dialog box will let you see the different references to the selected definition.&nbsp; You can select one and click the Go to button, and the Object Browser will take you to that object.

![How-to definitions where-used dialog](<lib/How-to%20definitions%20where-used%20dialog.png>)

&nbsp;

## External definitions

External definitions are external files (any Hackolade data model or JSON Schema, plus SwaggerHub openAPI specs in Swagger/OpenAPI target models) that can be referenced, in whole or in part, by any other Hackolade Studio data models.

&nbsp;

In the contextual menu, choose Append Attribute \> Reference \> External. &nbsp; This action is not available through the menus or the toolbar.&nbsp; It is only possible via the contextual menus, in the Object Browser, the ERD or the hierarchical schema tree view of each entity tab.

&nbsp;

![Image](<lib/How-to%20definitions%20external%20menu.png>)

&nbsp;

&nbsp;

**Important:** when referencing external files, it is important to realize that data model files can sometimes move around and be shared between different users.&nbsp; For example, a library of definitions may be stored in a shared folder, in which case you may want to use an *absolute path* to the file.&nbsp; Whereas if data models and their definitions are in the same repository (even if in different folders of that repo), it would be preferable to use a *relative path* to the definition file.

&nbsp;

References can also be made to files accessible at a URL.

&nbsp;

![How-to definitions external path dialog](<lib/How-to%20definitions%20external%20path%20dialog.png>)

&nbsp;

&nbsp;

&nbsp;

You are then presented with a dialog to choose one or more objects to reference:

![How-to definitions external selection dialog](<lib/How-to%20definitions%20external%20selection%20dialog.png>)

&nbsp;

**Warning:** you should avoid doing recursive external definitions.&nbsp; In other words, don't create from a given data model an external reference to an object in the same model file.&nbsp; Also, you must avoid circular references.

&nbsp;

When you open a data model with references to external files, you are prompted to choose whether to update the definitions or not:

&nbsp;

![How-to definitions external update refs](<lib/How-to%20definitions%20external%20update%20refs.png>)

&nbsp;

While in a model with external references, you may at any time update the path to the external file (ellipsis button), or refresh the references in case the external file changed (refresh button.)

![How-to definitions external ref property](<lib/How-to%20definitions%20external%20ref%20property.png>)

&nbsp;

![How-to definitions external update ref dialog](<lib/How-to%20definitions%20external%20update%20ref%20dialog.png>)

&nbsp;

 

**Important Note:** Definitions are a Hackolade concept that is not necessarily carried over to the target technology, unless specifically supported (such as UDTs for Cassandra, Hive, RDBMS...)&nbsp; If definitions are not supported, they are resolved during the forward-engineering process.&nbsp;

