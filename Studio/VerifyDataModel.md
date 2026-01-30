# Verify Data Model

Starting with version 6.10.0, Hackolade Studio includes a tool to verify the consistency and quality of data models according to a glossary of class and prime terms, and to target-specific attribute rules such as precision/scale for numeric, and length for string data types. &nbsp;

&nbsp;

The model verification is based on:

* business names and not target-specific when it comes to rules verified against the glossary
* technical names and target-specific when it comes to properties-related rules of attributes.&nbsp; Given the variety of targets supported by Hackolade Studio, and sometimes big differences in data types between these targets, it is necessary to have one file for each target.

&nbsp;

## Naming theory

The glossary verifications compare the expression of the business names of model objects with entries in a glossary file.

&nbsp;

### Business names

A business name is an English expression with specific words to describe a single data object (e.g., data model, database, schema, file, table, collection, attribute, field, data element, etc). Each business name comprises one or more optional modifying terms, prime terms, and one class term. These terms are specific to each organization and generally defined by subject matter experts. They should have an agreed upon definition, and are typically maintained in a Glossary.

&nbsp;

Business names should be less than eight words. Nouns should be singular and verbs in present tense.

&nbsp;

In terminology, it is typical to define 3 different units:&nbsp;

\- class terms to represent concept classes

\- prime terms to represent basic primitive concepts

\- modifying terms to represent concept modifiers or attributes.

&nbsp;

Other legacy data modeling tools require that you mark a term as class term.  We designed an approach that we think is more flexible...

&nbsp;

In Hackolade Studio, a term defined in a glossary file is assumed to be an approved term.  The determination that the term is a class term, a prime term, or a modifying term does not come from the term itself in the glossary, but from its position in the expression being evaluated, assuming that it is an English expression.

&nbsp;

Take for example the word "customer":

* Customer is the class term in the 1-word expression "Customer"
* Customer is the prime term in the 2-word expression "Customer Account"
* Customer is a modifying term in the 3-word expression "Customer Identification File"

&nbsp;

#### Class terms

The class term is the highest level of qualification and the most important word in a business name. The class term is **always the last word of a business name** (or in some rare cases a **phrase** such as "Unit of Measure"). It must be a noun **identifying the general purpose** of the data object.

&nbsp;

Examples:

\- specific instance: code, identifier, name, number

\- numeric: amount, count, percent

\- conditional: indicator, switch

\- temporal: date, time, timestamp

\- spatial: line, point, polygon

\- persistent: constant

\- general: document, file, text

&nbsp;

#### Prime terms

A prime term can be **a single word** ( or a **phrase** such as 'Unit of Measure'.)&nbsp; It is the most important **modifier of the class term**, and **directly precedes it**.

&nbsp;

#### Modifying terms

Modifying terms are used to add important business information to a business name, and precede the prime term. &nbsp;

&nbsp;

A glossary loses a significant part of its value for a user if every possible combination of words must be declared in the glossary so model verifications could occur. Therefore the glossary verifications of Hackolade Studio span only prime terms and class terms, and ignore modifiers if they are not themselves declared separately as class terms.&nbsp; Typically, a user will define in the glossary the last 2 terms which are most significant in a name, then allow any kind of declination of these 2 words with other modifiers.

&nbsp;

For example, let's say that you defined the Business Name "Currency Code" in the glossary file. The application will allow any combination of terms that is using this term at the end of the expression without requiring for these combinations to be explicitly declared in the glossary file:

Component Invoice Amount Currency Code

Component Total Amount Currency Code

Unit Price Currency Code

Item Converted Price Currency Code

Item Original Price Currency Code

Item Total Converted Price Currency Code

Item Total Original Price Currency Code

etc...

&nbsp;

We suggest that you experiment with different combinations in a small glossary file and a small model to first understand the behavior of the application, before embarking on the definition of a large glossary file and applying the verification to large data models.

&nbsp;

## Glossary verifications

These verifications are generic, i.e. not specific to a target, and are made by checking the business names in the model with the terms in the glossary file.&nbsp; Any exception to an enabled verification rule is logged into a report.

&nbsp;

### Glossary file

For this step, Hackolade Studio leverage the existing abbreviations .csv file used in Naming Conventions.&nbsp; There's just one optional additional column needed if you want to declare synonyms to be prevented.&nbsp; Terms are checked for each object in the model:&nbsp;

\- containers/groups/databases/schemas/namespaces/keyspaces/...

\- entities/tables/collections/...

\- and mainly for attributes/fields/columns/...

&nbsp;

While Naming Conventions parameters are target-specific, the glossary/abbreviations file is typically the same for all targets. It is the other parameters such as case conversion which are target-specific.

&nbsp;

The glossary file is made of several columns, with Business Name as a first column, and Technical Name as the second column.&nbsp; Then come Description and Synonyms.&nbsp; Multiple synonyms are separated by a pipe ("\|"). &nbsp; Additional columns are ignored by Hackolade.&nbsp; The columns are separated by commas.&nbsp; The first line is the header line, and is ignored in the conversion.&nbsp; The lines are separated by a \<CR\>\<LF\>.&nbsp; There is no limit to the number of lines in the file.&nbsp; The values in the columns are not case-sensitive. &nbsp;

&nbsp;

**Example:**

> Business Name,Technical Name,Description,Synonyms\
action,axn,"The accomplishment of a process over a period of time, in stages, or with the possibility of repetition",behavior\|conduct\
account,acct,,\
currency code,curr\_cd,,\
customer,cust,,\
feedback,fdbak,,

&nbsp;

**Important notes**:&nbsp;

* the first line in the glossary file is a header line describing the columns in the file
* if a cell contains commas, it must be stored in the CSV file in between double quotes
* if your file contains [diacritics](<https://en.wikipedia.org/wiki/Diacritic> "target=\"\_blank\"") (accents, ...) you must save your file with [UTF-8](<https://en.wikipedia.org/wiki/UTF-8> "target=\"\_blank\"") encoding for the function to work properly.&nbsp; If you edit the file using Excel, you should make sure to save it using this CSV UTF-8 option:
* ![Naming Conventions - CSV UTF-8](<lib/Naming Conventions - CSV UTF-8.png>)
* multiple synonyms are separated by a pipe ("\|")

&nbsp;

&nbsp;

### Glossary verifications

Current glossary-related rules are:

* **Invalid Term:** the business name contains terms that are not in the glossary: business names must contain only approved terms drawn from the glossary. If a term in the business name does not exist in the glossary, then an entry is created in the report. Remember that a "term" can be either a single word, or a combination of words, e.g. "Unit of Measure" or "Universal Unique Identifier".
* **Inconsistent Terms:** while each individual term in the business name matches terms in the glossary, the combination of (prime term + class term) does not exist in the terms glossary.&nbsp; For example, the business name "document category code" has 3 terms: "document", "category", and "code" which all exist individually in the glossary.&nbsp; \
The application checks that "category code" exists in the glossary, and if it doesn't, then an entry is created in the report.&nbsp; In the business name "Item Total Converted Price Currency Code", the class term is "Code", the prime term is "Currency".&nbsp; So the application checks that "Currency Code" exists in the glossary.\
Remember that a term could be made of several words, e.g. "Universal Unique Identifier". It counts as just one single term. So in the business name "Commodity Product Description Universal Unique Identifier", the class term is "Universal Unique Identifier", and the prime term is "Description". So the application checks that "Description Universal Unique Identifier" exists in the glossary.
* **Synonyms:** check whether the business name contains synonyms of glossary terms: term names must not contain synonyms of glossary terms. For example, a glossary term "supplier" might have as synonyms "provider", and "seller".&nbsp; If either of these terms are found in business names, then an entry is created in the report.

&nbsp;

In other words, if a class term is not in the glossary, it is flagged as **invalid**.  Same for a prime term.

\
If, for a prime+class combination, they are both declared individually in the glossary but the combination is not in the glossary, then the combination is flagged as **inconsistent**.\
 \
And it is only thru their position in an name that terms are labeled "prime" or "class" in the logic.  The combination of words in a name could be such that a certain term is a class term in some names, and a prime term in others.

&nbsp;

## Attribute properties

All the properties verifications are target-specific.

Hackolade Studio offers predefined, out-of-the-box rules for standard modeling objects such as Containers, Entities, Views, Attributes, and Relationships. These rules can be individually activated or deactivated based on user needs.

In addition, custom verification rules can be defined via configuration files, offering flexibility and control over data quality.

&nbsp;

### Technical names

Technical names are generated by applying to business names: standard abbreviations, processing of illegal characters, and case conversion. This is an optional feature of Hackolade Studio.&nbsp; It is not required to enable [Naming Conventions](<Namingconventions.md>) to use the Model Verification feature.&nbsp; In the absence of a technical name, the application always considers that the technical equals the business name, without need to be declared.

&nbsp;

The length of technical names must meet the constraints of the target.&nbsp; Technical names are generated by applying to business names: standard abbreviations, processing of illegal characters, and case conversion. The length of technical names must meet the constraints of the target.

&nbsp;

### Attribute propRules file

The property rules file is typically stored in the folder:

&nbsp;

> .hackolade/OPTIONS/\<target\>&nbsp;

&nbsp;

It contains several columns:

\- Technical name: \[string\] the name of physical attributes/columns/fields

\- Required: \[boolean\] (default:false) whether attribute must marked as required (a.k.a. NOT NULL)&nbsp;

\- Default: \[string\] the default value if applicable

\- Data Type: \[string\] the most granular data type for the target.&nbsp; For example if type is numeric and subtype is float, then float should be declared here.

\- Length: \[number\] length of string data types

\- Precision: \[number\] total number of digits in a number, not counting the decimal point

\- Scale: \[number\] total number of digits to the right of the decimal point

&nbsp;

**Example:**

> Technical Name,Required,Default,DataType,Length,Precision,Scale\
action\_cd,true,NO\_CHANGE,varchar,10,0,0\
adjustment\_desc,,,varchar,100,0,0\
amt,,,decimal,0,18,3

&nbsp;

### Out-of-the-box verification rules

The objects Container, Entity, View, Attribute, and the Model itself can be automatically checked for the following standard property-related rules:

&nbsp;

* check that the properties of each attribute in the model match the specification in the propRules file. An entry is created in the report for each attribute property not matching the declared value in the target-specific propRules file.

  * **Invalid data type:** verify that the column value in the propRules file, if set, matches the property of the attribute in the model (i.e., if not declared in the file, then the value in the model can be anything.) If not, an entry is created in the report.
  * **Missing required property:** verify that the column value in the propRules file, if set, matches the property of the attribute in the model (i.e., if not declared in the file, then the value in the model can be either true or false.) If not, an entry is created in the report.
  * **Invalid default property:** verify that the column value in the propRules file, if set, matches the property of the attribute in the model (i.e., if not declared in the file, then the value in the model can be anything.) If not, an entry is created in the report.
  * **Invalid length:** if a string data type, verify that the column value in the propRules file, if set, matches the property of the attribute in the model (i.e., if not declared in the file, then the value in the model can be anything.) If not, an entry is created in the report.
  * **Invalid precision:** if a numeric data type, verify that the column value in the propRules file, if set, matches the property of the attribute in the model (i.e., if not declared in the file, then the value in the model can be anything.) If not, create an entry in the report.
  * **Invalid scale:** if a numeric data type, verify that the column value in the propRules file, if set, matches the property of the attribute in the model (i.e., if not declared in the file, then the value in the model can be anything.) If not, an entry is created in the report.

* check additional rules that are independent of propRules file:

  * **Business name is not empty**
  * **Technical name is not empty**
  * **Business name does not start with:** user-defined string, default: "New"
  * **Technical name does not start with:** user-defined string, default: "New"
  * **Description is not empty**
  * **Technical name conflicts with reserved keywords:** independent of glossary. Each target has a list of reserved words per level. An entry in the report is created if an attribute technical name, in full, is a reserved word.
  * **Excessive technical name length:** independent of glossary. Some target have max length of, for example 128 characters. Some customers may have their own more restrictive standards. An entry in the report is created if an attribute technical name is greater than the user-defined length. We store this user-defined length, per target, for future reuse.

&nbsp;

Note that some rules already pro-actively generate warnings in the tool, such as:

* duplicate table names in the same schema
* duplicate column name in the same table
* dangling relationships
* mismatched data types in relationships
* etc. &nbsp;

So these rules did not get included in the list above.

&nbsp;

### User-defined regular expression verification rules

You can define your own verification rules for any string property of any modeling object using regular expressions in a CSV configuration file.

This CSV format enables multiple validation rules per property, supporting more complex and nuanced validation scenarios. It ensures data complies with internal standards and naming conventions.

&nbsp;

#### Supported Properties

User-defined verification rules apply to both standard Hackolade properties and custom properties. Currently, only simple scalar properties (at the root level) are supported. Future releases may include complex types, such as block and group properties.

&nbsp;

#### Regular expression regExpRules file

The regular expression rules file is typically located in the following directory:

> .hackolade/OPTIONS/\<target\>&nbsp;

&nbsp;

The file contains multiple columns that define the rules and their scope.

&nbsp;

| **Column** | **Purpose** | **Allowed values and example** |
| --- | --- | --- |
| Rule Keyword | A unique identifier for the rule | Any unique string to identify the rule, example: *viewNameRule* |
| Rule Name | The name of the rule for the generated report | Any descriptive name for the rule, for example:&nbsp; *verification rule on view name* |
| Severity | Indication of the severity level when a rule fails | Allowed values: *warning* or *error* |
| Object | Identifies the nature of the modeling object for the rule | Use the abstract name of the modeling object:&nbsp; *model, container, entity, view, relationship, attribute* |
| Property | Specifies the property keyword of the object targeted by the rule | Use the JSON keyword found in the persistence model file.&nbsp; This value is case-sensitive and must match exactly how the property is defined in the model.&nbsp; Otherwise, the rule will not be applied.&nbsp; For example: *version, author, description* To identify the correct property keyword, you can open a model file in a text editor such as Notepad, and inspect the JSON content |
| Regular Expression | The pattern with which the property value must match | Any [JavaScript regular expression](<https://www.w3schools.com/jsref/jsref\_obj\_regexp.asp> "target=\"\_blank\"") written using the standard format */yourPattern/flags*. If the expression is not valid, the application will fallback to a simple string comparison (which may yield incorrect results.) &nbsp; There is no verification of the syntax correctness of the regex provided. If your expression contains a comma, enclose it in double quotes to ensure correct CSV formatting.&nbsp; Line breaks are not allowed.&nbsp; See example patterns below. |


&nbsp;

#### Example regExpRules file

> Rule keyword;Rule name;Severity;Object;Property;Regular expression\
&#49;-model-author-not-empty;Model author is specified;Warning;model;author;/\^.+$/\
&#50;-model-version-not-empty;Model version is specified;Warning;model;version;/\^.+$/\
&#51;-table-name-starts-with-T\_-prefix;Table technical name starts with T\_ prefix;warning;entity;code;/\^T\_\[a-zA-Z0-9\_-\]+/\
&#52;-view-name-starts-with-V\_-prefix;View technical name starts with V\_ prefix;warning;view;code;/\^V\_\[a-zA-Z0-9\_-\]+/\
&#53;-relationship-name-starts-with-FK\_-prefix;Relationship name starts with FK\_ prefix;warning;relationship;name;/\^FK\_\[a-zA-Z0-9\_-\]+/

&nbsp;

#### Common regular expression examples

To assist in creating effective regular expressions, here are some common patterns:

&nbsp;

| **Rule** | **RegeEx** |
| --- | --- |
| must be numeric only &nbsp; | */\^\\d+$/* |
| must start with A (case sensitive)&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; | */\^A/* |
| does **not** start with A (case sensitive)&nbsp; &nbsp; | */\^(?\!A)/* |
| must start with A (case insensitive)&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; | */\^A/i* |
| does **not** start with A (case insensitive)&nbsp; | */\^(?\!A)/i* |
| must end with A (case sensitive)&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; | */A$/* |
| does **not** end with A (case sensitive)&nbsp; &nbsp; &nbsp; | */\[\^A\]$/* |
| must end with A (case insensitive)&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; | */A$/i* |
| does **not** end with A (case insensitive)&nbsp; &nbsp; | */\[\^A\]$/i* |
| must contain A (case sensitive) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; | */A/* |
| does **not** contain A (case sensitive) &nbsp; &nbsp; &nbsp; | */\^\[\^A\]\*$/* |
| must contain A (case insensitive) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; | */A/i* |
| does **not** contain A (case insensitive) &nbsp; &nbsp; | */\^\[\^A\]\*$/i* |


&nbsp;

&nbsp;

#### Tips for authoring valid JavaScript regular expressions

For help creating more advanced regular expressions, consider using tools like ChatGPT to generate and refine your patterns. To improve the quality and usability of the generated output, make sure to include format requirements in your prompt.

&nbsp;

For example:

"Generate a JavaScript regular expression that starts and ends with slashes (e.g., */.../*), includes appropriate flags if necessary, and is suitable for insertion into a CSV file (i.e., no line breaks, and wrap the regex in double quotes if it contains a comma). The regex should validate that a name starts with *\<insert your rule here, for example a single uppercase letter (A-Z)\>*, followed by one or more alphanumeric characters (*a-z*, *A-Z*, or *0-9*) and allows dashes and underscores."

&nbsp;

You can also use [regex101.com](<https://regex101.com/> "target=\"\_blank\"") to validate your expressions by selecting the JavaScript (ECMAScript) flavor from the menu.

&nbsp;

⚠️ **Important:** Regular expressions are case-sensitive by default. To ensure matches are not affected by letter casing, use the *i* flag as shown above.

&nbsp;

&nbsp;

## Using the tool to Verify Data Models

A couple of default paths have been added to the user parameters in Tools \> Options, for the default path of the Glossary file, and for the default path where the reports should be created:

![Verify Data Model - Default paths](<lib/Verify Data Model - Default paths.png>)

&nbsp;

The tool can be found in Tools \> Verify Data Model

![Verify Data Model - menu](<lib/Verify Data Model - menu.png>)

&nbsp;

When you invoke the tool, you are first presented with a dialog box:

![Verify Data Model - main dialog](<lib/Verify Data Model - main dialog.png>)

&nbsp;

&nbsp;

With this dialog, you may select and deselect rules to be verified for the loaded data model, and you may change the severity.&nbsp; To select a rule or deselect it, you may toggle the checkbox with a click of the mouse.&nbsp; With a click of the mouse on the severity icon, you can change the severity to be listed in the report for each instance of a failed verification.

&nbsp;

After you click the Submit button and select the report name and path for storage, the application executes the selected rules, and displays this dialog at the end of the process:

![Verify Data Model - open in Excel](<lib/Verify Data Model - open in Excel.png>)

&nbsp;

&nbsp;

## Interpreting the exception report

Each failed rule results in an entry in the report.&nbsp; If a single object in the model fails multiple rules, there multiple lines are generated in the report.

&nbsp;

When running the verification for the first time, particularly on large models, the report could be quite long.&nbsp; It is strongly suggested to then focus on the biggest issues first, for example wrong data type, before adding other rules like length, precision, and scale.&nbsp; etc.&nbsp; Be aware that some rules depend on other rules.&nbsp; For example if an attribute has data type varchar instead of numeric, then precision and scale would be wrong as well.&nbsp; So it it is probably preferable to fix all the data type first before running the verification again on precision and scale.

&nbsp;

There are many columns in the CSV report opened in Excel.&nbsp; The first thing to do is to go to the Data menu tab and click on Filter, then to go the View tab \> Freeze Panes \> Freeze Top Row.&nbsp; We also suggest to hide the technical columns modelGUID, containerGUID, entityGUID, relationshipGUID, and attribGUID.&nbsp; These columns are only useful for automated processing.

&nbsp;

There are different groups of columns in the report:

* Verification failure identification: these columns can be used to filter lines and address them in chunks of similar types of failures.&nbsp; They are: verifRuleCode, verifRuleName, verifRuleSeverity
* Objects GUIDs: these columns are used for reference to the unique internal keys of objects in Hackolade models.&nbsp; They are: modelGUID, containerGUID, entityGUID, relationshipGUID, and attribGUID, and you should probably hide them to increase legibility of the report.
* Objects Business Names and Technical Names: these columns contain the names of the object hierarchy and which might have been used in the glossary verification.&nbsp; They are: modelBusName, modelTechName, containerBusName, containerTechName, entityBusName, entityTechName, relationshipName, attribBusName, attribTechName
* Attributes properties: these columns contain the properties verified by the tool.&nbsp; They are: attribDataType, attribLength, attribPrecision, attribScale, attribRequired, attribDefault
* Glossary entries: these columns contain the values Business Names in the glossary against which the object name was verified, as well as the corresponding Technical Names, for reference.&nbsp; They are: glossTermBusName, glossTermTechName, glossSysnonyms
* Attribute rules values: these columns contain the values for Required, Default, Data Type, Length, Precision and Scale, that are used for verification of the attribute properties.&nbsp; The columns are: rulesRequired, rulesDefault, rulesDataType, rulesLength, rulesPrecision, rulesScale

&nbsp;

