# Access issues when doing reverse-engineering of Couchbase

# Access issues when doing reverse-engineering of Couchbase #

With Couchbase 3.x and 4.x fairly basic security, the Administrator can set a password at the bucket level, but anyone with that password gets full rights on the bucket. With Couchbase 5.x a new role-based access control is introduced.  Hackolade supports security of all these versions, but special attention is required for proper configuration:

* if N1QL service is running, we use Couchbase nodejs SDK and a combination of INFER when available (Enterprise 4.5 and above) and N1QL queries, plus:
  * v5.x: we use role-based access control 
  * v4.x: we use read-only credentials combined with bucket name/password if any 
  * v3.x: not possible as N1QL did not exist
* if N1QL is not running, we fall back to the REST API, plus:
  * v5.x: we use RBAC credentials (specified in the Authentication tab)
  * v4.x: we use read-only credentials combined with bucket name/password if any: the bucket name/password needs to be filled in Connection tab, while the Read-Only username/password is entered in the Authentication tab.  This is required, as per:  "Couchbase requires Cluster level authentication for certain REST commands and Bucket level for others"
  * v3.x: we need the console admin name/password (specified in the Authentication tab)

&nbsp;


***
_Created with the Personal Edition of HelpNDoc: [Create help files for the Qt Help Framework](<https://www.helpndoc.com/feature-tour/create-help-files-for-the-qt-help-framework>)_
