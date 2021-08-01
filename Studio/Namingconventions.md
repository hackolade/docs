# Naming conventions

**Note:** You may wish to view the [how-to video](<https://hackolade.com/videos.html#naming> "target=\"\_blank\"") on this subject.

&nbsp;

Hackolade includes the ability to maintain both a ‘business name’ and a ‘technical name’ for objects (containers, entities, and attributes.)&nbsp; To facilitate the maintenance of these 2 names, it is possible to keep them synchronized and transformed based on a set of user-driven parameters, and optionally based on a conversion file maintained outside of the application.&nbsp; Name conversion can go both directions: Business-to-Technical, or Technical-to-Business.&nbsp; Furthermore, when performing reverse-engineering, it is assumed that the database instance contains technical names, to be transformed in business names.

&nbsp;

If you do not wish to use this feature, keep disabled the Name Coupling parameter (see below) and simply leave the technical name property blank, so the (business) name property is used by default.

&nbsp;

Starting with version 4.1.2, we have replaced global parameters with separate target-specific parameters to allow different behavior depending on target.&nbsp; Also, the parameters are stored in a JSON file in the C:\\Users\\%usernames%\\.hackolade\\options\\\<targetname\> directory, so they can be shared with teammates via Git.

&nbsp;

## Conversion file

A conversion file is not mandatory to use the Naming Conventions feature. &nbsp; A conversion file is a .csv file listing words that may appear in object names (business name), with a corresponding technical name to use instead in database definition scripts.

&nbsp;

The conversion file is made of at least 2 columns, with Business name as a first column, and Technical name as the second column.&nbsp; Additional columns are ignored by Hackolade.&nbsp; The columns are separated by commas.&nbsp; The first line is the header line, and is ignored in the conversion.&nbsp; The lines are separated by a \<CR\>\<LF\>.&nbsp; There is no limit to the number of lines in the file.&nbsp; The values in the columns are not case-sensitive.&nbsp; A case conversion may be applied in the conversion parameters, cfr below.

&nbsp;

Example:

Business Name,Technical Name,Optional Description

account,acct,

customer,cust,

feedback,fdbak,

&nbsp;

## Conversion parameters

Conversion parameters are specific to each target.&nbsp; To modify the behavior of the name sync feature for a target, user options can be set in Tools \> Options \> Naming Conventions:

&nbsp;

![Image](<lib/Naming%20Conventions%20-%20parameters.png>)

**Application target:** select the target for which these parameters apply

**Enable auto-complete:** when this option is enabled, auto-completion is active to use the conversion file to type-ahead names as they are created.

**Default name coupling:** 3 options are available from the dropdown box: No, Business-to-Technical, or Technical-to-Business. &nbsp;

**Specify** path and file name of the conversion file, or choose to Convert without a file and using the only the rules specified below.&nbsp; If you update the file while Hackolade is open, you may press the refresh button to reload the file.

**Display:** choose to see the Business name or the Technical name in the Object Browser, ER Diagram and hierarchical schema view

&nbsp;

**Business-to-Technical Conversion:** the following options, if enabled will be applied after the file conversion (with or without file.)

**Remove vowels:** when this option is enabled, the vowels in the name are suppressed

**Invalid characters:** the characters declared can optionally be removed or replaced by another character.&nbsp; Example of invalid characters: "\!?.,:;()=+-\*@/\\", and replacing character: "\_"&nbsp;

**Case conversion:** choose from the dropdown:

* *none*: no case conversion is performed
* *camelCase*: also know as [lowerCamelCase](<http://wiki.c2.com/?LowerCamelCase> "target=\"\_blank\""), words are joined together, and the first letter of the first word is lowercase, while the first letter of the subsequent words is capitalized
* [*PascalCase*](<http://wiki.c2.com/?PascalCase> "target=\"\_blank\""): also know as [UpperCamelCase](<http://wiki.c2.com/?UpperCamelCase> "target=\"\_blank\""), words are joined together, and the first letter of every word, including the first one, is capitalized&nbsp;
* [*lowercase*](<http://wiki.c2.com/?LowerCase> "target=\"\_blank\""): all letters are converted to lowercase
* [*UPPERCASE*](<https://en.wikipedia.org/wiki/Capitalization#All\_caps> "target=\"\_blank\""): all letter are converted to UPPERCASE
* [*snake\_case*](<https://en.wikipedia.org/wiki/Snake\_case> "target=\"\_blank\""): all letters are converted to lowercase, plus words are separated with a underscore "\_"
* [*kebab-case*](<http://wiki.c2.com/?KebabCase> "target=\"\_blank\""): all letters are converted to lowercase, plus words are separated with a dash "-"
* *dot.case*: all letters are converted to lowercase, plus words are separated with a dot "."
* *path/case*: all letters are converted to lowercase, plus words are separated with a slash "/"

&nbsp;

**Technical-to-Business Conversion:** the following options, if enabled will be applied after the file conversion (with or without file.)

**Case conversion:** If enabled, a space is inserted between words detected in the technical name (based on the presence of a separator such as underscore (‘\_’), a dash (‘-‘), a dot (‘.’), a slash (‘/’), or simply an Upper case letter).&nbsp; Choose from the dropdown:

* *none*: no case conversion is performed
* [*lower case*](<http://wiki.c2.com/?LowerCase> "target=\"\_blank\""): all letters are converted to lowercase
* [*UPPER CASE*](<https://en.wikipedia.org/wiki/Capitalization#All\_caps> "target=\"\_blank\""): all letter are converted to UPPERCASE
* [*Proper case*](<https://www.computerhope.com/jargon/p/proper-case.htm> "target=\"\_blank\""): the first letter of every word is capitalized – no exceptions
* [*Title case*](<https://en.wikipedia.org/wiki/Capitalization#Title\_case> "target=\"\_blank\""): the first letter of every word is capitalized, except for certain small words, such as articles and short prepositions
* [*Sentence case*](<https://en.wikipedia.org/wiki/Capitalization#Sentence\_case> "target=\"\_blank\""):  only the first letter of the sentence or phrase is capitalized

&nbsp;

Upon exit of the dialog (via OK or Apply) after making a change in parameters, the user will be prompted to choose whether: to apply the changes to just previously coupled names, to apply the changes to all object names, or to not apply any of the changes performed by canceling the dialog.

&nbsp;

&nbsp;

![Image](<lib/Naming%20Conventions%20-%20apply%20changes%20dialog.png>)

&nbsp;

&nbsp;

&nbsp;

## Properties Pane

In the properties pane, the relationship between business name and technical name can have 3 states: OFF (default), convert Business name to Technical name, or convert technical name to business name.&nbsp; This state can be set separately for each individual object.&nbsp; To set Naming Conventions to control the business names and technical names of all objects, select Tools \> Options \> Naming Conventions, then choose either Business-to-Technical or Technical-to-Business from the dropdown "Enable name coupling".

&nbsp;

Let’s say we have this starting situation:

![Image](<lib/Naming%20Conventions%20-%20properties.png>)

&nbsp;

To indicate that coupling is OFF between business and technical name, the 2 = sign icons to the right are un-selected.&nbsp; The user could simply type the technical name of his choice,&nbsp; without any compliance to the glossary file.

&nbsp;

Now, if the user wants to apply naming convention by using the conversion file referenced in the parameters, he would just click on the = sign to the right of the Technical name:

![Image](<lib/Naming%20Conventions%20-%20B2T%20properties.png>)

where the = sign icon shown as pressed, and the Business name is converted into the Technical name by using the conversion file and other conversion parameters.&nbsp; While the = sign icon is ON, the Technical name field is locked and cannot be edited.

&nbsp;

&nbsp;

If the Technical name = sign icon is pressed again, the entry field is unlocked and the entry can be edited again:

![Image](<lib/Naming%20Conventions%20-%20neutral%20properties.png>)

&nbsp;

If the Business name = sign icon is pressed this time, the Technical name is converted into the Business name by using the conversion file and other conversion parameters.&nbsp; While the = sign icon is ON, the Business name field is locked and cannot be edited.

&nbsp;

## Behavior during Reverse-Engineering

During Reverse-Engineering, if coupling parameters is set to 'No', then all object names from the source (whether from a DB instance, XSD, DDL, Excel, JSON, etc...) are stored in the Business Name property.

&nbsp;

If coupling is set to either Business-to-Technical, or Technical-to-Business, the result of the Reverse-Engineering is the same.&nbsp; In both cases, the object names from the source are stored in the Technical Name property and converted to Business Name using the conversion parameter.&nbsp; That's intuitively obvious when the coupling parameter is set to Technical-to-Business.

&nbsp;

But you may wonder why the handling is done as such when the coupling parameter is set to Business-to-Technical... The following dialog is presented to the user:

![Image](<lib/Naming%20Conventions%20-%20RE%20warning.png>)

&nbsp;

The only safe method we can ensure is one by which the Technical Name come from the source is preserved, no matter the conversion parameters.&nbsp; Say we have a source object called cust\_acct and the Technical-to-Business is set in such a way that the Business Name becomes Cust Acct.&nbsp; If the application applies Business-to-Technical conversion that would be set for example to camelCase, the Technical Name would be changed to custAcct, thereby losing the original cust\_acct in the source.&nbsp; We prefer to let the user choose the expected outcome to either keep it as is, or to change the parameters and apply these changes to the model.

&nbsp;

&nbsp;

## Clearing all Technical Names

You may wish to disable any coupling between Business and Technical Names and maintain both manually.&nbsp; You may also decide that you want to empty all Technical Name properties.&nbsp; You may do so by setting coupling to No.&nbsp; When you get the following dialog:

![Image](<lib/Naming%20Conventions%20-%20apply%20changes%20with%20clear.png>)

you may choose to check the box "Clear all Technical Names".&nbsp; Be careful of course.&nbsp; You may want to save a version of your model prior to applying this clearing, and test that the behavior matches your expectations.

&nbsp;

## Advanced considerations

### Conversion file

Entries in the conversion file can be in any order, and are case insensitive.&nbsp; You may declare individual words as well as expressions where words in an expression may have a different abbreviation than their individual abbreviation, or than in another expression.&nbsp; Example:

| **Business Name** | **Technical Name** |
| --- | --- |
| Customer | cust |
| Account | accnt |
| Customer Account | cstacc |
| Customer Account Center | cac |


&nbsp;

### Conversion rules hierarchy

There's a hierarchy in our transformations:

\- conversion file

\- invalid characters

\- case conversion

&nbsp;

Plus we natively use 2 word separators when parsing the input line: blank (' ') and underscore ('\_')

&nbsp;

How you set the Invalid Characters behavior is important, as it affects the case conversion behavior.&nbsp; Say, for example that you have camelCase conversion with this Invalid Characters setting:

![Image](<lib/Naming%20Conv%20-%20invalid%20char%20-%20remove.png>)

where a blank (" ") appears in the list of invalid characters (hardly visible, but present in front of the exclamation mark.)&nbsp;

&nbsp;

Going through "Customer Account", first we convert the word with the conversion file to "cust acct", then with the Invalid characters config, we remove the blank and get "custacct", but we've lost the word separator, therefore camelCase does not see the "acct" as a separate mode.  The end result is: "custacct".

&nbsp;

If however, you do a replace blank by underscore:

![Image](<lib/Naming%20Conv%20-%20invalid%20char%20-%20replace.png>)

the sequence becomes "cust acct" then "cust\_acct", then "custAcct" which is the expected behavior.

&nbsp;

However, it may sometimes be preferable to take the blank (" ") out of the list of invalid characters, and let it be handled by the case conversion.

&nbsp;

&nbsp;

### Choices when applying configuration changes&nbsp;

To better understand the impacts of choices in this dialog:

&nbsp;

![Image](<lib/Naming%20Conventions%20-%20apply%20changes%20with%20clear.png>)

Let's look at the user cases.&nbsp; It is possible that, during the course of maintaining a model:

* either the model was started with no coupling, then coupling was enabled selectively for some objects;
* or that a model was started with coupling, then coupling was selectively disabled for some objects.

As a result, less than 100% of the objects may have coupling enabled.  And it may be on purpose, we have no way to tell.

&nbsp;

In such cases, when the choice is being presented as you modify the Naming Conventions parameters, it is important that we apply parameters to objects according to the wish of the user:

* either strictly to the objects for which coupling was previously enabled,
* or give the opportunity to the user to correct an inconsistency, and enable the entire model with the Naming Conventions parameters

&nbsp;

You may also perform this operation, without changing the parameters, by clicking the button at the bottom of the Naming Conventions parameters. 

&nbsp;

Finally, you may also use this button to turn OFF coupling and clear all technical names.

&nbsp;

