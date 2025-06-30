# Local instance

In addition to the Azure Cosmos DB web service, Microsoft provides a downloadable version of Cosmos DB that can be run locally.&nbsp; This edition of Cosmos DB lets you write applications without accessing the actual Azure Cosmos DB web service.&nbsp; Instead, the database is self-contained on your computer.

&nbsp;

This local version of Cosmos DB can help you save on provisional throughput, data storage, and data transfer fees.&nbsp; In addition, you do not need to have an Internet connection while your are developing your application. &nbsp;

&nbsp;

Assuming that have downloaded from [https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator](<https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator> "target=\"\_blank\""),&nbsp; to perform the reverse-engineering of the local Cosmos DB instance, you need to create a connection setting, filling the fields in this dialog:

&nbsp;

&nbsp;

![Cosmos DB local mongo connection](<lib/Cosmos DB local mongo connection.png>)

&nbsp;

![Cosmos DB local Mongo auth](<lib/Cosmos DB local Mongo auth.png>)

&nbsp;

with these parameters:

**Name:** local

**Address:** localhost

**Port:** 10255

**Password:** C2y6yDjf5/R+ob0N8A7Cgv30VRDJIWEHLM+4QDU5DE2nQ9nDuVTqobD4b8mGGyPMbIZnqyMsEcaGQy67XIw/Jw==

