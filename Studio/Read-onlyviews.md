# Read-only views

Hackolade Studio support the creation, documentation, and maintenance of views for a variety of targets that support the concept: MongoDB, Cassandra, Hive, Snowflake, RDBMS, etc.. The support of views varies of course depending on target's capabilities. Some support materialized views, others not. Some support joins across multiple entities, which others limit views to a single one. You should refer to the respective documentation of the target technology concerned, for the specific implementation details. While the rest of this page uses MongoDB as an example, you can transpose most of the concept to other targets.

&nbsp;

Starting with version 3.4, MongoDB added support for the creation of read-only views from existing collections or other views. Views use indexes of the underlying collection. Views are computed on demand during read operations, and MongoDB executes read operations on views as part of the underlying aggregation pipeline. Views are considered sharded if their underlying collection is sharded. More info can be found [here](<https://docs.mongodb.com/manual/reference/method/db.createView/#db.createView> "target=\"_blank\"").

&nbsp;

In Hackolade, views constitute another type of object in the Entity Relationship Diagram, alongside collections.

&nbsp;

![Views - ERD](<lib/Views - ERD.png>)

&nbsp;

They are visually distinguished by the dotted-line box plus the icon in the top left corner. As per MongoDB's capabilities, a view is based on a particular collection, with the ability to create joins to other collections via the $lookup function. The capability to build views on top of other views is not currently supported.

&nbsp;

## Define a simple view

To build your new view, you add fields by picking existing ones from the collection. Right click on the the root box in the hierarchical schema view to get the contextual menu, then select 'Pick from field list':\
![Views - contextual menu](<lib/Views - contextual menu.png>)\
A dialog containing all the fields of the underlying collection lets you pick the field you want to include (multiple selections will be added at a later time.)

&nbsp;

A corresponding box is added to the hierarchical schema:\
![Views - schema tree view](<lib/Views - DTD.png>)

&nbsp;

At the same time, a pipeline expression is dynamically generated to represent the fields in the view:

&nbsp;

```json
[
    {
        "$project": {
            "_id": 1,
            "business_id": 1,
            "name": 1,
            "full_address": 1,
            "type": 1
        }
    }
]
```

&nbsp;

Similarly, the corresponding Create View script is dynamically generated and can be pasted in code or in the MongoDB console:

&nbsp;

```javascript
db.createView( "rov_business",
"businesses",
[
    {
        "$project": {
            "_id": 1,
            "business_id": 1,
            "name": 1,
            "full_address": 1,
            "type": 1
        }
    }
]
);
```

&nbsp;

## Create joins across multiple collections

In MongoDB, it is possible to link related data from multiple collections into one single view, by using the pipeline aggregation $lookup function. You can find more information [here](<https://docs.mongodb.com/manual/reference/operator/aggregation/lookup/#pipe._S_lookup> "target=\"_blank\""). This is possible therefore in Hackolade as well. To do so, the contextual menu let's you add an attribute to the root via right-click:

&nbsp;

![Views - lookup contextual menu](<lib/Views - lookup contextual menu.png>)

&nbsp;

You then get prompted to fill the lookup fields:\
![Views - add lookup](<lib/Views - add lookup.png>)

&nbsp;

The localField represents the foreign key upon which the $lookup will perform the matching with the foreignField in the foreign collection. If your model already contains relationships, the from and foreignField entries will get automatically field in. You still need to define the name you wish in the 'as' parameter.

&nbsp;

When you click 'Apply', the application will fetch all the fields of the foreign collection, add them to the hierarchical schema view and update the pipeline expression. You may now suppress and/or reorder foreign fields in the view.

&nbsp;

```json
[
    {
        "$project": {
            "_id": 1,
            "review_id": 1,
            "date": 1,
            "stars": 1,
            "type": 1,
            "business": {
                "business_id": "$business_id",
                "name": "$name",
                "type": "$type",
                "stars": "$stars",
                "review_count": "$review_count",
                "full_address": "$full_address",
                "city": "$city",
                "state": "$state",
                "latitude": "$latitude",
                "longitude": "$longitude"
            },
            "user": {
                "user_id": "$user_id",
                "name": "$name",
                "type": "$type",
                "votes": "$votes",
                "yelping_since": "$yelping_since"
            }
        }
    },
    {
        "$lookup": {
            "from": "businesses",
            "as": "business",
            "localField": "business_id",
            "foreignField": "_id"
        }
    },
    {
        "$lookup": {
            "from": "users",
            "as": "user",
            "localField": "user_id",
            "foreignField": "name"
        }
    }
]
```
