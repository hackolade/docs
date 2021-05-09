# Read-only views

Hackolade support the creation, documentation, and maintenance of views for a variety of targets that support the concept: MongoDB, Cassandra, Hive, Snowflake, RDBMS, etc.. The support of views varies of course depending on target's capabilities.&nbsp; Some support materialized views, others not.&nbsp; Some support joins across multiple entities, which others limit views to a single one.&nbsp; You should refer to the respective documentation of the target technology concerned, for the specific implementation details.&nbsp; While the rest of this page uses MongoDB as an example, you can transpose most of the concept to other targets.

&nbsp;

Starting with version 3.4, MongoDB added support for the creation of read-only views from existing collections or other views.&nbsp; Views use indexes of the underlying collection.&nbsp; Views are computed on demand during read operations, and MongoDB executes read operations on views as part of the underlying aggregation pipeline.&nbsp; Views are considered sharded if their underlying collection is sharded.&nbsp; More info can be found [here](<https://docs.mongodb.com/manual/reference/method/db.createView/#db.createView> "target=\"\_blank\"").&nbsp;

&nbsp;

In Hackolade, views constitute another type of object in the Entity Relationship Diagram, alongside collections. &nbsp;

&nbsp;

![Image](<lib/Views%20-%20ERD.png>)

&nbsp;

They are visually distinguished by the dotted-line box plus the icon in the top left corner.&nbsp; As per MongoDB's capabilities, a view is based on a particular collection, with the ability to create joins to other collections via the $lookup function.&nbsp; The capability to build views on top of other views is not currently supported.

&nbsp;

## Define a simple view ##

To build your new view, you add fields by picking existing ones from the collection.&nbsp; Right click on the the root box in the hierarchical schema view to get the contextual menu, then select 'Pick from field list':

![Image](<lib/Views%20-%20contextual%20menu.png>)

A dialog containing all the fields of the underlying collection lets you pick the field you want to include (multiple selections will be added at a later time.)

&nbsp;

A corresponding box is added to the hierarchical schema:

![Image](<lib/Views%20-%20DTD.png>)

&nbsp;

At the same time, a pipeline expression is dynamically generated to represent the fields in the view:

&nbsp;

\[

&nbsp; &nbsp; {

&nbsp; &nbsp; &nbsp; &nbsp; "$project": {

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "\_id": 1,

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "business\_id": 1,

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "name": 1,

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "full\_address": 1,

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "type": 1

&nbsp; &nbsp; &nbsp; &nbsp; }

&nbsp; &nbsp; }

\]

&nbsp;

Similarly, the corresponding Create View script is dynamically generated and can be pasted in code or in the MongoDB console:

&nbsp;

db.createView( "rov\_bussiness",

"businesses",

\[

&nbsp; &nbsp; {

&nbsp; &nbsp; &nbsp; &nbsp; "$project": {

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "\_id": 1,

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "business\_id": 1,

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "name": 1,

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "full\_address": 1,

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "type": 1

&nbsp; &nbsp; &nbsp; &nbsp; }

&nbsp; &nbsp; }

\]

);

&nbsp;

## Create joins across multiple collections ##

In MongoDB, it is possible to link related data from multiple collections into one single view, by using the pipeline aggregation $lookup function.&nbsp; You can find more information [here](<https://docs.mongodb.com/manual/reference/operator/aggregation/lookup/#pipe.\_S\_lookup> "target=\"\_blank\"").&nbsp; This is possible therefore in Hackolade as well.&nbsp; To do so, the contextual menu let's you add an attribute to the root via right-click:

&nbsp;

![Image](<lib/Views%20-%20lookup%20contextual%20menu.png>)

&nbsp;

You then get prompted to fill the lookup fields:

![Image](<lib/Views%20-%20add%20lookup.png>)

&nbsp;

The localField represents the foreign key upon which the $lookup will perform the matching with the foreignField in the foreign collection.&nbsp; If your model already contains relationships, the from and foreignField entries will get automatically field in.&nbsp; You still need to define the name you wish in the 'as' parameter.

&nbsp;

When you click 'Apply', the application will fetch all the fields of the foreign collection, add them to the hierarchical schema view and update the pipeline expression.&nbsp; You may now suppress and/or reorder foreign fileds in the view.

&nbsp;

\[

&nbsp; &nbsp; {

&nbsp; &nbsp; &nbsp; &nbsp; "$project": {

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "\_id": 1,

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "review\_id": 1,

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "date": 1,

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "stars": 1,

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "type": 1,

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "business": {

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "business\_id": "$business\_id",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "name": "$name",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "type": "$type",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "stars": "$stars",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "review\_count": "$review\_count",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "full\_address": "$full\_address",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "city": "$city",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "state": "$state",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "latitude": "$latitude",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "longitude": "$longitude"

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "user": {

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "user\_id": "$user\_id",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "name": "$name",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "type": "$type",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "votes": "$votes",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "yelping\_since": "$yelping\_since"

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }

&nbsp; &nbsp; &nbsp; &nbsp; }

&nbsp; &nbsp; },

&nbsp; &nbsp; {

&nbsp; &nbsp; &nbsp; &nbsp; "$lookup": {

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "from": "businesses",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "as": "business",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "localField": "business\_id",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "foreignField": "\_id"

&nbsp; &nbsp; &nbsp; &nbsp; }

&nbsp; &nbsp; },

&nbsp; &nbsp; {

&nbsp; &nbsp; &nbsp; &nbsp; "$lookup": {

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "from": "users",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "as": "user",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "localField": "user\_id",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; "foreignField": "name"

&nbsp; &nbsp; &nbsp; &nbsp; }

&nbsp; &nbsp; }

\]

&nbsp;

&nbsp;

&nbsp;


***
_Created with the Personal Edition of HelpNDoc: [Free EBook and documentation generator](<https://www.helpndoc.com>)_
