# Property controls

A custom property control is defined using the following syntax, starting with 3 mandatory keywords:

&nbsp;

## Mandatory keywords

### propertyName

(*string*) - required; used to display label in the Properties Panes for a property.

&nbsp;

### propertyKeyword

(*string*) - required; used in the main code as a keyword; no whitespaces are allowed.

&nbsp;

### propertyType

(*string*) - required; defines the type of control used in the Properties Pane, with the allowed values below:

&nbsp;

&#49;. simple text: text

&#50;. text area (pop-up text): details with template = textarea

&#51;. dropdown selection (unique): select

&#52;. dropdown selection (multiple):&nbsp;

&#53;. numeric: numeric

&#54;. checkbox (boolean): checkbox

&#55;. properties group: group

&#56;. properties block: block

&#57;. field list: fieldList

&#49;0. field list with dropdown of attributes: fieldList with template = orderedList

&#49;1. select from a list of entities

&nbsp;

&nbsp;

The rest of the keywords below are optional.

&nbsp;

## Syntax

Below is the list of optional keywords.

&nbsp;

### abbr

(string) - optional: short marker drawn on the attribute in the ERD, e.g. PK

&nbsp;

### addTimestampButton

(*boolean*) - optional (default = false): if "propertyType": "details" and "template": "textarea", a button "Add timestamp" can be made to appear

&nbsp;

&nbsp;

### allowNegative

(*boolean*) - optional (default = true): for numeric controls only.&nbsp; Self explanatory.&nbsp; If false, equivalent to setting minValue to 0.

&nbsp;

### attributeList

(*array of values*) - optional) : used in combination with propertyType = fieldList and template = orderedList &nbsp;

&nbsp;

&nbsp;

![Image](<lib/Custom prop control attributeList.png>)

&nbsp;

> &nbsp; &nbsp; {\
&nbsp; &nbsp; &nbsp; &nbsp; "propertyName": "Key",\
&nbsp; &nbsp; &nbsp; &nbsp; "propertyKeyword": "indxKey",\
&nbsp; &nbsp; &nbsp; &nbsp; "propertyType": "fieldList",\
&nbsp; &nbsp; &nbsp; &nbsp; "template": "orderedList",\
&nbsp; &nbsp; &nbsp; &nbsp; "attributeList": \["ascending", "descending"\],\
&nbsp; &nbsp; &nbsp; &nbsp; "requiredProperty": true\
&nbsp; &nbsp; }

&nbsp;

&nbsp;

### cleanDependency

(*boolean*) - optional (default = false) - deprecated from v7.6.1: used to reset related properties to their default values when the user chooses a different option. When the related property doesn’t have default value, it will not be changed. When there are few configurations for the same \*propertyKeyword\*, the property will not be changed as well.

&nbsp;

### customScriptVariables

(boolean) - optional (default = false): used in template = codeEditor, allows to use predefined variables, to be resolved automatically during script generation, as described [here](<https://hackolade.com/help/Target-specific.html#Using%20variables>).

&nbsp;

&nbsp;

### defaultValue&nbsp;

(*string/number/boolean*) - optional; default value for property

&nbsp;

&nbsp;

### dependency

(*object*) - optional: contains an object with a key and arguments determining whether or not to display this property. &nbsp;

&nbsp;

Example of a simple dependency, testing the value of a property:

&nbsp;

> &nbsp; &nbsp; "dependency": {\
&nbsp;     &nbsp; "key": "type",\
&nbsp;     &nbsp; "value": "string"\
&nbsp; &nbsp; }

&nbsp;

Example of a dependency, testing for the presence of a property:

> &nbsp;

> &nbsp; &nbsp; "dependency": {\
&nbsp;     &nbsp; "key": "name",\
&nbsp;     &nbsp; "exist": false\
&nbsp; &nbsp; }

&nbsp;

Example of a dependency, testing for the properties of the string characteristics of a property:

> &nbsp;

> &nbsp; &nbsp; "dependency": {\
&nbsp;     &nbsp; "key": "name",\
&nbsp;     &nbsp; "minLength": 5,\
&nbsp;     &nbsp; "maxLength": 10\
&nbsp; &nbsp; }

&nbsp;

Example of a dependency, testing for the properties of the regex pattern value of a property:

> &nbsp;

> &nbsp; &nbsp; "dependency": {\
&nbsp;     &nbsp; "key": "name",\
&nbsp;     &nbsp; "pattern": "\^(H\|h)ackolade (2.5.8\|3.0.2)$"\
&nbsp; &nbsp; }

&nbsp;

Example of a dependency, testing for multiple values of a property (equivalent to an or operator):

&nbsp;

> &nbsp; &nbsp; "dependency": {\
&nbsp; &nbsp; &nbsp; &nbsp; "key": "mode",\
&nbsp; &nbsp; &nbsp; &nbsp; "value": \["char","varchar", "bit", "varbit"\]\
&nbsp; &nbsp; }

&nbsp;

Example of a dependency, testing for the properties of the numeric value of a property:

&nbsp;

> &nbsp; &nbsp; "dependency": {\
&nbsp;     &nbsp; "key": "amount",\
&nbsp;     &nbsp; "minimum": 10,\
&nbsp;     &nbsp; "exclusiveMinimum": true,\
&nbsp;     &nbsp; "maximum": 100\
&nbsp; &nbsp; }

&nbsp;

Example of a dependency combining and and or operators:

&nbsp;

> &nbsp; &nbsp; "dependency": {\
&nbsp;     &nbsp; "type": "and",\
&nbsp;     &nbsp; "values": \[\
&nbsp;         &nbsp; {\
&nbsp;             &nbsp; "type": "or",\
&nbsp;             &nbsp; "values": \[\
&nbsp;                 &nbsp; {\
&nbsp;                     &nbsp; "level": "parent",\
&nbsp;                     &nbsp; "key": "name",\
&nbsp;                     &nbsp; "value": "query"\
&nbsp;                 &nbsp; },\
&nbsp;                 &nbsp; { \
&nbsp;                     &nbsp; "level": "parent",\
&nbsp;                     &nbsp; "key": "name",\
&nbsp;                     &nbsp; "value": "formData"\
&nbsp;                 &nbsp; }\
&nbsp;             &nbsp; \]\
&nbsp;         &nbsp; },\
&nbsp;         &nbsp; {\
&nbsp;             &nbsp; "level": "parent",\
&nbsp;             &nbsp; "key": "structureType",\
&nbsp;             &nbsp; "value": true\
&nbsp;         &nbsp; }\
&nbsp;     &nbsp; \]\
&nbsp; &nbsp; }

&nbsp;

As you can see above, you can use for your dependency a keyword located at a different level.&nbsp; To avoid any risk of confusion if you use the same keyword at different levels, it is recommended to use the dot notation based on the root level.

&nbsp;

> &nbsp; &nbsp; &nbsp; &nbsp; {\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "propertyName": "Enabled",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "propertyKeyword": "configEnabled",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "propertyType": "checkbox",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "dependency": {\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "level": "objectRoot",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "key": "dbtLabs.semanticComponent",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "value": "metric"\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }\
&nbsp; &nbsp; &nbsp; &nbsp; },

&nbsp;

When a dependency contains a key pointing to a multipleCheckboxSelect control (dropdown with multiple select), then the key must be appended with dot+star (".\*") to indicate "any element in the array".

&nbsp;

&nbsp;

> &nbsp; &nbsp; &nbsp; &nbsp; "structure": \[\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "propertyName": "Data Classification",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "propertyKeyword": "dataClassification",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "propertyType": "multipleCheckboxSelect",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "options": \[\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "PII",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "GDPR",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "Confidential",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "Public"\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \]\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "propertyName": "Shows when PII is included",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "propertyKeyword": "showsWhenPII",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "propertyType": "text",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "dependency": {\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "key": "dataClassification.\*",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "value": "PII"\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "propertyName": "Shows when PII or GDPR",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "propertyKeyword": "showsWhenPIIorGDPR",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "propertyType": "text",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "dependency": {\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "key": "dataClassification.\*",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "value": \[\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "PII",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "GDPR"\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \]\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "propertyName": "Shows when Confidential is NOT selected",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "propertyKeyword": "showsWhenNotConfidential",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "propertyType": "text",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "dependency": {\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "type": "not",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "values": \[\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "key": "dataClassification.\*",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "value": "Confidential"\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \]\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "propertyName": "Shows when PII and GDPR",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "propertyKeyword": "showsWhenPIIandGDPR",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "propertyType": "text",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "dependency": {\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "type": "and",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "values": \[\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "key": "dataClassification.\*",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "value": "PII"\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "key": "dataClassification.\*",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "value": "GDPR"\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \]\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }\
&nbsp; &nbsp; &nbsp; &nbsp; \]&nbsp;

&nbsp;

&nbsp;

### disabledOption

(*boolean*) - optional (default = false): only applicable to "propertyKeyword": "dropdownProp" if the dropdown list must appear in grey and disabled.

&nbsp;

&nbsp;

### disabledOnCondition

(*object*) - optional: disables the property if any of conditions is true for the current entity. Must be an array of condition objects. The condition object can have the following structure:

&nbsp;

> &nbsp; &nbsp; {\
&nbsp; &nbsp; &nbsp; &nbsp; "propertyName": "Or replace",\
&nbsp; &nbsp; &nbsp; &nbsp; "propertyKeyword": "orReplace",\
&nbsp; &nbsp; &nbsp; &nbsp; "propertyType": "checkbox",\
&nbsp; &nbsp; &nbsp; &nbsp; "disabledOnCondition": {\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "key": "ifNotExist",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "value": true\
&nbsp; &nbsp; &nbsp; &nbsp; }\
&nbsp; &nbsp; }

&nbsp;

&nbsp;

### disableForDefinitions

(*boolean*) - optional (default = false): keeps the control active inside references of a reusable definitions

&nbsp;

### editorDialect

(string) - optional:&nbsp; used in template = codeEditor, editorDialect is one of the possible temptlateOptions and allows for syntax highlighting depending on the language: sql, pgsql, markdown, javascript, yaml.

&nbsp;

### enableForReference

(*boolean*) - optional: by default, properties of references to a definition (local, model or external) are typically disabled.&nbsp; By setting this to true, the property can be editable in the reference and its value has higher priority than the same property value from the referenced definition.&nbsp; So, when the reference is resolved, the properties values will be taken from the reference (if present) and not from its definition.

&nbsp;

### excludeCurrent

(*boolean*) - optionsl (default = false): in case of selectHashed list, excludes the current object from the list

&nbsp;

### helpUrl

(string with URL) - optional: allows to display a question mark ("?") icon next to the property label, pointing the a web page containing instructions.

&nbsp;

### inputPlaceholder

(*string*) - optional: displays a greyed out hint in text background

&nbsp;

### groupItemLimit

(numeric) - optional: inside a propertyType = group, it is possible to maximum number of groups

&nbsp;

### hidden

(*boolean*) - optional (default = false): hides the control from the pane while keeping the value.&nbsp;

&nbsp;

### labelName

(*string*) - optional: display an alternate label for the propertyName

&nbsp;

### markdown

(*boolean*) - optional (default = true): if "propertyType": "details" and "template": "textarea", markdown can be turned off (for example for functions)

&nbsp;

### maxValue

(*number*) - optional: for numeric controls only. Self explanatory

&nbsp;

### minValue

(*number*) - optional: for numeric controls only. Self explanatory

&nbsp;

### options

(*array*) - optional: used to define possible values in the the list to choose from, if propertyType is select.

&nbsp;

### propertySource

(object) - optional: used with propertyType = selecthashed if you need to specify the source at a different object level than the current.

&nbsp;

> &nbsp; &nbsp; {\
&nbsp; &nbsp; &nbsp; &nbsp; "propertyName": "Tag name",\
&nbsp; &nbsp; &nbsp; &nbsp; "propertyKeyword": "tagName",\
&nbsp; &nbsp; &nbsp; &nbsp; "propertyTooltip": "Specify tag to be referenced at all levels",\
&nbsp; &nbsp; &nbsp; &nbsp; "propertyType": "selecthashed",\
&nbsp; &nbsp; &nbsp; &nbsp; "withEmptyOption": true,\
&nbsp; &nbsp; &nbsp; &nbsp; "propertySource": {\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "level": "container",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "source": "tags.\*.name"\
&nbsp; &nbsp; &nbsp; &nbsp; }\
&nbsp; &nbsp; }

&nbsp;

&nbsp;

&nbsp;

### propertyTooltip

(*string*) - optional: only taken into account for propertyTypes: text area,&nbsp; dropdown, properties group, and field list

&nbsp;

&nbsp;

### regex

(*string*) - optional: defines the regex validation for this specific property (the same propertyName could have a different validation rule elsewhere.)

&nbsp;

### requiredProperty

(*boolean*) - optional (default = false): adds an asterisk next to the property name in the Properties Pane.

&nbsp;

### shouldValidate

(*boolean*) - optional (default = false): defines whether field should be validated or any value is allowed.&nbsp; Validation rules are defined once in validationRegularExpressions.json, and are the same in any matching propertyName in any level. &nbsp;

&nbsp;

### step

(numeric) - optional (default = 1): for a numeric propeety typically defined between a nimValue and a maxValue, the step increment that the up/down arrows allow.

&nbsp;

> {\
&nbsp; &nbsp; "propertyName": "Numeric",\
&nbsp; &nbsp; "propertyKeyword": "numericProp",\
&nbsp; &nbsp; "propertyType": "numeric",\
&nbsp; &nbsp; "valueType": "number",\
&nbsp; &nbsp; "allowNegative": false,\
&nbsp; &nbsp; "minValue": 0,\
&nbsp; &nbsp; "maxValue": 1,\
&nbsp; &nbsp; "step": 0.01,\
&nbsp; &nbsp; "propertyValidate": true\
}

&nbsp;

### template&nbsp;

(string) - optional; template used in the modal window if propertyType is details; possible value is:&nbsp;

\- details: textarea, or textAreaJSON (input is validated to be JSON)

\- fieldList: orderedList

\- code editor

\- collectionTree

\- entities

\- boolean

\- definitions

&nbsp;

### templateOptions

(object) - optional: allows to specify the behavior of the template

&nbsp;

> &nbsp; &nbsp; {\
&nbsp; &nbsp; &nbsp; &nbsp; "propertyName": "Before CREATE VIEW",\
&nbsp; &nbsp; &nbsp; &nbsp; "propertyKeyword": "beforeCreateView",\
&nbsp; &nbsp; &nbsp; &nbsp; "propertyType": "details",\
&nbsp; &nbsp; &nbsp; &nbsp; "markdown": false,\
&nbsp; &nbsp; &nbsp; &nbsp; "template": "codeEditor",\
&nbsp; &nbsp; &nbsp; &nbsp; "templateOptions": {\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "editorDialect": "sql",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "customScriptVariables": true\
&nbsp; &nbsp; &nbsp; &nbsp; }\
&nbsp; &nbsp; }

&nbsp;

### typeDecorator

(*boolean*) - optional (default = true): if false, turns off the display of length in parenthesis in ERD, e.g. for *varchar* data type instead of *varchar(4000)*.

&nbsp;

&nbsp;

### validation

(*object*) - optional: adds a warning badge in case no value is in the property, with a tooltip message:

&nbsp;

> &nbsp; &nbsp; &nbsp; &nbsp; "requiredProperty": true,\
&nbsp; &nbsp; &nbsp; &nbsp; "validation": {\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "required": true,\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "message": "Required property"\
&nbsp; &nbsp; &nbsp; &nbsp; }

&nbsp;

### valueType

(*string*) - optional; type (one out of 7 basic types) to define validation rules.

&nbsp;

### withEmptyOption

(boolean) - optional (default = false): used in propertyType = selectHashed to determine whether the dropdown list should include an empty option or just the strict list of possible choices.

&nbsp;

&nbsp;

## Input controls

For your properties, you may choose among a number of input controls:

### Simple text

Display a box for short free-form text input

&nbsp;

![Custom props control simple text](<lib/Custom props control simple text.png>)

&nbsp;

One may find useful to add keywords such as propertyTooltip, valueType, inputPlaceHolder, and defaultValue.

&nbsp;

> {\
&nbsp; &nbsp; "propertyName": "Simple text",\
&nbsp; &nbsp; "propertyKeyword": "simpletextProp",\
&nbsp; &nbsp; "propertyType": "text",\
&nbsp; &nbsp; "valueType": "string"\
}

&nbsp;

### Text area (pop-up box)

For longer, more elaborate text, possibly including URL hyperlinks and markdown, this control allows users to click the ellipse (3 dots) in the properties pane to pop a box up.

&nbsp;

![Custom props control textarea](<lib/Custom props control textarea.png>)

One may find useful to add keywords such as markdown (set to true), or addTimeStampButton

&nbsp;

![Custom props control textarea pop-up](<lib/Custom props control textarea pop-up.png>)

&nbsp;

> {\
&nbsp; &nbsp; "propertyName": "Text area",\
&nbsp; &nbsp; "propertyKeyword": "textareaProp",\
&nbsp; &nbsp; "propertyTooltip": "Popup for multi-line text entry",\
&nbsp; &nbsp; "propertyType": "details",\
&nbsp; &nbsp; "template": "textarea",\
&nbsp; &nbsp; "markdown": false\
}

&nbsp;

### Dropdown list selection (unique)

Display a list of allowed values whereby only a single value is possible.&nbsp; If the choice is optional, make sure to include an empty "" option, generally at the top of the list.&nbsp; You may define a defaultValue.&nbsp; It is also easy to build a dependency on the value selected in another property.

&nbsp;

![Custom props control dropdown](<lib/Custom props control dropdown.png>)

&nbsp;

&nbsp;

> {\
&nbsp; &nbsp; "propertyName": "Dropdown selection",\
&nbsp; &nbsp; "propertyKeyword": "dropdownProp",\
&nbsp; &nbsp; "shouldValidate": false,\
&nbsp; &nbsp; "propertyTooltip": "Select from list of options",\
&nbsp; &nbsp; "propertyType": "select",\
&nbsp; &nbsp; "options": \[\
&nbsp;     &nbsp; "Option 1",\
&nbsp;     &nbsp; "Option 2",\
&nbsp;     &nbsp; "Option 3",\
&nbsp;     &nbsp; "Option 4"\
&nbsp; &nbsp; \]\
}

&nbsp;

### Dropdown list selection (multiple)

Display a list of allowed values whereby 0 to multiple values are allowed.

&nbsp;

![Custom props control dropdown multi](<lib/Custom props control dropdown multi.png>)

&nbsp;

> {\
&nbsp; &nbsp; "propertyName": "Dropdown with multiple selection",\
&nbsp; &nbsp; "propertyKeyword": "dropdownMulti",\
&nbsp; &nbsp; "propertyTooltip": "Select from list of options",\
&nbsp; &nbsp; "propertyType": "multipleCheckboxSelect",\
&nbsp; &nbsp; "options": \[\
&nbsp;     &nbsp; "Option 1",\
&nbsp;     &nbsp; "Option 2",\
&nbsp;     &nbsp; "Option 3",\
&nbsp;     &nbsp; "Option 4"\
&nbsp; &nbsp; \]\
}

&nbsp;

### numeric

Display a box that only allows numeric values.&nbsp; Up and down arrows allow to increase or decrease the value according to a defined step (if different than 1). &nbsp;

&nbsp;

![Custom props control numeric](<lib/Custom props control numeric.png>)

> &nbsp;

> {\
&nbsp; &nbsp; "propertyName": "Numeric",\
&nbsp; &nbsp; "propertyKeyword": "numericProp",\
&nbsp; &nbsp; "propertyType": "numeric",\
&nbsp; &nbsp; "valueType": "number",\
&nbsp; &nbsp; "allowNegative": false,\
&nbsp; &nbsp; "minValue": 0,\
&nbsp; &nbsp; "maxValue": 1,\
&nbsp; &nbsp; "step": 0.01,\
&nbsp; &nbsp; "propertyValidate": true\
}

> &nbsp;

### checkbox (boolean)

Displays a checkbox for boolean values true/false. &nbsp;

&nbsp;

![Custom props control checkbox](<lib/Custom props control checkbox.png>)

&nbsp;

&nbsp;

> {\
&nbsp; &nbsp; "propertyName": "Checkbox",\
&nbsp; &nbsp; "propertyKeyword": "checkboxProp",\
&nbsp; &nbsp; "propertyType": "checkbox"\
}

&nbsp;

### properties group

Displays a complex structure of one or more properties, whereby multiple groups can be created.&nbsp; To create the group, the user clicks on the + plus sign.&nbsp; The user may delete a previously created group by clicking the X.

&nbsp;

![Custom props control group](<lib/Custom props control group.png>)

&nbsp;

&nbsp;

> {\
&nbsp; &nbsp; "propertyName": "Group",\
&nbsp; &nbsp; "propertyType": "group",\
&nbsp; &nbsp; "propertyKeyword": "grpProp",\
&nbsp; &nbsp; "propertyTooltip": "",\
&nbsp; &nbsp; "structure": \[\
&nbsp;     &nbsp; {\
&nbsp;         &nbsp; "propertyName": "Simple Grp Text",\
&nbsp;         &nbsp; "propertyKeyword": "simpleGrpText",\
&nbsp;         &nbsp; "propertyType": "text"\
&nbsp;     &nbsp; },\
&nbsp;     &nbsp; {\
&nbsp;         &nbsp; "propertyName": "Group Number",\
&nbsp;         &nbsp; "propertyKeyword": "grpNumber",\
&nbsp;         &nbsp; "propertyValidate": true,\
&nbsp;         &nbsp; "propertyType": "numeric",\
&nbsp;         &nbsp; "valueType": "number",\
&nbsp;         &nbsp; "allowNegative": false\
&nbsp;     &nbsp; }\
&nbsp; &nbsp; \]\
}

&nbsp;

&nbsp;

### properties block

A block control is similar to a group control except for the fact that there can only be 0 or 1 block entry, whereas groups allows between 0 and multiple entries.

&nbsp;

![Custom props control block](<lib/Custom props control block.png>)

&nbsp;

&nbsp;

&nbsp;

### field list

This control allows to select items from a dialog of allowed items (for example columns of an entity that can be part of a composite primary key).&nbsp; the items can be ordered, either through the sequence used during selection, or later on with the up/down arrow buttons.

&nbsp;

![Custom props control filed list](<lib/Custom props control filed list.png>)

&nbsp;

&nbsp;

> {\
&nbsp; &nbsp; "propertyName": "Field List",\
&nbsp; &nbsp; "propertyKeyword": "keyList",\
&nbsp; &nbsp; "propertyType": "fieldList",\
&nbsp; &nbsp; "template": "orderedList"\
}

&nbsp;

### field list with dropdown of attributes

Optionally, it may be useful to qualify the items in a field list with different possible attributes.

&nbsp;

![Custom props control list with attrib](<lib/Custom props control list with attrib.png>)

&nbsp;

&nbsp;

> {\
&nbsp; &nbsp; "propertyName": "Field List w/ dropdown",\
&nbsp; &nbsp; "propertyKeyword": "keyListOrder",\
&nbsp; &nbsp; "propertyType": "fieldList",\
&nbsp; &nbsp; "template": "orderedList",\
&nbsp; &nbsp; "types": \[\
&nbsp;     &nbsp; "ascending",\
&nbsp;     &nbsp; "descending"\
&nbsp; &nbsp; \]\
} 

&nbsp;

&nbsp;

### select from a list of entities

This control allows to list entities of another object level to select from.

&nbsp;

> &nbsp; &nbsp; {\
&nbsp; &nbsp; &nbsp; &nbsp; "propertyName": "Tag name",\
&nbsp; &nbsp; &nbsp; &nbsp; "propertyKeyword": "tagName",\
&nbsp; &nbsp; &nbsp; &nbsp; "propertyTooltip": "",\
&nbsp; &nbsp; &nbsp; &nbsp; "propertyType": "selecthashed",\
&nbsp; &nbsp; &nbsp; &nbsp; "withEmptyOption": true,\
&nbsp; &nbsp; &nbsp; &nbsp; "propertySource": {\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "level": "container",\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "source": "tags.\*.name"\
&nbsp; &nbsp; &nbsp; &nbsp; }\
&nbsp; &nbsp; }

&nbsp;

see keywords withEmptyOption, and propertySource

