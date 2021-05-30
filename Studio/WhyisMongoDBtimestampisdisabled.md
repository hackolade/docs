# Why is MongoDB timestamp is disabled?

That's because you really don't want to use timestamp which is a MongoDB-internal data type: [https://docs.mongodb.com/manual/reference/bson-types/#timestamps](<https://docs.mongodb.com/manual/reference/bson-types/#timestamps> "target=\"\_blank\"")

&nbsp;

You want to use date which is really an ISODate data type [https://docs.mongodb.com/manual/reference/method/Date/](<https://docs.mongodb.com/manual/reference/method/Date/> "target=\"\_blank\"") or alternatively use string with a format date-time, ideally formatted according to [ISO 8601](<https://en.wikipedia.org/wiki/ISO\_8601> "target=\"\_blank\"").

&nbsp;

We do display the timestamp data type for backward compatibility purposes, but disabled it so users would not be tempted to use it.
