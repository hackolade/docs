# Suggest denormalization of a SQL schema

You should save the resulting model as a base, for example v0.&nbsp; Then it is suggested you save it again as v1 and work with the denormalization function to make v1 evolve towards a denormalized model.

&nbsp;

The user needs to have a fairly good idea of where he wants to go with the schema design, and use Hackolade to facilitate the work.&nbsp; For example, with the Northwind database shown above, in a NoSQL model, one would want to merge the tables 'orders' and 'order details' while embedding some data from the master tables around.

&nbsp;

![Image](<lib/Denormalization%20dialog.png>)

&nbsp;

Select at least 2 tables to which denormalization should be applied.&nbsp; Then select the type of embedding (sub-document in child, array in parent, or both) and the number of cascading levels that should be applied.&nbsp; If a table has a parent, and the parent has a grand-parent, we talk about cascading relationships.&nbsp; This can go on and on.&nbsp; To avoid circular references and other incoherent result, the user can limit the number of cascading levels.

&nbsp;

Example of embedding of sub-documents in child.

Collection 'products' contains a foreign key to 'categories':

![Image](<lib/Denormalization%20--%20sub-document%20in%20child%20-%201.png>)

&nbsp;

the resulting denormalization would be:

![Image](<lib/Denormalization%20--%20sub-document%20in%20child%20-%202.png>)

with the field category\_id in 'products' being replaced by a sub-document with all the fields of the 'categories' collection, including one foreign key and several foreign master relationships.&nbsp; Depending on your needs, you may want to keep the 'categories' collection, or delete it.

&nbsp;

Example of embedding an array in parent.

Collection 'order details' contains a foreign key to 'orders':

![Image](<lib/Denormalisation%20-%20Array%20in%20parent%20-%201.png>)

&nbsp;

the resulting denormalization would be:

![Image](<lib/Denormalization%20-%20Array%20in%20child%20-%202.png>)

where you notice that all fields of 'order details' have been added in an array of sub-documents in 'orders'.&nbsp; And it makes sense to delete the collection 'order details'.


***
_Created with the Personal Edition of HelpNDoc: [Free PDF documentation generator](<https://www.helpndoc.com>)_
