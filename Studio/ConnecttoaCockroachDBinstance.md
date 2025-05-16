# Connect to a CockroachDB instance

**Important:** when reverse-engineering a CockroachDB instance, non-privileged users can see the metadata of only their own objects, so to access others you need to be be granted the role USAGE. &nbsp; It more granularity is necessary, here are the full details:

&#49;) SELECT privileges on all tables in \`pg\_catalog\` schema (is default and included in PUBLIC role).

&#50;) Schemas: CREATE or USAGE privilege.

&#51;) Tables: SELECT or REFERENCES or TRIGGER privilege.

&#52;) Columns: SELECT or REFERENCES privilege.

&#53;) Views: SELECT or REFERENCES or TRIGGER privilege.

&#54;) Function: EXECUTE privilege.

&#55;) Domains: USAGE privilege.

&nbsp;

More information is available [here](<https://www.cockroachlabs.com/docs/stable/security-reference/authorization#privileges> "target=\"\_blank\"").

The CockroachDB instance can be hosted on-premises, or on virtualized machines in a private or public cloud. &nbsp;

&nbsp;

In the Hackolade connection settings dialog, give a meaningful name to the connection, then set the the host and port, and an optional database name if you wish to limit the scope of the discovery.

&nbsp;

![PostgreSQL connection settings](<lib/PostgreSQL connection settings.png>)

&nbsp;

If required, you may enter your username and password

&nbsp;

![Image](<lib/MariaDB connection settings auth.png>)
