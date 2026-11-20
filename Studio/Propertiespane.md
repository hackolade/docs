---
description: The Hackolade Studio Properties pane shows the properties and constraints of the selected object, and marks values that do not satisfy the target's rules.
seoTitle: Properties pane in Hackolade Studio
image: lib/Properties pane controls - large text dialog.png
---
# Properties pane

The right-hand pane displays the properties for any entity you select in the object browser or central pane. This is where you maintain the characteristics and constraints of each selected object.

You may adjust the width of the pane by moving the vertical ellipse ![Central pane - ellipse hovered](<lib/Central pane - ellipse hovered.png>)separating the central and properties panes. You may toggle the appearance of the Properties pane by choosing the menu option View > Properties pane.

The relevant properties pane is displayed depending on the context being worked on, for example:

Database users properties:\
![Properties pane - users tab](<lib/Properties pane - users tab.png>)

Collection details properties:\
![Properties pane - collection details tab](<lib/Properties pane - collection details tab.png>)

Attribute details properties:\
![Properties pane - field details](<lib/Properties pane - field details.png>)

A set of tabs appears at the bottom of the properties pane. The bottom tabs are fixed but differ depending on the selected entity.

It is possible to toggle the appearance of the Properties pane from the workspace by choosing the menu View > Properties Pane.

The properties pane is made of ... properties. They are the characteristics and constraints of a selected attribute. Depending on the property, you may find different controls, as detailed below.

With v4.2, Hackolade has introduced the capability to control the activation of objects (containers, entities, and attributes), ON by default. If unchecked, forward-engineered objects are commented (if the target script syntax allows it) or filtered.

## Collapse/Expand

The properties pane may contains multiple elements, in which case, you can expand the list or collapse it using the\
![Properties pane controls - plus and minus](<lib/Properties pane controls - plus and minus.png>)\
signs.

## Text box

A typical property is a text box to record a name or a description. It accepts alpha-numeric characters.\
![Properties pane controls - text box](<lib/Properties pane controls - text box.png>)

## Ellipse to dialog box

When a longer text is typically needed for a property, an ellipse at the end of the text box\
![Properties pane controls - text box ellipse](<lib/Properties pane controls - text box ellipse.png>) indicates that a bigger dialog box can be accessed:

![Properties pane controls - large text dialog](<lib/Properties pane controls - large text dialog.png>)

The ellipse is also used to pop-up a relationship field picker:\
![Properies pane controls - field picker](<lib/Properies pane controls - field picker.png>)

## Checkbox

When a property is boolean, it is represented with a checkbox:\
![Properties pane controls - checkbox](<lib/Properties pane controls - checkbox.png>)

## Dropdown list

When a limited list of possible entries is provided, it is in the form of a dropdown list:\
![Properties pane controls - dropdown list](<lib/Properties pane controls - dropdown list.png>)

## Add/Remove

When it is provided, you can add an entry by pressing the plus sign:\
![Properties pane controls - add entry](<lib/Properties pane controls - add entry.png>)

To delete the entry, click on the X to the right of the text box:\
![Properties pane controls - delete entry](<lib/Properties pane controls - delete entry.png>)

## Validation of property values

Hackolade Studio pro-actively checks in real-time the values that you enter in the Properties Pane against the rules of the target of the data model, such as the uniqueness of objects names within their respective level, such as the naming rules of the database, and against the other properties of the same object. An invalid value is marked in the Properties Pane, in the Object Browser and in the diagrams, so that you can correct it before you generate scripts or share the model.

An invalid value is kept in the data model. You can still save the model and generate scripts, and it is up to you to correct the value.

### Rules that are checked

The rules depend on the target of the data model and on the property, and the plugin of each target defines its own rules. The main checks are the following:

- Uniqueness: objects at the same level that have the same name are marked. For example, two attributes of the same entity that have the same name or the same technical name are both marked, and so are two entities of the same container.
- The business name and the technical name of an object are checked against the naming rules of the target, such as the characters allowed and the maximum length, and against the list of reserved words of the target. For example, in a DynamoDB model, the name of an attribute cannot be one of the reserved words of DynamoDB.
- The sample value and the default value of an attribute are checked against its data type and its constraints, such as the pattern, the format, the minimum and maximum length, the minimum and maximum values, and the "multiple of" value. For example, a default value of 150 is marked when the maximum of the attribute is 100.
- Each value of an enumeration, and each value of the examples of an attribute, is checked in the same way as the sample value.
- Constraints that contradict each other are marked, for example a minimum length that is greater than the maximum length, or a minimum value that is greater than the maximum value.
- The value of the pattern property must be a valid regular expression.
- A property marked as required must have a value. This applies to the properties of the target, and to the [user-defined custom properties](Userdefinedcustomproperties.md) that have a `validation` keyword, as described in [Property controls](<https://hackolade.com/help/Propertycontrols.html#validation>).
- Some properties of a target have their own checks, for example the options of indexes in a MongoDB model, or the read and write capacity of a DynamoDB table.

### How invalid values are shown

- In the Properties Pane, a red exclamation mark in a circle is displayed next to the label of the property. Hover over the mark to read the message, for example "Incorrect default. Check min and max fields".
- In the Object Browser, an exclamation mark in a circle is displayed next to the name of the object, with the tooltip "Has error".
- In the ER diagram, the same mark is displayed on the container, on the header of the entity box, on the attribute row or on the relationship. The name of an invalid attribute is displayed in red in the entity box and in the hierarchical schema view.

To find the invalid values of a model, look for the exclamation marks in the Object Browser, then select each marked object to see its invalid properties in the Properties Pane.

### When the checks are made

The value of a property is checked when you change it in the Properties Pane. When you select an object in the Object Browser or in a diagram, all the properties of this object are checked again.

The results of the checks are saved with the model. When you open a data model, the marks that are displayed are the results that were saved previously, and an object is checked again only when you select it. The saved results can be out of date, for example when the model was saved with an earlier version of Hackolade Studio or of the plugin of the target, whose rules were different. To update the marks of all the objects at once, validate the open model as described below.

### Validate the open model

To check all the objects of the model that is open:

1. In the menu bar, choose **Tools > Options**, and select the **General** tab.
2. Click **Validate opened model now**.
3. Click **OK** to close the Options dialog.

The marks in the Object Browser, in the diagrams and in the Properties pane are updated for all the objects of the model. The **Validate opened model now** button is available only when a model is open.

### Validate each model when it is opened

> [!NOTE]
> Be conscious of the fact that this option, if enabled, has a performance impact, as the validation would check the entire data model each time you open it.  We suggest that this option should not be enabled by default for a lengthy period.

To check all the objects of each data model when you open it, select **Revalidate rules when opening model** in **Tools > Options > General**. The option applies to all the models that you open, and it is not selected by default. With the option selected, it takes longer to open a large model.

When the checks change the results that were saved with the model, the model is shown as modified after it is opened, so that you can save it with the new results.

### Other checks of a model

The validation of property values checks values against the rules of the target. To check business names against a glossary, and the properties of attributes against the rules of your organization, use [Verify Data Model](VerifyDataModel.md). To derive technical names from business names, see [Naming conventions](Namingconventions.md).

## FAQ about some "obscure" properties

What's the purpose of these properties?

- [id](<http://json-schema.org/draft-04/json-schema-core.html#rfc.section.7.2> "target=\"_blank\""): a JSON Schema keyword used to reduce scope. It can be used by those who wish to apply JSON Schema principles, or to link to internal data dictionaries.
- [additionalProperties](<https://json-schema.org/understanding-json-schema/reference/object#additionalproperties> "target=\"_blank\""): a JSON Schema keyword. A boolean to control whether additional properties are allowed or not.
- [required](<https://tools.ietf.org/html/draft-fge-json-schema-validation-00#section-5.4.3> "target=\"_blank\""): a JSON Schema keyword. An array identifying the schema elements that must be present. A required attribute in Hackolade appears as a solid box in the hierarchical schema view, whereas not-required attributes appear as a dashed box.
- technical name: see [Naming Conventions](Namingconventions.md)
