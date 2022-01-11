# Create your first data model

After [installation](<Installation.md>) and [software key validation](<Softwareregistration.md>), you are now ready to run Hackolade Studio and create your first data model.&nbsp; By the end of this tutorial, you will master different ways to enter information in Hackolade Studio, as well as different ways to visualize structures you've created.

&nbsp;

The application starts with a Welcome Page (there's also a slide show overview of the application functionality, but will skip this here):

![Image](<lib/Welcome%20page.png>)

&nbsp;

&nbsp;

## Choose the target for your data model

If you click "New Model", you are presented with a dialog to choose your target:

![Image](<lib/Target%20selection.png>)

&nbsp;

The application is shipped standard with some built-in targets: [Polyglot](<PolyglotDataModel.md>), [JSON](<JSONSchema2.md>), [Couchbase](<Couchbase.md>), [DynamoDB](<DynamoDB.md>), and [MongoDB](<MongoDB.md>).&nbsp; If you wish to create a data model for a different target, you first need to [install the corresponding plugin](<DownloadadditionalDBtargetplugin.md>).&nbsp; Some plugins are available for different versions of the target technology. &nbsp;

&nbsp;

Choose the target of your choice, the target version if appropriate, then click the Create button.&nbsp; For the purpose of this tutorial, we are going to select the JSON Schema specification 2019-09.

&nbsp;

You are presented with a blank workspace.&nbsp; Refer to the [overview of the user interface](<Workspace.md>) for more details.

&nbsp;

## Create your data model

There are 2 main ways to create a data model: you either [build your data model from scratch](<Whatisadatamodel.md>) based on your analysis of requirements, or you can [reverse-engineer](<Reverseengineeranexistinginstanc.md>) from a variety of sources: an existing [instance](<Target-specific1.md>), from [JSON documents](<JSONdocument1.md>) or [JSON Schema](<JSONSchema1.md>), from [SQL DDLs](<SQLDDL.md>), or from [XSDs](<ImportamodelfromXSD.md>).&nbsp; For the purpose of this tutorial, we will start a model from scratch.

&nbsp;

There are many ways to create a data model in Hackolade Studio: using the menu bar, with the toolbar buttons, with keyboard shortcuts, with contextual menus in the ERD pane, or with contextual menus in the Object Browser.

&nbsp;

Let' do a right-click in the middle ERD pane and choose Add document:

![ERD contextual menu](<lib/ERD%20contextual%20menu.png>)

&nbsp;

Then in the Properties pane on the right, let's give a name to this document:

![Image](<lib/Tutorial%20-%20entity%20name%20property.png>)

&nbsp;

We now have our first entity in the ERD:

![Image](<lib/Tutorial%20-%20person%20entity.png>)

&nbsp;

To add our first attribute, we can use right-click again to get the contextual menu and choose the data type String:

![ERD - entity contextual menu](<lib/ERD%20-%20entity%20contextual%20menu.png>)

&nbsp;

We can give it a name:

![Image](<lib/Tutorial%20-%20attribute%20name%20property.png>)

&nbsp;

So it appears in the ERD:

![Image](<lib/Tutorial%20-%20entity%20with%20first%20attribute.png>)

&nbsp;

We can add a new field by clicking the Append Field button in the toolbar:

![Image](<lib/Toolbar%20-%20append%20attribute.png>)

&nbsp;

and give it a name:

![Tutorial - entity with 2 attributes](<lib/Tutorial%20-%20entity%20with%202%20attributes.png>)

&nbsp;

When adding new field DOB, we can see taht a description can be added as well as a format to create a constraint for the field:

![Tutorial - atttribute string properties](<lib/Tutorial%20-%20atttribute%20string%20properties.png>)

&nbsp;

When adding another field, we can see also that we can pick a different data type from the list.&nbsp; This list is specific to each technology target.

![Image](<lib/Tutorial%20-%20atttribute%20data%20types.png>)

&nbsp;

&nbsp;

You may add additional constraints and descriptive properties, default, enumerations, examples, etc...

&nbsp;

You may move the attributes up or down, either using the up and down arrow keys in the toolbar:

![Toolbar field order up-down arrows](<lib/DTD%20field%20order%20arrows.png>)

or by grabbing the handle on the left of the attribute name in the ERD:

![ERD - attribute drag-and-drop](<lib/ERD%20-%20attribute%20drag-and-drop.png>)

&nbsp;

## Hierarchical schema view

In addition to the ERD view, it is possible to have a detailed view of each entity in its own tab, which will be particularly handy in the next tutorial:

![Tutorial - hierarchical schema view](<lib/Tutorial%20-%20hierarchical%20schema%20view.png>)

&nbsp;

We call it the "hierarchical schema view" because it let's you easily create and visualize nested structures.&nbsp; There are many ways to open this view:&nbsp;

\- double click on the entity title\
\- click once on the middle-right icon in the entity title\
\- right-click on the entity title and choose Open in new tab\
\- right-click on the entity name in the Object Browser on the left, and choose Open in new tab, or double-click on the entity name

&nbsp;

![JSON Tree in new tab](<lib/JSON%20Tree%20in%20new%20tab.png>)

&nbsp;

&nbsp;

### JSON Preview

In this upper tab dedicated to a specific entity, there are several lower tabs.&nbsp; The JSON Preview tab provides 2 side-by-side panes: one for the JSON Schema of the entity, and the other tab is for a sample JSON document of the structure:

![Central pane - JSON Preview](<lib/Central%20pane%20-%20JSON%20Preview.png>)

&nbsp;

&nbsp;

Several options are available for the display of the JSON Preview lower tab.&nbsp; You will find all the [details in this page](<Centralpane.md>).

&nbsp;

The sample document generated in the right pane uses dummy values.&nbsp; You may easily make this document more meaningful by entering, for each attribute a sample property (or example, depending on the JSON Schema version), and this value will be used in the JSON Data pane.

&nbsp;

In this tutorial, we reviewed different ways to enter information in Hackolade Studio, as well as different ways to visualize the structure you've created.&nbsp; In the next tutorial, we will see how to create more complex structures.

