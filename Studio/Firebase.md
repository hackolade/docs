# Firebase

The Google Firebase Realtime Database is a cloud-hosted database.&nbsp; Data is stored in JSON and synchronized in real time to every connected mobile or other client.&nbsp; It lets developers build rich collaborative applications, with data also persisted locally, to give users a responsive experience.

&nbsp;

Google offers two cloud-based, client-accessible database solutions that support real time data syncing:

* Realtime database: is Firebase's original database
* Cloud Firestore: an improved solution with a more intuitive data model.&nbsp; It features richer, faster queries and scales better than the Realtime Firesbase database.

&nbsp;

Given the [differences](<https://firebase.google.com/docs/database/rtdb-vs-firestore> "target=\"\_blank\"") between the 2 approaches, data modeling for the Cloud Firestore requires a [separate plugin](<Firestore.md>).

&nbsp;

To perform data modeling for Firebase with Hackolade, you must first download the Firebase [plugin](<DownloadadditionalDBtargetplugin.md>).&nbsp; **Note:** the reverse-engineering of documents is not currently available.&nbsp; It is being developed and will be released at a later time.

&nbsp;

Hackolade was specially adapted to support the data modeling of data stored as a large [JSON tree](<https://firebase.google.com/docs/database/web/structure-data> "target=\"\_blank\""), with data nodes and their associated keys.

![Firebase workspace](<lib/Firebase%20workspace.png>)

## Databases

Each Firebase Realtime database data is stored as JSON objects. &nbsp;

&nbsp;

&nbsp;

## Nodes

&nbsp;

&nbsp;

&nbsp;

## IDs

&nbsp;

&nbsp;

## Attributes data types

&nbsp;

&nbsp;

## Indexes

&nbsp;

## Forward-Engineering

Not applicable, as Firebase does not provide any way to enforce any kind of schema.

## Reverse-Engineering

**Note:** the reverse-engineering of documents is not currently available.&nbsp; It is being developed and will be released at a later time.

&nbsp;

&nbsp;

For more information on Cosmos DB in general, please consult the [website](<https://docs.microsoft.com/en-us/azure/cosmos-db/introduction> "target=\"\_blank\"").

