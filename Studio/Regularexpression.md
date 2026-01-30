# Regular expression

Regex is used in different places:

\- for the pattern validation of strings

\- for the definition of pattern fields

&nbsp;

These regular expressions should be valid according to the ECMA 262 regular expression dialect.&nbsp; Regex value should start with the “\^” and end with the “$” anchors to satisfy the internal Hackolade validation.

&nbsp;

The following regular expression tokens are supported:

* simple character classes (\[abc\]), range character classes (\[a-z\]);
* complemented character classes (\[\^abc\], \[\^a-z\]);
* simple quantifiers: "+" (one or more), "\*" (zero or more), "?" (zero or one), and their lazy versions ("+?", "\*?", "??");
* range quantifiers: "{x}" (exactly x occurrences), "{x,y}" (at least x, at most y, occurrences), {x,} (x occurrences or more), and their lazy versions;
* simple grouping ("(...)") and alternation ("\|").

&nbsp;

Ref: [https://json-schema.org/draft/2020-12/json-schema-validation#name-regex](<https://json-schema.org/draft/2020-12/json-schema-validation#name-regex> "target=\"\_blank\"") and [https://regex101.com/#javascript](<https://regex101.com/#javascript> "target=\"\_blank\"")

&nbsp;

## Custom property validation

It is possible to customize the validation of out-of-the-box properties.

&nbsp;

It requires editing, fir each target that requires it, the file "C:\\Users\\%username%\\.hackolade\\options\\\<target\>\\customProperties\\validation\\validationRegularExpressions.json"&nbsp; for the appropriate \<target\>

&nbsp;

Here is an example of entries that you could add to the file, in curly brackets:

&nbsp;

> {\
&nbsp; &nbsp; "description": "\^\[\^\|\]+$", //description-SQL COMMENT for all levels\
&nbsp; &nbsp; "comments": "\^\[\^\|\]+$", //remarks for all levels\
&nbsp; &nbsp; "modelName": "\^\[A-Z\_ \]+$", // business names for models\
&nbsp; &nbsp; "containerName": "\^\[A-Z\_ \]+$", // business names for containers/schemas/databases/namespaces/keyspaces/...\
&nbsp; &nbsp; "collectionName": "\^\[A-Z\_ \]+$", // business names for entities/tabels/records/nodes\
&nbsp; &nbsp; "name": "\^\[A-Z\_ \]+$", // business names for attributes/columns/fields\
&nbsp; &nbsp; "code": "\^\[a-z0-9\_\]+$", // technical names for all objects at all level\
&nbsp; &nbsp; "relationshipName": "\^\[A-Z\_ \]+$" //relationship names\
}

&nbsp;

You should eliminate the lines that don’t apply, and adjust the regex to your needs, for example:

* only lowercase letters, digits, and dashes: “\^\[a-z0-9-\]+$”
* only uppercase letters and dashes: “\^\[A-Z-\]+$”

&nbsp;

GenAI is particularly useful to compose the proper Regex. &nbsp;

&nbsp;

