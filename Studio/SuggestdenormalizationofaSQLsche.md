# Suggest denormalization of a SQL schema

Ease migration from SQL with denormalization suggestions.&nbsp; Hackolade Studio helps with the migration from SQL. You can now reverse-engineer a Data Definition Language (DDL) file from Oracle into a Hackolade model. Then you can apply denormalization functions for embedding and referencing data, and truly leverage the power and benefits of nested objects in JSON and MongoDB.

&nbsp;

You should save the resulting model as a base, for example v0.&nbsp; Then it is suggested you save it again as v1 and work with the denormalization function to make v1 evolve towards a denormalized model.

&nbsp;

![Image](<lib/Suggest%20denormalization%20-%20Northwind.png>)

&nbsp;

The user needs to have a fairly good idea of where he wants to go with the schema design, and use Hackolade to facilitate the work.&nbsp; For example, with the Northwind database shown above, in a NoSQL model, one would want to merge the tables 'orders' and 'order details' while embedding some data from the master tables around.

&nbsp;

![Denormalization dialog](<lib/Denormalization%20dialog.png>)

&nbsp;

Select 2 tables to which denormalization should be applied.&nbsp; Then select the type of embedding (sub-document in child, array in parent, or both.)

&nbsp;

Example of embedding of sub-documents in child.

Collection 'products' contains a foreign key to 'categories':

![Denormalization -- sub-document in child - 1](<lib/Denormalization%20--%20sub-document%20in%20child%20-%201.png>)

&nbsp;

the resulting denormalization would be:

![Denormalization -- sub-document in child - 2](<lib/Denormalization%20--%20sub-document%20in%20child%20-%202.png>)

with the field category\_id in 'products' being replaced by a sub-document with all the fields of the 'categories' collection, including one foreign key and several foreign master relationships.&nbsp; Depending on your needs, you may want to keep the 'categories' collection, or delete it.

&nbsp;

Example of embedding an array in parent.

Collection 'order details' contains a foreign key to 'orders':

![Denormalisation - Array in parent - 1](<lib/Denormalisation%20-%20Array%20in%20parent%20-%201.png>)

&nbsp;

the resulting denormalization would be:

![Denormalization - Array in child - 2](<lib/Denormalization%20-%20Array%20in%20child%20-%202.png>)

where you notice that all fields of 'order details' have been added in an array of sub-documents in 'orders'.&nbsp; And it makes sense to delete the collection 'order details'.

