# Kerberos

MongoDB Enterprise provides support for Kerberos authentication of MongoDB clients.&nbsp; Kerberos is an industry standard authentication protocol for large client/server systems. Kerberos allows MongoDB and applications to take advantage of existing authentication infrastructure and processes.

&nbsp;

For more info on how to setup Kerberos in MongoDB, please consult this [link](<http://docs.mongodb.com/manual/core/kerberos> "target=\"\_blank\"").

&nbsp;

The Kerberos parameters are maintained in Hackolade as follows:

&nbsp;

![MongoDB Kerberos connection settings](<lib/Kerberos%20connection%20settings.png>)

&nbsp;

A Kerberos principal is a unique identity to which Kerberos can assign tickets.

&nbsp;

Principals can have an arbitrary number of components. Each component is separated by a component separator, generally /. The last component is the realm, separated from the rest of the principal by the realm separator, generally @.

&nbsp;

An example for a Kerberos Principal is: primary/instance@REALM.

&nbsp;

A Kerberos Service Name is the name by which a client uniquely identifies an instance of a service.

&nbsp;

Typically, the service name for a MongoDB instance is named mongodb. Provide another name here if your MongoDB instance was set up with a different service name.

