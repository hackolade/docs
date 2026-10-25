# Attribute boxes in hierarchical schema view

This page explains how to introduce new attributes and control them in a hierarchical schema view. Typically, these attributes are simple fields, but there are other possibilities, as detailed in the [Attributes](Attributes.md) page. Most of the controls below are also available from the ERD view and the Object Browser.

&nbsp;

1\. Root\
2\. Add, Insert or Append\
3\. Controls\
4\. Choosing family of attribute, field type, and choice

&nbsp;

## 1. Root

When you create a new collection, you get an empty hierarchical schema view with a fixed root:\
![Tree view - root](<lib/Tree view - root.png>)

&nbsp;

## 2. Add, Insert or Append

In simple terms, the difference between the 3 actions are:

- Add: introduce a new attribute as a child to the right of the selected attribute
- Insert: introduce a new attribute before the selected attribute and as a sibling, i.e; at the same level
- Append: introduce a new attribute at the bottom of the level of the selected attribute

&nbsp;

### 2.1 Add Attribute

Not all types of fields are allowed to have attributes. Root is allowed to have only attributes as children, no siblings. Documents are also allowed to have attributes a and arrays are will have array items.\
![Tree view - root doc or array box](<lib/Tree view - root doc or array box.png>) **plus** ![Contextual menu - Add Attribute selected](<lib/Contextual menu - Add Attribute selected.png>) **equals** ![Tree view - Child added](<lib/Tree view - Child added.png>)

&nbsp;

### 2.2 Insert Attribute

Siblings can be inserted before the selected attribute, at the same level. .

&nbsp;

![Tree view - Child added](<lib/Tree view - Child added.png>) **plus** ![Contextual menu - Insert selected](<lib/Contextual menu - Insert selected.png>)**equals** ![Tree view - field inserted](<lib/Tree view - field inserted.png>)

&nbsp;

### 2.3 Append Attribute

Siblings can be appended at the bottom of the same level.\
![Tree view - field inserted](<lib/Tree view - field inserted.png>) **plus** ![Contextual menu - Append selected](<lib/Contextual menu - Append selected.png>) **equals** ![Tree view - field appended](<lib/Tree view - field appended.png>)

&nbsp;

## 3. Controls

When an attribute is selected, the color of the box is changed to turquoise.

&nbsp;

### 3.1 Introduce an attribute

There are 4 ways to introduce a new attribute

&nbsp;

#### 3.1.1 Menu

Choose the appropriate option in the Actions menu:\
![Menu - Actions](<lib/Menu - Actions.png>)

&nbsp;

#### 3.1.2 Shortcuts

Press the keyboard shortcut of your choice:

&nbsp;

<table style="width:30%">
<colgroup><col style="width:22%"><col style="width:78%"></colgroup>
<thead>
<tr>
<th>Shortcut</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Ctrl+A</td>
<td>Add attribute</td>
</tr>
<tr>
<td>Ctrl+I</td>
<td>Insert field</td>
</tr>
<tr>
<td>Ctrl+E</td>
<td>Append field</td>
</tr>
<tr>
<td>Ctrl+X</td>
<td>Cut</td>
</tr>
<tr>
<td>Ctrl+C</td>
<td>Copy</td>
</tr>
<tr>
<td>Ctrl+V</td>
<td>Paste</td>
</tr>
<tr>
<td>Del</td>
<td>Delete</td>
</tr>
<tr>
<td>Ctrl+D</td>
<td>Duplicate</td>
</tr>
</tbody>
</table>

&nbsp;

#### 3.1.3 Toolbar

Choose the appropriate icon in the toolbar:\
![Tree view - icons](<lib/Tree view - icons.png>)\
with:

&nbsp;

<table style="width:30%">
<colgroup><col style="width:21%"><col style="width:79%"></colgroup>
<thead>
<tr>
<th>Icon</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><img src="lib/Icons - addChild.jpeg" alt="Icons - addChild"></td>
<td>Add attribute</td>
</tr>
<tr>
<td><img src="lib/Icons - insertField.jpeg" alt="Icons - insertField"></td>
<td>Insert field</td>
</tr>
<tr>
<td><img src="lib/Icons - appendField.jpeg" alt="Icons - appendField"></td>
<td>Append field</td>
</tr>
<tr>
<td><img src="lib/Icons - moveUp.jpeg" alt="Icons - moveUp"></td>
<td>Move up</td>
</tr>
<tr>
<td><img src="lib/Icons - moveDown.jpeg" alt="Icons - moveDown"></td>
<td>Move down</td>
</tr>
<tr>
<td><img src="lib/Icons - toggleDetails.jpeg" alt="Icons - toggleDetails"></td>
<td>Toggle details in diagram</td>
</tr>
</tbody>
</table>

&nbsp;

and also:\
![Toolbar - Edit section](<lib/Toolbar - Edit section.png>)\
with:

&nbsp;

<table style="width:30%">
<colgroup><col style="width:21%"><col style="width:79%"></colgroup>
<thead>
<tr>
<th>Icon</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><img src="lib/Icons - cut.jpeg" alt="Icons - cut"></td>
<td>Cut</td>
</tr>
<tr>
<td><img src="lib/Icons - copy.jpeg" alt="Icons - copy"></td>
<td>Copy</td>
</tr>
<tr>
<td><img src="lib/Icons - paste.jpeg" alt="Icons - paste"></td>
<td>Paste</td>
</tr>
<tr>
<td><img src="lib/Icons - delete.jpeg" alt="Icons - delete"></td>
<td>Del</td>
</tr>
<tr>
<td><img src="lib/Icons - duplicate.jpeg" alt="Icons - duplicate"></td>
<td>Duplicate</td>
</tr>
</tbody>
</table>

&nbsp;

#### 3.1.4 Contextual menu

Right-click on an existing item to display a contextual menu:\
![Tree view - contextual menu](<lib/Tree view - contextual menu.png>)\
Only available options are activated, depending on the item selected when you perform the right-click. To understand the different types of attributes, you may want to read this [page](Attributes.md).

&nbsp;

### 3.2 Move an attribute

To change the order of the attributes within a level, use the Move Up or Move Down icons in the toolbar. You may also move an attribute with your mouse by selecting the attribute, holding your left mouse button and dragging the box up or down in the same level.

&nbsp;

### 3.3 Delete an attribute

There are several ways to delete an attribute. You must first select it, then:

- choose Delete from the Edit menu

&nbsp;

![Menu Edit - Delete selected](<lib/Menu Edit - Delete selected.png>)

- press the Delete key on your keyboard
- click the button ![Icons - delete](<lib/Icons - delete.jpeg>)in the toolbar
- right-click the attribute and choose Delete

&nbsp;

![Contextual menu - Delete selected](<lib/Contextual menu - Delete selected.png>)

&nbsp;

### 3.4 Duplicate an attribute

When you choose to duplicate an attribute, all the properties of the selected item will be copied to a new attribute as a sibling at the same level, including the relationship. There are several ways to delete an attribute. You must first select it, then:

- choose Duplicate from the Edit menu

&nbsp;

![Contextual menu - Duplicate selected1](<lib/Contextual menu - Duplicate selected1.png>)

- press the shortcut Ctrl+D
- click the button ![Icons - duplicate](<lib/Icons - duplicate.jpeg>) in the toolbar
- right-click the attribute and choose Duplicate

&nbsp;

![Contextual menu - Duplicate selected](<lib/Contextual menu - Duplicate selected.png>)

&nbsp;

### 3.5 Cut, Copy, and Paste

These control have a behavior similar to what is expected in any desktop application. When performing the operation, all the properties of the selected attribute will be copied to a new attribute as a sibling at the same level, including the relationship.

&nbsp;

### 3.6 Collapse/Expand

When an attribute has at least one attribute, its descendance can be collapse or expanded by pressing the - or the + sign to the right of the box:\
![Tree view - expanded](<lib/Tree view - expanded.png>)\
![Tree view - collapsed](<lib/Tree view - collapsed.png>)

&nbsp;

### 3.7 Toggle details

You may also toggle the appearance of details by pressing the ![Icons - toggle Details](<lib/Icons - toggleDetails.jpeg>) button:\
![Tree view - no details](<lib/Tree view - no details.png>)

&nbsp;

## 4. Choosing family of attribute, field type, and choice

### 4.1 family of attributes

![Family of Attributes](<lib/Family of Attributes.png>)

&nbsp;

For an array:\
![Family of Attributes - Array](<lib/Family of Attributes - Array.png>)

&nbsp;

For [schema composition](<https://json-schema.org/understanding-json-schema/reference/combining> "target=\"_blank\"") choices:\
![Family of Attributes - choices](<lib/Family of Attributes - choices.png>)

&nbsp;

### 4.2 Field type

Field types include standard JSON Schema field types, plus the BSON types not already in JSON Schema. BSON is a binary serialization format used to store documents and make remote procedure calls in MongoDB. The BSON specification is located [here](<http://bsonspec.org> "target=\"_blank\""). BSON supports the following data types as values in documents.\
![Tree view - field types](<lib/Tree view - field types.png>)

&nbsp;

This list varies depending on the database target.

&nbsp;

Often with modern databases, you may specify more than one data type for a given attribute, for example string and null. This is the simplest form of polymorphism.

&nbsp;

To add another type, simply click on the + sign to the right in the Properties Pane:\
![Data type - single](<lib/Data type - single.png>)

&nbsp;

Then you may select the additional data type from the dropdown list, change the order with the up/down arrows, or delete with the X:

&nbsp;

![Data type - multiple](<lib/Data type - multiple.png>)

&nbsp;

### 4.3 Choice

For [schema composition](<https://json-schema.org/understanding-json-schema/reference/combining> "target=\"_blank\"") choices, you may add choices for alternate sub-schemas:

&nbsp;

![Tree view - choices](<lib/Tree view - choices.png>)

&nbsp;

### 4.4 Reference definition

You may add references to re-usable objects as explained [here](Reusableobjectsdefinitions.md).\
![Family of Attributes - Ref Def](<lib/Family of Attributes - Ref Def.png>)

&nbsp;

### 4.5 DBRef (MongoDB only)

Hackolade supports this MongoDB [convention](<https://docs.mongodb.com/manual/reference/database-references/> "target=\"_blank\"").

&nbsp;

![Family of Atributes - DBRref](<lib/Family of Atributes - DBRref.png>)

&nbsp;

### 4.6 Pick from list

If you want to re-use a previously created attribute (without making it a re-usable reference definition), then you can copy its properties with this option:

&nbsp;

![Family of Attributes - Pick from List](<lib/Family of Attributes - Pick from List.png>)

&nbsp;

There are several ways to create a new field. Depending on which attribute you select, you will want to add the new attribute as an attribute, or as a sibling.

&nbsp;

and to Append:

&nbsp;

For each of the 3 methods (Add attribute, Insert, and Append), there are 4 ways to do so:

- from the menu, choose Actions > then Add attribute, Insert field or Append field
- press the shortcut Ctrl+H (Add attribute), Ctrl+E (Insert field), or Ctrl+D (Append field)
- from the toolbar, choose the 'add attribute' button ![Icons - addChild](<lib/Icons - addChild.jpeg>)
- inside the central pane, Schema tab, right-click on the box for which you want to create a child attribute, and choose Add Attribute

&nbsp;

![Contextual menu - attributes](<lib/Contextual menu - attributes.png>)
