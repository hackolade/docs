# Document types for Couchbase are not discovered as expected

If you feel that several document kinds in your bucket are not identified by Hackolade during the reverse-engineering process, be aware that the process requires that the bucket is indexed.  This can be a primary index, but does not have to be.  It can be a secondary index, as long as it on the field that serves to differentiate document types.

An easy way to check is to got to the Couchbase console http://localhost:8091/ui/index.html#/query/workbench and make sure that your bucket does not appear in the 'Non-Indexed Buckets' list. 

Refer to [https://docs.couchbase.com/server/current/n1ql/n1ql-language-reference/createindex.html](<https://docs.couchbase.com/server/current/n1ql/n1ql-language-reference/createindex.html> "target=\"\_blank\"") and [https://docs.couchbase.com/server/current/n1ql/n1ql-language-reference/createprimaryindex.html](<https://docs.couchbase.com/server/current/n1ql/n1ql-language-reference/createprimaryindex.html> "target=\"\_blank\"") for more information.

