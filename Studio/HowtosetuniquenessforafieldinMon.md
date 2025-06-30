# How to set uniqueness for a field in MongoDB

MongoDB is a schemaless database.  As such, the possibilities for constraints are less than with a relational database.  Nevertheless, with the [MongoDB validator](<https://www.mongodb.com/docs/manual/core/schema-validation/> "target=\"\_blank\"") it is possible to do validations.  They are based on the [$jsonschema operator](<https://www.mongodb.com/docs/manual/core/schema-validation/specify-json-schema/> "target=\"\_blank\"") which itself is based on (actually is a subset/superset of) the JSON Schema draft-à4 specification.  

The JSON Schema specification allows to set [uniqueness in arrays](<https://json-schema.org/understanding-json-schema/reference/array#uniqueItems> "target=\"\_blank\"") only, and in Hackolade, we support this via the corresponding property:

 ![Image](<lib/MongoDB uniqueItems in arrays.png>)

&nbsp;

But this uniqueness feature is not available for scalar fields in a document.

However, you can set in MongoDB a [unique index](<https://www.mongodb.com/docs/v3.0/core/index-unique/#index-type-unique> "target=\"\_blank\"")  on a field or a set of fields.  This is done in Hackolade, at the collection level, in the Indexes tab whe you can create your index, which will generate the corresponding script in forward-engineering.

![Image](<lib/MongoDB unique index.png>)

