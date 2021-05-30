# Firestore

The Google Cloud Firestore is a flexible, scalable database for mobile, web, and server development from Firebase and Google Cloud Platform.&nbsp; Like Firebase, it keeps data in sync across client apps through relatime listeners, and offers offline support for mobile and web, so developers can build responsive apps that work regardless of network latency or Internet connectivity.

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; .

Google offers two cloud-based, client-accessible database solutions that support real time data syncing:

* Realtime database: is Firebase's original database
* Cloud Firestore: an improved solution with a more intuitive data model.&nbsp; It features richer, faster queries and scales better than the Realtime Firesbase database.

&nbsp;

Given the [differences](<https://firebase.google.com/docs/database/rtdb-vs-firestore> "target=\"\_blank\"") between the 2 approaches, data modeling for the RealTime Firebase requires a [separate plugin](<Firebase.md>).

&nbsp;

To perform data modeling for Firestore with Hackolade, you must first download the Firestore [plugin](<DownloadadditionalDBtargetplugin.md>).&nbsp; **Note:** the reverse-engineering of documents is not currently available.&nbsp; It is being developed and will be released at a later time.

&nbsp;

Hackolade was specially adapted to support the data modeling of data stored in collections, nested objects, and subcollections.

![Image](<lib/Firestore%20workspace.png>)

## Databases

&nbsp;

## Collections

&nbsp;

In Firestore, data is stored in *documents*, which are organized into *collections*.&nbsp; Each *document* contains a set of key-value pairs. Cloud Firestore is optimized for storing large collections of small documents.&nbsp; All documents must be stored in collections. Documents can contain *subcollections* and nested objects, both of which can include primitive fields like strings or complex objects like lists.&nbsp; Collections and documents are created implicitly in Cloud Firestore. Simply assign data to a document within a collection. If either the collection or document does not exist, Cloud Firestore creates it.

&nbsp;

Subcollections are an implementation of [multi-table inheritance](<https://danchak99.wordpress.com/enterprise-rails/chapter-10-multiple-table-inheritance/> "target=\"\_blank\"")

&nbsp;

## IDs

&nbsp;

The unique key is based on a timestamp, so list items will automatically be ordered chornologically.&nbsp; The Firebase JavaScript clients provide a push() function that generates a unique ID, or key, for each new child.

&nbsp;

&nbsp;

## Attributes data types

&nbsp;

## Indexes

## &nbsp;

## Forward-Engineering

Not applicable, as Firestore does not provide any way to enforce any kind of schema.

&nbsp;

## Reverse-Engineering

**Note:** the reverse-engineering of documents is not currently available.&nbsp; It is being developed and will be released at a later time.

&nbsp;

For more information on Google cloud Firestore in general, please consult the [website](<https://firebase.google.com/docs/firestore> "target=\"\_blank\"").

