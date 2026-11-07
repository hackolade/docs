---
description: The MongoDB timestamp type is for internal use; Hackolade Studio models dates with the date (ISODate) type instead.
seoTitle: Why is the MongoDB timestamp type disabled?
---
# Why is MongoDB timestamp is disabled?

That's because you really don't want to use timestamp which is a MongoDB-internal data type: [https://docs.mongodb.com/manual/reference/bson-types/#timestamps](<https://docs.mongodb.com/manual/reference/bson-types/#timestamps> "target=\"_blank\"")

You want to use date which is really an ISODate data type [https://docs.mongodb.com/manual/reference/method/Date/](<https://docs.mongodb.com/manual/reference/method/Date/> "target=\"_blank\"") or alternatively use string with a format date-time, ideally formatted according to [ISO 8601](<https://en.wikipedia.org/wiki/ISO_8601> "target=\"_blank\"").

Alternatively, you may want to use a String data type with a date-time format.

We do display the timestamp data type for backward compatibility purposes, but disabled it so users would not be tempted to use it.
