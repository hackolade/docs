---
description: Connect Hackolade Studio to HBase with basic or Kerberos authentication, for reverse-engineering of tables and column families.
seoTitle: Connect to an Apache HBase instance
image: lib/HBase connection settings.png
---
# Connect to an HBase instance

HBase can be configured to provide User Authentication, which ensures that only authorized users can communicate with HBase. The authorization system is implemented at the RPC level, and is based on the Simple Authentication and Security Layer (SASL.) Hackolade provides support for basic authentication.

![HBase connection settings](<lib/HBase connection settings.png>)
