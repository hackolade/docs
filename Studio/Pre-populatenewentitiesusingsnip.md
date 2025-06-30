# Pre-populate new entities using snippets

To avoid the repetitive task of adding the same set of attributes to new entities as you create a model, you may leverage [reusable definitions](<Addreusabledefinitions.md>).&nbsp; But there's another option to pre-populate new entities with the same structure, through JSON configuration, using the concept of snippets.

&nbsp;

You may also view this [short video](<https://youtu.be/YHTWOlOl2eE> "target=\"\_blank\"") on YouTube.

&nbsp;

A good example use case would be if your governance standards require to separate metadata header information about a document/record, from data intended for consumption by external processes.&nbsp; Metadata header information may include: schema version, provenance, transformation rules, etc.

![Image](<lib/Snippet metadata.png>)

&nbsp;

Another example could be the creation of a section for canonical data, separate from the idiomatic data coming from the source.&nbsp; Say that you have multiple systems feeding a collection, using different labels for the same type of information: zip, zipcode, postcode, postal code.&nbsp; You wish to keep the source of data as-is, yet be able to query or index the data despite the different labels across documents.&nbsp; You could store the canonical data in a separate section such as:

![Snippet canonical](<lib/Snippet canonical.png>)

&nbsp;

The configuration is done for each target in the folder:

* **Windows:** C:\\Users\\%username%\\.hackolade\\options\\\<target\>\\customProperties
* **Mac/Linux:** ~/.hackolade/options/\<target\>/customProperties

&nbsp;

This folder can be access via Help \> Plugin Manager \> Installed and clicking on the ling "Show plugin customization directory" or via the operating system explorer/finder.

&nbsp;

&nbsp;

## Create snippets

You may create many snippets, but only one can be active, per target, at any time.&nbsp; If you don't have one already, you should create a snippets folder below&nbsp; \\customProperties\\

&nbsp;

![Snippets folder structure](<lib/Snippets folder structure.png>)

&nbsp;

&nbsp;

&nbsp;

A snippet is a simple JSON file with a .json extension. You may [download this example](<https://hackolade.com/schemas/custProps/snippets/metadata.json> "target=\"\_blank\"") and use it as a basis for adjustments to your specific needs.

&nbsp;

![Snippet metadata JSON](<lib/Snippet metadata JSON.png>)

&nbsp;

&nbsp;

Or you may [download this example](<https://hackolade.com/schemas/custProps/snippets/canonical.json> "target=\"\_blank\"") as well.

&nbsp;

![Snippet canonical JSON](<lib/Snippet canonical JSON.png>)

&nbsp;

## Activate a snippet

For your snippet to be used when you create a new entity in your model, you must first activate it.&nbsp; Only a single snippet, if any, can be active at a given time.

&nbsp;

The activation is done in a file that should already exist in your \\customProperties\\properties\_pane folder: defaultData.json

&nbsp;

Simply replace the empty object {} by an object such as this one:

&nbsp;

![Snippets activation](<lib/Snippets activation.png>)

&nbsp;

You may [download an example](<https://hackolade.com/schemas/custProps/properties\_pane/defaultData.json> "target=\"\_blank\"") for this file.

&nbsp;

If you wish to use a different snippet, just change the value in defaultData.json.&nbsp; If you wish to cancel the use of snippets, you should comment the lines.

&nbsp;

![Snippets deactivation](<lib/Snippets deactivation.png>)

&nbsp;

