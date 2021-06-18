# What's a pattern field?

Hackolade, being built on JSON Schema, leverages this little-known but extremely powerful feature of JSON.

Pattern fields function in exactly the same way as standard fields, with one exception: the name (in the name-value pair) is not a fixed string, but a regex pattern.

For example:

![Image](<lib/Pattern%20property%20example.png>)

This is represented in the Hackolade ERD as:

![Image](<lib/Pattern%20property%20ERD.png>)

The name in the name-value pair is not a fixed word, but a variable.  That's what pattern fields are for.  They are typically controlled by a regular expression, hence the name of pattern field.

You should not look at it as a 'field name', but as a key to a sub-document when embedding.  It lets you easily access the right sub-document inside an array or main document, using dot notation.

In Hackolade, the above example is modeled this way:

![Image](<lib/Pattern%20property%20schema.png>)

To add a pattern field to a document structure, right-click and choose add/insert/append \> Pattern Field then the field data type:

![Image](<lib/Pattern%20property%20contextual%20menu.png>)
