---
description: Connect Hackolade Studio to a YugabyteDB instance, and the privileges a user needs to reverse-engineer objects owned by others.
seoTitle: Connect to YugabyteDB for reverse-engineering
image: lib/YugabyteDB connection settings.png
---
# Connect to YugabyteDB

> [!IMPORTANT]
> When reverse-engineering a YugabyteDB instance, non-privileged users can see the metadata of only their own objects, so to access others you need to be be granted the role `USAGE`. It more granularity is necessary, here are the full details:

1\) SELECT privileges on all tables in \`pg_catalog\` schema (is default and included in PUBLIC role).\
2\) Schemas: CREATE or USAGE privilege.\
3\) Tables: SELECT or REFERENCES or TRIGGER privilege.\
4\) Columns: SELECT or REFERENCES privilege.\
5\) Views: SELECT or REFERENCES or TRIGGER privilege.\
6\) Function: EXECUTE privilege.\
7\) Domains: USAGE privilege.

More information is available [here](<https://www.postgresql.org/docs/current/ddl-priv.html> "target=\"_blank\"").\
The YugabyteDB instance can be hosted on-premises, or on virtualized machines in a private or public cloud.

In the Hackolade connection settings dialog, give a meaningful name to the connection, then set the the host and port, and an optional database name if you wish to limit the scope of the discovery.

![YugabyteDB connection settings](<lib/YugabyteDB connection settings.png>)

If required, you may enter your username and password

![MariaDB connection settings auth](<lib/MariaDB connection settings auth.png>)
