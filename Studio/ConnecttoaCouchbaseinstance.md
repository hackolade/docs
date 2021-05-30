# Connect to a Couchbase instance

**Important note:** Schema service is a feature available only in the Couchbase Enterprise Edition.&nbsp; Unless N1QL is disabled plus REST API is enabled, Hackolade Reverse-Engineering will not function properly.

&nbsp;

Authentication is the process of verifying the identity of a client. When access control, i.e. authorization, is enabled, Couchbase requires clients to authenticate themselves in order to allow access.

&nbsp;

With Couchbase 3.x and 4.x fairly basic security, the Administrator can set a password at the bucket level, but anyone with that password gets full rights on the bucket.  With Couchbase 5.x a new role-based access control is introduced.&nbsp; Hackolade supports security of all these versions, but special attention is required for proper configuration:

* if N1QL service is running, we use Couchbase nodejs SDK and a combination of INFER when available (Enterprise 4.5 and above) and N1QL queries, plus:
  * v5.x and above: we use role-based access control 
  * v4.x: we use read-only credentials combined with bucket name/password if any 
  * v3.x: not possible as N1QL did not exist
* if N1QL is not running, we fall back to the REST API, plus:
  * v5.x and above: we use RBAC credentials (specified in the Authentication tab)
  * v4.x: we use read-only credentials combined with bucket name/password if any: the bucket name/password needs to be filled in Connection tab, while the Read-Only username/password is entered in the Authentication tab.  This is required, as per:&nbsp; "Couchbase requires Cluster level authentication for certain REST commands and Bucket level for others"
  * v3.x: we need the console admin name/password (specified in the Authentication tab)

&nbsp;

**Important note:** for the Hackolade reverse-engineering process to effectively use the N1QL service, it is critical that the bucket has a PRIMARY INDEX.&nbsp; Also, for the proper discovery of the different document kinds within a bucket, it is critical that the field used to segregate document kinds be indexed (a secondary index is sufficient.)

As per [https://forums.couchbase.com/t/creating-secondary-index/12783/3](<https://forums.couchbase.com/t/creating-secondary-index/12783/3> "target=\"\_blank\"") : "A primary index of N1QL will allow you to query any field of your JSON. As such, it takes up more space and is less efficient (but much more flexible). It is the basic requirement to be able to use the query language on your data.&nbsp; A secondary index of N1QL is targeted at specific field(s) and will be more performant for queries involving these fields (because the index to scan will be shorter and more to the point)."

&nbsp;

For access to a Couchbase instance in the Cloud, you may need [SSH tunneling](<SSH.md>).

&nbsp;

The Connection Settings dialog lets define the parameters in different tabs, as needed: &nbsp;

&nbsp;

![Image](<lib/Couchbase%20connection%20settings.png>)

For buckets on Couchbase versions 3.0 through 4.6, if the a password has been set at the bucket level, it is necessary to create one connection setting per bucket, and provide the bucket name and password. &nbsp;

&nbsp;

**Important note:** If the N1QL service is not running, it is required to provide BOTH the bucket name/password AND the read-only username/password.

&nbsp;

For read-only users in versions 3.x through 4.6, or for all users starting with version 5.0, it is necessary to enter the username and password in the Authentication tab:

![Image](<lib/Couchbase%20connection%20settings%20Auth%20tab.png>)

&nbsp;

These parameters are assembled by Hackolade to create the full connection string when establishing the connection during the Reverse-Engineering process.

&nbsp;

&nbsp;

## Reverse-Engineering index information from .n1ql file

Couchbase documentation has no unified standard of how to export indexes from couchbase instance to n1ql.&nbsp; You may extract the information following instruction sin this [Couchbase forum exchange](<https://forums.couchbase.com/t/exporting-gsi-indexes/5854/12> "target=\"\_blank\"").

&nbsp;

&nbsp;

SELECT CURL("http://Administrator:passXXX@127.0.0.1:8091//indexStatus").indexes\[\*\].definition As indexes;&nbsp;

"results": \[&nbsp;

{&nbsp;

"indexes": \[&nbsp;

"CREATE PRIMARY INDEX \`#primary\` ON \`default\`",&nbsp;

"CREATE INDEX \`ix100\` ON \`default\`(\`c0\`,\`c1\`,\`c2\`,\`c3\`,\`c4\`)"&nbsp;

\] } \]

&nbsp;

&nbsp;

The highlighted information is to be saved in a text file with extension .n1ql before it can be imported into Hackolade.

&nbsp;

