# Attribute boxes in hierarchical schema view

This page explains how to introduce new attributes and control them in a hierarchical schema view.&nbsp; Typically, these attributes are simple fields, but there are other possibilities, as detailed in the [Attributes](<Attributes.md>) page.&nbsp; Most of the controls below are also available from the ERD view and the Object Browser.

&nbsp;

&#49;. Root

&#50;. Add, Insert or Append &nbsp;

&#51;. Controls

&#52;. Choosing family of attribute, field type, and choice

&nbsp;

### &#49;. Root

When you create a new collection, you get an empty hierarchical schema view with a fixed root:

![Tree view - root](<lib/Tree%20view%20-%20root.png>)

&nbsp;

### &#50;. Add, Insert or Append

In simple terms, the difference between the 3 actions are:

\- Add: introduce a new attribute as a child to the right of the selected attribute&nbsp;

\- Insert: introduce a new attribute before the selected attribute and as a sibling, i.e; at the same level

\- Append: introduce a new attribute at the bottom of the level of the selected attribute

#### &#50;.1 Add Attribute

Not all types of fields are allowed to have attributes.&nbsp; Root is allowed to have only attributes as children, no siblings.&nbsp; Documents are also allowed to have attributes a and arrays are will have array items. &nbsp;

![Tree view - root doc or array box](<lib/Tree%20view%20-%20root%20doc%20or%20array%20box.png>) **plus** ![Contextual menu - Add Attribute selected](<lib/Contextual%20menu%20-%20Add%20Attribute%20selected.png>) **equals** ![Tree view - Child added](<lib/Tree%20view%20-%20Child%20added.png>)

&nbsp;

#### &#50;.2 Insert Attribute

Siblings can be inserted before the selected attribute, at the same level. &nbsp; .

&nbsp;

![Tree view - Child added](<lib/Tree%20view%20-%20Child%20added.png>) **plus** ![Contextual menu - Insert selected](<lib/Contextual%20menu%20-%20Insert%20selected.png>)**equals** ![Tree view - field inserted](<lib/Tree%20view%20-%20field%20inserted.png>)

&nbsp;

#### &#50;.3 Append Attribute

Siblings can be appended at the bottom of the same level.

![Tree view - field inserted](<lib/Tree%20view%20-%20field%20inserted.png>) **plus** ![Contextual menu - Append selected](<lib/Contextual%20menu%20-%20Append%20selected.png>) **equals** ![Tree view - field appended](<lib/Tree%20view%20-%20field%20appended.png>)

&nbsp;

&nbsp;

### &#51;. Controls

When an attribute is selected, the color of the box is changed to turquoise. &nbsp;

#### &#51;.1 Introduce an attribute

There are 4 ways to introduce a new attribute

##### &#51;.1.1 Menu

Choose the appropriate option in the Actions menu:

![Menu - Actions](<lib/Menu%20-%20Actions.png>)

##### &#51;.1.2 Shortcuts

Press the keyboard shortcut of your choice:

| **Shortcut** | **Description** |
| --- | --- |
| Ctrl+A | Add attribute |
| Ctrl+I | Insert field |
| Ctrl+E | Append field |
| Ctrl+X | Cut |
| Ctrl+C | Copy |
| Ctrl+V | Paste |
| Del | Delete |
| Ctrl+D | Duplicate |


##### &#51;.1.3 Toolbar

Choose the appropriate icon in the toolbar:

![Tree view - icons](<lib/Tree%20view%20-%20icons.png>)

with:

&nbsp;

| **Icon** | **Description** |
| --- | --- |
| ![Image](<lib/Icons%20-%20addChild.jpeg>) | Add attribute |
| ![Image](<lib/Icons%20-%20insertField.jpeg>) | Insert field |
| ![Image](<lib/Icons%20-%20appendField.jpeg>) | Append field |
| ![Image](<lib/Icons%20-%20moveUp.jpeg>) | Move up |
| ![Image](<lib/Icons%20-%20moveDown.jpeg>) | Move down |
| ![Image](<lib/Icons%20-%20toggleDetails.jpeg>) | Toggle details in diagram |


&nbsp;

and also:

![Toolbar - Edit section](<lib/Toolbar%20-%20Edit%20section.png>)

with:

&nbsp;

| **Icon** | **Description** |
| --- | --- |
| ![Icons - cut](<lib/Icons%20-%20cut.jpeg>) | Cut |
| ![Icons - copy](<lib/Icons%20-%20copy.jpeg>) | Copy |
| ![Icons - paste](<lib/Icons%20-%20paste.jpeg>) | Paste |
| ![Icons - delete](<lib/Icons%20-%20delete.jpeg>) | Del |
| ![Icons - duplicate](<lib/Icons%20-%20duplicate.jpeg>) | Duplicate |


##### &#51;.1.4 Contextual menu

Right-click on an existing item to display a contextual menu:

![Tree view - contextual menu](<lib/Tree%20view%20-%20contextual%20menu.png>)

Only available options are activated, depending on the item selected when you perform the right-click.&nbsp; To understand the different types of attributes, you may want to read this [page](<Attributes.md>).

#### &#51;.2 Move an attribute

To change the order of the attributes within a level, use the Move Up or Move Down icons in the toolbar.&nbsp; You may also move an attribute with your mouse by selecting the attribute, holding your left mouse button and dragging the box up or down in the same level.

#### &#51;.3 Delete an attribute

There are several ways to delete an attribute.&nbsp; You must first select it, then:

\- choose Delete from the Edit menu

![Menu Edit - Delete selected](<lib/Menu%20Edit%20-%20Delete%20selected.png>)

\-&nbsp; press the Delete key on your keyboard

\- click the button ![Icons - delete](<lib/Icons%20-%20delete.jpeg>)in the toolbar

\- right-click the attribute and choose Delete

![Contextual menu - Delete selected](<lib/Contextual%20menu%20-%20Delete%20selected.png>)

&nbsp;

#### &#51;.4 Duplicate an attribute

When you choose to duplicate an attribute, all the properties of the selected item will be copied to a new attribute as a sibling at the same level, including the relationship.&nbsp; There are several ways to delete an attribute.&nbsp; You must first select it, then:

\- choose Duplicate from the Edit menu

![Contextual menu - Duplicate selected1](<lib/Contextual%20menu%20-%20Duplicate%20selected1.png>)

\- press the shortcut Ctrl+D

\- click the button ![Image](<lib/Icons%20-%20duplicate.jpeg>) in the toolbar

\- right-click the attribute and choose Duplicate

![Contextual menu - Duplicate selected](<lib/Contextual%20menu%20-%20Duplicate%20selected.png>)

&nbsp;

#### &#51;.5 Cut, Copy, and Paste

These control have a behavior similar to what is expected in any desktop application.&nbsp; When performing the operation, all the properties of the selected attribute will be copied to a new attribute as a sibling at the same level, including the relationship.&nbsp;

&nbsp;

#### &#51;.6&nbsp; Collapse/Expand

When an attribute has at least one attribute, its descendance can be collapse or expanded by pressing the - or the + sign to the right of the box:

![Tree view - expanded](<lib/Tree%20view%20-%20expanded.png>)

![Tree view - collapsed](<lib/Tree%20view%20-%20collapsed.png>)

&nbsp;

&nbsp;

#### &#51;.7 Toggle details

You may also toggle the appearance of details by pressing the ![Icons - toggle Details](<lib/Icons%20-%20toggleDetails.jpeg>) button:

![Tree view - no details](<lib/Tree%20view%20-%20no%20details.png>)

&nbsp;

&nbsp;

### &#52;. Choosing family of attribute, field type, and choice

#### &#52;.1 family of attributes

&nbsp;

![Family of Attributes](<lib/Family%20of%20Attributes.png>)

&nbsp;

&nbsp;

For an array:

![Family of Attributes - Array](<lib/Family%20of%20Attributes%20-%20Array.png>)

&nbsp;

For choices:

![Family of Attributes - choices](<lib/Family%20of%20Attributes%20-%20choices.png>)

&nbsp;

#### &#52;.2 Field type

Field types include standard JSON Schema field types, plus the BSON types not already in JSON Schema.&nbsp; BSON is a binary serialization format used to store documents and make remote procedure calls in MongoDB. The BSON specification is located [here](<http://bsonspec.org> "target=\"\_blank\"").&nbsp; BSON supports the following data types as values in documents.

![Tree view - field types](<lib/Tree%20view%20-%20field%20types.png>)

&nbsp;

This list varies depending on the database target.

&nbsp;

&nbsp;

'***4.3 Choice***

You may add choices for alternate sub-schemas:

&nbsp;

![Tree view - choices](<lib/Tree%20view%20-%20choices.png>)

&nbsp;

&nbsp;

#### &#52;.4 Reference definition

You may add references to re-usable objects as explained [here](<Reusableobjectsdefinitions.md>).

![Family of Attributes - Ref Def](<lib/Family%20of%20Attributes%20-%20Ref%20Def.png>)

&nbsp;

#### &#52;.5 DBRef (MongoDB only)

Hackolade supports this MongoDB [convention](<https://docs.mongodb.com/manual/reference/database-references/> "target=\"\_blank\"").&nbsp; &nbsp;

&nbsp;

![Family of Atributes - DBRref](<lib/Family%20of%20Atributes%20-%20DBRref.png>)

&nbsp;

#### &#52;.6 Pick from list

If you want to re-use a previously created attribute (without making it a re-usable reference definition), then you can copy its properties with this option:

&nbsp;

![Family of Attributes - Pick from List](<lib/Family%20of%20Attributes%20-%20Pick%20from%20List.png>)

&nbsp;

&nbsp;

&nbsp;

There are several ways to create a new field.&nbsp; Depending on which attribute you select, you will want to add the new attribute as an attribute, or as a sibling.

&nbsp;

and to Append:

&nbsp;

For each of the 3 methods (Add attribute, Insert, and Append), there are 4 ways to do so:

\- from the menu, choose Actions \>&nbsp; then Add attribute, Insert field or Append field

\- press the shortcut Ctrl+H (Add attribute), Ctrl+E (Insert field), or Ctrl+D (Append field)&nbsp;

\- from the toolbar, choose the 'add attribute' button ![Image](<lib/Icons%20-%20addChild.jpeg>)

\- inside the central pane, Schema tab, right-click on the box for which you want to create a child attribute, and choose Add Attribute

![Contextual menu - attributes](<lib/Contextual%20menu%20-%20attributes.png>)

