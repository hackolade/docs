# Generate Schema Error during Couchbase reverse-engineering

If you get this message:

![Couchbase reverse-engineering error](<lib/Couchbase RE error.png>)

and the log file HackoladeRE.log in C:\\Users%userprofile%\\AppData\\Roaming\\HackoladeLogs shows the error "message": "An unknown N1QL error occurred. This is usually related to an out-of-memory condition."

There's a workaround for this Couchbase issue.  In Hackolade go to Tools \> Options \> Reverse-Engineering and enable Query Pagination.

![Couchbase reverse-engineering pagination parameters](<lib/Couchbase RE pagination parameters.png>)

The pagination parameter is a fine balance... If too high, and you get that same error.  If too low, and the reverse-engineering process will be slower.
