# Regular expression

Regex is used in 2 places:

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

