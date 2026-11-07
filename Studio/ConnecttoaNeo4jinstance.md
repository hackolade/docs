---
description: Connect Hackolade Studio to Neo4j through the Bolt driver, with authentication and client-side SSL certificates, for reverse-engineering.
seoTitle: Connect to a Neo4j instance
image: lib/Neo4j connection settings.png
---
# Connect to a Neo4j instance

To perform the reverse-engineering function, Hackolade connects to the Neo4j instance via the Bolt driver for JavaScript, with some additional improvements for client-side SSL certificates.

The Connection Settings dialog lets define the parameters in different tabs, as needed:\
![Neo4j connection settings](<lib/Neo4j connection settings.png>)

As an illustration, taking the Neo4j sandbox for movie recommendations:\
![Neo4j Recommendations Sandbox](<lib/Neo4j Recommendations Sandbox.png>)\
copy the IP Address, Bolt Port and paste in the Connection tab\
![Neo4j - Connection settings Recommendation ex](<lib/Neo4j - Connection settings Recommendation ex.png>)

and copy the Username and Password to the Authentication tab:\
![Neo4j - Connections setting authentication](<lib/Neo4j - Connections setting authentication.png>)
