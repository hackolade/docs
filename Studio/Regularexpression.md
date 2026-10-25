# Regular expression

Regex is used in different places:

- for the pattern validation of strings
- for the definition of pattern fields

&nbsp;

These regular expressions should be valid according to the ECMA 262 regular expression dialect. Regex value should start with the “^” and end with the “$” anchors to satisfy the internal Hackolade validation.

&nbsp;

The following regular expression tokens are supported:

- simple character classes (\[abc\]), range character classes (\[a-z\]);
- complemented character classes (\[^abc\], \[^a-z\]);
- simple quantifiers: "+" (one or more), "\*" (zero or more), "?" (zero or one), and their lazy versions ("+?", "\*?", "??");
- range quantifiers: "{x}" (exactly x occurrences), "{x,y}" (at least x, at most y, occurrences), {x,} (x occurrences or more), and their lazy versions;
- simple grouping ("(...)") and alternation ("|").

&nbsp;

Ref: [https://json-schema.org/draft/2020-12/json-schema-validation#name-regex](<https://json-schema.org/draft/2020-12/json-schema-validation#name-regex> "target=\"_blank\"") and [https://regex101.com/#javascript](<https://regex101.com/#javascript> "target=\"_blank\"")

&nbsp;

## Custom property validation

It is possible to customize the validation of out-of-the-box properties.

&nbsp;

It requires editing, fir each target that requires it, the file "C:\\Users\\%username%\\.hackolade\\options\\\<target>\\customProperties\\validation\\validationRegularExpressions.json" for the appropriate \<target>

&nbsp;

Here is an example of entries that you could add to the file, in curly brackets:

&nbsp;

```json
{
    "description": "^[^|]+$", //description-SQL COMMENT for all levels
    "comments": "^[^|]+$", //remarks for all levels
    "modelName": "^[A-Z_ ]+$", // business names for models
    "containerName": "^[A-Z_ ]+$", // business names for containers/schemas/databases/namespaces/keyspaces/...
    "collectionName": "^[A-Z_ ]+$", // business names for entities/tabels/records/nodes
    "name": "^[A-Z_ ]+$", // business names for attributes/columns/fields
    "code": "^[a-z0-9_]+$", // technical names for all objects at all level
    "relationshipName": "^[A-Z_ ]+$" //relationship names
}
```

&nbsp;

You should eliminate the lines that don’t apply, and adjust the regex to your needs, for example:

- only lowercase letters, digits, and dashes: “^\[a-z0-9-\]+$”
- only uppercase letters and dashes: “^\[A-Z-\]+$”

&nbsp;

GenAI is particularly useful to compose the proper Regex.
