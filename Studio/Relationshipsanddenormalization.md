# Relationships and denormalization

Even non-relational databases have relationships\!

&nbsp;

With traditional relational databases, a modeler tries to minimize data redundancy through normalization.&nbsp; Data redundancy is considered a bad practice.&nbsp; Given the need to often work with data from multiple tables, they share a common value, known as foreign key, so joins can be performed.&nbsp; Some integrity of the data is enforced by the database and its structure, but the execution of joins when reading data can adversely affect performance.

&nbsp;

Document databases provide scalability and flexibility, but the responsibility to avoid data anomalies resides in the application code.&nbsp; Some of the performance is achieved by avoiding costly joins, in a process known as denormalization.&nbsp; The goal is to keep data that is frequently used together in one document.&nbsp; This allows the document database to minimize the number of times it must read from disk.

&nbsp;

So why is Hackolade providing support for foreign key relationships?&nbsp; With complex systems using document databases, a lot of data may be duplicated in different places.&nbsp; Even if referential integrity is not enforced by the database itself, but by the application code, there is a need to keep track of all the places where a common piece of data is stored.&nbsp; In effect, there are logical relationships in the data, even if the database does not enforce them.

&nbsp;

In addition to implicit relationships due to embedding, Hackolade documents and helps visualize 2 types of relationships: foreign key and foreign master.&nbsp; The foreign key relationship is the unique identifier of the data.&nbsp; The foreign master relationship identifies the master for the duplicated field of the denormalized data.&nbsp; &nbsp;

&nbsp;

Let's take a simplified example... Say we have a master collection of customers, each identified by a unique id.&nbsp; When creating a document for each sales order, the customer name and address are repeated so as to avoid having to perform joins each time an order is accessed. &nbsp;

&nbsp;

![Image](<lib/Relationships%20and%20denormalization.png>)

Three relationships can be documented in the model:

* a foreign key relationship for the customerID in the customers collection
* a foreign master relationship for the customerName
* a foreign master relationship for the customer address

The interest of documenting these relationships is that a routine could be implemented such that, if the address of a customer changes, all pending sales orders for that customer should be updated.&nbsp; The update process would then look for the customerID in the salesOrders collection and update the customerAddress field, in this case only if the order has not shipped yet.

&nbsp;

With v4.2.13, the option was introduced to attempt foreign key relationship inference during reverse-engineering.&nbsp; This features is only available for the MongoDB target, and is for documentation purposes only, as Foreign Key relationships are not enforced by the database.&nbsp; For each field in a collection with the data type ObjectID, the application finds if the sampled value can be linked to a document in the same collection (for a recursive FK) or another collection in the database.&nbsp; The cardinality is set by default to "0...n" on the child side, but can be adjusted manually by the user.

&nbsp;

Hackolade loosely adopts some ER concepts to a NoSQL document environment to help keep complex schemas under control.

&nbsp;

Originally, MongoDB did not support server-side foreign key relationships.&nbsp; With v3.2, MongoDB introduced a $lookup function in the aggregation pipeline to perform a left-outer join with another collection.

&nbsp;

![Image](<lib/MongoDB%20left-outer%20join.png>)

(source: [http://www.mongodb.com/blog/post/joins-and-other-aggregation-enhancements-coming-in-mongodb-3-2-part-1-of-3-introduction](<http://www.mongodb.com/blog/post/joins-and-other-aggregation-enhancements-coming-in-mongodb-3-2-part-1-of-3-introduction> "target=\"\_blank\""))

&nbsp;

&nbsp;

With the following syntax to perform the join:

\- *leftCollection* is the collection that the aggregation is being performed on and is the *left* collection in the join

\- *from* identifies the collection that it will be joined with – the *right* collection (*rightCollection* in this case)

\- *localField* specifies the key from the original/left collection – *leftVal*

\- *foreignField* specifies the key from the right collection – *rightVal*

\- *as* indicates that the data from the right collection should be embedded within the resulting documents as an array called embeddedData

&nbsp;

With the support of RDBMS databases, Hackolade also allows the creation of composite foreign keys, i.e. foreign keys consisting of two or more attributes that reference a set of two or more attributes representing an occurrence in a parent table.&nbsp; A compound key is a composite key for which each attribute that makes up the key is a simple (foreign) key in its own right.


***
_Created with the Personal Edition of HelpNDoc: [Free EPub producer](<https://www.helpndoc.com/create-epub-ebooks>)_
