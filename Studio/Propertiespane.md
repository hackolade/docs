# Properties pane

The right-hand pane displays the properties for any entity you select in the object browser or central pane.&nbsp; This is where you maintain the characteristics and constraints of each entity.

&nbsp;

You may adjust the width of the pane by moving the vertical ellipse ![Central pane - ellipse hovered](<lib/Central pane - ellipse hovered.png>)separating the central and properties panes.&nbsp; You may toggle the appearance of the Properties pane by choosing the menu option View \> Properties pane.

&nbsp;

The relevant properties pane is displayed depending on the context being worked on, for example:

&nbsp;

Database users properties:

![Properties pane - users tab](<lib/Properties pane - users tab.png>)

&nbsp;

Collection details properties:

![Properties pane - collection details tab](<lib/Properties pane - collection details tab.png>)

&nbsp;

&nbsp;

Attribute details properties:

![Properties pane - field details](<lib/Properties pane - field details.png>)

&nbsp;

A set of tabs appears at the bottom of the properties pane.&nbsp; The bottom tabs are fixed but differ depending on the selected entity.

&nbsp;

It is possible to toggle the appearance of the Properties pane from the workspace by choosing the menu View \> Properties Pane.

&nbsp;

The properties pane is made of ... properties.&nbsp; They are the characteristics and constraints of a selected attribute.&nbsp; Depending on the property, you may find different controls, as detailed below.

&nbsp;

With v4.2, Hackolade has introduced the capability to control the activation of objects (containers, entities, and attributes), ON by default.&nbsp; If unchecked,&nbsp; forward-engineered objects are commented (if the target script syntax allows it) or filtered. &nbsp;

&nbsp;

## Collapse/Expand

The properties pane may contains multiple elements, in which case, you can expand the list or collapse it using the&nbsp;

![Properties pane controls - plus and minus](<lib/Properties pane controls - plus and minus.png>)

signs.

&nbsp;

## Text box

A typical property is a text box to record a name or a description.&nbsp; It accepts alpha-numeric characters.

![Properties pane controls - text box](<lib/Properties pane controls - text box.png>)

&nbsp;

## Ellipse to dialog box

When a longer text is typically needed for a property, an ellipse at the end of the text box&nbsp;

![Properties pane controls - text box ellipse](<lib/Properties pane controls - text box ellipse.png>) indicates that a bigger dialog box can be accessed:

&nbsp;

![Properties pane controls - large text dialog](<lib/Properties pane controls - large text dialog.png>)

&nbsp;

The ellipse is also used to pop-up a relationship field picker:

![Properies pane controls - field picker](<lib/Properies pane controls - field picker.png>)

&nbsp;

## Checkbox

When a property is boolean, it is represented with a checkbox:

![Properties pane controls - checkbox](<lib/Properties pane controls - checkbox.png>)

&nbsp;

## Dropdown list

When a limited list of possible entries is provided, it is in the form of a dropdown list:

![Properties pane controls - dropdown list](<lib/Properties pane controls - dropdown list.png>)

&nbsp;

&nbsp;

## Add/Remove

When it is provided, you can add an entry by pressing the plus sign:

![Properties pane controls - add entry](<lib/Properties pane controls - add entry.png>)

&nbsp;

To delete the entry, click on the X to the right of the text box:

![Properties pane controls - delete entry](<lib/Properties pane controls - delete entry.png>)

&nbsp;

&nbsp;

## FAQ about some "obscure" properties

What's the purpose of these properties?

\- [id](<http://json-schema.org/draft-04/json-schema-core.html#rfc.section.7.2> "target=\"\_blank\""): a JSON Schema keyword used to reduce scope. It can be used by those who wish to apply JSON Schema principles, or&nbsp; to link to internal data dictionaries.

\- [additionalProperties](<http://json-schema.org/latest/json-schema-validation.html#rfc.section.6.5.6> "target=\"\_blank\""): a JSON Schema keyword.&nbsp; A boolean to control whether additional properties are allowed or not.

\- [required](<https://tools.ietf.org/html/draft-fge-json-schema-validation-00#section-5.4.3> "target=\"\_blank\""): a JSON Schema keyword.&nbsp; An array identifying the schema elements that must be present.&nbsp; A required attribute in Hackolade appears as a solid box in the hierarchical schema view, whereas not-required attributes appear as a dashed box.

\- technical name: see [Naming Conventions](<Namingconventions.md>)

