# Create a new model from scratch

Dynamically generate forward-engineering scripts and documentation with just a few mouse clicks.

&nbsp;

When starting a new project, the database model is at the core of your application. With Hackolade, you can get started in no time! With just a few mouse clicks, you can generate sample documents, an Oracle table or MongoDB collection or DynamoDB table creation scripts, and HTML or PDF documentation. In an Agile approach, you can engage in a meaningful dialog between analysts, designers, architects, developers and DBAs, playing what-if scenarios. It increases your chances to deliver an evolving application that responds to your customer's needs.

&nbsp;

While a real-life model creation process will not be as linear as the flow below, the list below provides a useful checklist:

1. Create a new model
2. Fill in model properties
3. Create a collection
4. Fill in collection properties
5. Create a collection attribute
6. Fill in attribute properties
7. Iterate steps 5 and 6 to create all attributes in collection
8. Iterate steps 3 through 6 to create all collections in the database
9. Create relationships between collection fields
10. Save the model

&nbsp;

## 1. Create a new model

There are 4 ways to create a new model:

- from the Welcome Screen, choose the New model option:

&nbsp;

![Create new model](<lib/Create new model.png>)

- or click File > New Model
- or press the shortcut Ctrl+N
- of click on the New model icon ![Icons - new Model](<lib/Icons - newModel.jpeg>) in the Toolbar

&nbsp;

## 2. Fill in model properties

You start by filling the name for your new model, and the rest of the relevant information in the details tab of properties pane.\
![Creat new model properties](<lib/Creat new model properties.png>)\
At this stage, you may ignore the Relationships tab, and come back to it later.

&nbsp;

## 3. Create an entity/table/collection

There are 5 ways to create a new collection:

- from the menu, choose Actions > Add Collection
- press the shortcut Ctrl+L
- from the toolbar, choose the 'add collection' button ![Icons - add Collection](<lib/Icons - addCollection.jpeg>)
- inside the central pane, Diagram tab, right-click where you want the collection box to appear, and choose Add Collection

&nbsp;

![Contextual menu - Add collection](<lib/Contextual menu - Add collection.png>)

- from the Diagram Objects pane on the left:

&nbsp;

![Diagram Objects pane](<lib/Diagram Objects panel.png>)

&nbsp;

For more details, you may consult the [Collection boxes in ER diagram](EntityboxesinERdiagram.md) page.

&nbsp;

## 4. Fill in collection properties

You start by filling the name for your new collection, and the rest of the relevant information in the details tab of properties pane:\
![Properties pane - Collection](<lib/Properties pane - Collection.png>)\
The fields Capped (and related Size and Max) plus the Validation level and action flags are used in Forward-Engineering for the generation of the MongoDB script.

&nbsp;

## 5. Create a collection attribute

Before you add an attribute, you need to decide where it needs to be added. For the first one, it's simple: it needs to be an attribute of the tree root.

&nbsp;

Make sure to review the page [Attribute boxes in hierarchical schema view](Attributeboxesinhierarchicalsche.md) if you have any question on how to add an attribute. For example, you can add an objectId field, by right-clicking on the root box, and choosing in the cascading contextual menu as displayed below:\
![Create collection attributes](<lib/Create collection attributes.png>)

&nbsp;

## 6. Fill in attribute properties

For example:\
![Properties pane - field details0](<lib/Properties pane - field details0.png>) or\
![Properties pane - field details1](<lib/Properties pane - field details1.png>)

&nbsp;

## 7. Iterate steps 5 and 6 to create all attributes in collection

## 8. Iterate steps 3 through 6 to create all collections in the database

## 9. Create relationships between collection fields

![ER Diagram - contextual menu - add relationsh](<lib/ER Diagram - contextual menu - add relationsh.png>)\
For more details, you may consult the [Relationship links in ER diagram](RelationshiplinesinERdiagram.md) page.

&nbsp;

## 10. Save the model
