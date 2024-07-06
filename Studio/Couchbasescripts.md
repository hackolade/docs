# Couchbase scripts

For those in a technology stack using JavaScript, and are using the [Ottoman ODM](<http://ottomanjs.com/> "target=\"\_blank\""), Hackolade also provides the option to export a JavaScript Ottoman schema file for the collection definition via the menu option Tools \> Forward-Engineering \> Ottoman Schema or Couchbase script

&nbsp;

![Forward-Engineering - Ottoman Schema file](<lib/Forward-Engineering%20-%20Ottoman%20Schema%20file.png>)

&nbsp;

The same information can also be viewed in the Ottoman Schema tab:

![Forward-Engineering - Couchbase Ottoman Schem](<lib/Forward-Engineering%20-%20Couchbase%20Ottoman%20Schem.png>)

&nbsp;

We provide a sort of "forward-engineering by example", with an automatic JSON data sample generation.&nbsp; The script also includes the creation of indexes, and it can be applied to the database instance, provided that appropriate credentials are granted to the user.&nbsp; If the specified bucket does not exist, we attempt to create it.

&nbsp;

![Couchbase forward-engineering script](<lib/Couchbase%20forward-engineering%20script.png>)

&nbsp;

The following credentials are required:

\- if the bucket exists, the user should have at least:

* [Query Manage Index](<https://docs.couchbase.com/server/6.0/learn/security/roles.html#query-manage-index> "target=\"\_blank\"") - to insert indexes.
* [Query Insert](<https://docs.couchbase.com/server/6.0/learn/security/roles.html#query-insert> "target=\"\_blank\"") - to Insert documents.

If a bucket doesn't exist, the user needs either [Full Admin](<https://docs.couchbase.com/server/6.0/learn/security/roles.html#full-admin> "target=\"\_blank\"") or [Cluster Admin](<https://docs.couchbase.com/server/6.0/learn/security/roles.html#cluster-admin> "target=\"\_blank\"")  to be able to create the bucket.

&nbsp;

