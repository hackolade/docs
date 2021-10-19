# Create a new model from scratch

Dynamically generate forward-engineering scripts and documentation with just a few mouse clicks. &nbsp;

&nbsp;

When starting a new project, the database model is at the core of your application.&nbsp; With Hackolade, you can get started in no time\!&nbsp; With just a few mouse clicks, you can generate sample documents, MongoDB collection or DynamoDB table creation scripts, and HTML or PDF documentation.&nbsp; In an Agile approach, you can engage in a meaningful dialog between analysts, designers, architects, developers and DBAs, playing what-if scenarios.&nbsp; It increases your chances to deliver an evolving application that responds to your customer's needs.

&nbsp;

While a real-life model creation process will not be as linear as the flow below, the list below provides a useful checklist:

1. Create a new model
1. Fill in model properties
1. Create a collection
1. Fill in collection properties
1. Create a collection attribute
1. Fill in attribute properties
1. Iterate steps 5 and 6 to create all attributes in collection
1. Iterate steps 3 through 6 to create all collections in the database
1. Create relationships between collection fields
1. Save the model

&nbsp;

### &#49;. Create a new model

There are 4 ways to create a new model:

\- from the Welcome Screen, choose the New model option:

![Create new model](<lib/Create%20new%20model.png>)

\- or click File \> New Model

\- or press the shortcut Ctrl+N

\- of click on the New model icon ![Icons - new Model](<lib/Icons%20-%20newModel.jpeg>) in the Toolbar

&nbsp;

### &#50;. Fill in model properties

You start by filling the name for your new model, and the rest of the relevant information in the details tab of properties pane.

![Creat new model properties](<lib/Creat%20new%20model%20properties.png>)

At this stage, you may ignore the Relationships tab, and come back to it later.

&nbsp;

You may maintain user credentials at the DB-level in the Users tab of the properties pane:

![Create new model - user credentials](<lib/Create%20new%20model%20-%20user%20credentials.png>)

To add a new user, press the ![Properties pane controls - add entry](<lib/Properties%20pane%20controls%20-%20add%20entry.png>) sign to add a new user and check the appropriate rights.&nbsp; To remove a user, press the X ![Properties pane controls - delete entry](<lib/Properties%20pane%20controls%20-%20delete%20entry.png>) .

&nbsp;

&nbsp;

### &#51;. Create a collection

There are 4 ways to create a new collection:

\- from the menu, choose Actions \> Add Collection

\- press the shortcut Ctrl+L

\- from the toolbar, choose the 'add collection' button ![Icons - add Collection](<lib/Icons%20-%20addCollection.jpeg>)

\- inside the central pane, Diagram tab, right-click where you want the collection box to appear, and choose Add Collection

![Contextual menu - Add collection](<lib/Contextual%20menu%20-%20Add%20collection.png>)

For more details, you may consult the [Collection boxes in ER diagram](<EntityboxesinERdiagram.md>) page.

&nbsp;

### &#52;. Fill in collection properties

You start by filling the name for your new collection, and the rest of the relevant information in the details tab of properties pane:

![Properties pane - Collection](<lib/Properties%20pane%20-%20Collection.png>)

The fields Capped (and related Size and Max) plus the Validation level and action flags are used in Forward-Engineering for the generation of the MongoDB script.&nbsp;

&nbsp;

### &#53;. Create a collection attribute

Before you add an attribute, you need to decide where it needs to be added.&nbsp; For the first one, it's simple: it needs to be an attribute of the tree root.

&nbsp;

Make sure to review the page [Attribute boxes in hierarchical schema view](<Attributeboxesinhierarchicalsche.md>) if you have any question on how to add an attribute.&nbsp; For example, you can add an objectId field, by right-clicking on the root box, and choosing in the cascading contextual menu as displayed below:

![Create collection attributes](<lib/Create%20collection%20attributes.png>)

### &#54;. Fill in attribute properties

For example:

![Properties pane - field details0](<lib/Properties%20pane%20-%20field%20details0.png>) or&nbsp;

![Properties pane - field details1](<lib/Properties%20pane%20-%20field%20details1.png>)

### &#55;. Iterate steps 5 and 6 to create all attributes in collection

&nbsp;

### &#56;. Iterate steps 3 through 6 to create all collections in the database

&nbsp;

### &#57;. Create relationships between collection fields

&nbsp;

![ER Diagram - contextual menu - add relationsh](<lib/ER%20Diagram%20-%20contextual%20menu%20-%20add%20relationsh.png>)

For more details, you may consult the [Relationship links in ER diagram](<RelationshiplinksinERdiagram.md>) page.

### &#49;0. Save the model

